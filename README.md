# EC2MonitoringUsingCloudWatch
This guide walks through setting up a CloudWatch dashboard and alarm to monitor an EC2 instance.

---

## ☁️ Step 1: Access the Instance
1. Connect to your EC2 instance via **EC2 Instance Connect** or **SSH**.

2. (Optional) Simulate CPU Load:
```bash
sudo yum install stress -y
stress --cpu 2 --timeout 60
```
---

# 📈 Step 2: Create a CloudWatch Dashboard

This guide walks you through creating an Amazon CloudWatch dashboard for monitoring your EC2 instance.

## 🔧 Instructions

1. **Navigate to CloudWatch Dashboards**  
   Go to **AWS Console** > **CloudWatch** > **Dashboards** > **Create dashboard**

2. **Name Your Dashboard**  

3. **Add Widgets**  
- Click **Add widget**
- Choose **Line**
- For each of the following metrics, create **a separate widget**:

  - ✅ `CPUUtilization`
  - ✅ `NetworkIn`
  - ✅ `NetworkOut`
  - ✅ `DiskReadBytes`
  - ✅ `DiskWriteBytes`

> 💡 *Create each metric as a separate widget for better visibility and monitoring.*

---

# 🚨 Step 3: Set a Basic Alarm

Set up a basic alarm to monitor your EC2 instance's CPU usage and get notified when it exceeds a certain threshold.

## 🔧 Instructions

1. **Navigate to CloudWatch Alarms**  
   Go to **AWS Console** > **CloudWatch** > **Alarms** > **Create alarm**

2. **Select Metric**  
   - Choose **EC2**  
   - Select **CPUUtilization**

3. **Set Threshold**  
   - Example:  
     Trigger if **CPU > 60%** for **2 consecutive periods**

4. **Configure Notification**  
   - Choose to **Send notification to SNS topic** *(you can skip this step for now if not using SNS)*

5. **Name Your Alarm**

---

## 🖼️ Project Screenshots

<!-- Figure 1: EC2 instance creation -->
![Step 3: EC2 Instance Created](ec2-created.png)  
*Figure 1: EC2 instance successfully created and running.*

<!-- Figure 2: CloudWatch Dashboard -->
![CloudWatch Dashboard](cloudwatch-dashboard.png)  
*Figure 2: “EC2-Monitoring-Demo” dashboard showing CPU, Network, and Disk metrics.*

<!-- Figure 3: High CPU Alarm -->
![High CPU Alarm](highcpu-alarm.png)  
*Figure 3: CloudWatch alarm “HighCPUAlarm” configured to trigger when CPU > 60% for 2 periods.*

## 🧠 Skills Demonstrated

- ✅ EC2 provisioning and management
- ✅ CloudWatch dashboard and metric configuration
- ✅ Alarm and threshold-based monitoring
- ✅ Simulating CPU load for testing
- ✅ Infrastructure observability best practices

## 📌 Summary
This project serves as a practical foundation in AWS monitoring and alerting, showcasing the ability to proactively manage and visualize infrastructure health using native AWS services.
