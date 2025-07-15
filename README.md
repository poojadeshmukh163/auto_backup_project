🔄 Automated Backup and Rotation Script with Google Drive Integration
This project automates the process of backing up a directory on a Linux server (e.g., AWS EC2). It zips the target directory, uploads it to Google Drive using rclone, and applies retention rules to manage storage space. Additionally, it supports webhook notifications to inform about backup status.

🧾 Overview

    📦 Creates scheduled, timestamped backups of a project folder
    ☁️ Uploads backups to Google Drive via rclone
    🔁 Enforces smart backup rotation (daily, weekly, monthly)
    🔔 Sends optional webhook notifications (e.g., to Slack, Discord, or webhook.site)
    🕒 Supports automated cron job scheduling

⚙️ How to Install & Configure rclone

1. Install rclone

curl https://rclone.org/install.sh | sudo bash

2. Run configuration wizard

   rclone config

   
3. Create a new remote named gdrive:

    Choose n (new remote)
    Name: gdrive
    Choose drive as the storage (usually option 18)
    Use n for auto config (headless setup)
    On your local machine, run:

 rclone authorize "drive"
 Paste the resulting token JSON into your EC2 config prompt.

 4. Test upload

 echo "hello world" > test.txt
rclone copy test.txt gdrive:

Check Google Drive for test.txt.

Paste code from backup.py file.

✅ Run the Script Manually

  Make the script executable

chmod +x backup.py

 Run the script

python3 backup.py

Make the script executable

chmod +x backup_script.sh

execute the script

./backup_script.sh

⏲️ Automate with Cron

crontab -e

Choose nano as the editor (if prompted).
 Add Cron Job Entry

0 2 * * * /home/ubuntu/backup_script.sh >> /home/ubuntu/backup.log 2>&1

 Save and Exit In nano:

Press Ctrl + O, then Enter to save
Press Ctrl + X to exit

You should see:

crontab: installing new crontab
Verify Cron is Set

crontab -l


