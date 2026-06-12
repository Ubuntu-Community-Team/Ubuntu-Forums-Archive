---
title: "Not getting background daemon statup service notification message box"
date: 2011-06-22
forum: General Help
---

### Post by typhoon.2010 on 2011-06-22
[FONT=Verdana][SIZE=2]Hi All,

I have created a script named [/SIZE][/FONT] [FONT=Verdana][SIZE=2]**ssh_inotify.sh **to check **/var/log/auth.log** log file for newly started ssh session and display a question message box. This script uses **inotifywait **to monitor this above log file for modify file event and **zenity** to create question message boxes.
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Now i have created a startup service config file named **ssh_inotify** under **/etc/init.d** folder and placed the script **ssh_inotify.sh** under **/usr/sbin** and **chmod **this script to be executable.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] The service config file **ssh_inotify** uses **start-stop-daemon** to run this script as background process.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Now theproblem is that when i start this service using **sudo service ssh_inotify start**, the service is started, [/SIZE][/FONT][FONT=Verdana][SIZE=2]I can confirm this using **ps -A | grep ssh_inotify** also i can check for the PID associated with it under** /var/run/ssh_inotify.pid. **Now when i ssh to my machine, i do not get the question message box, I am writing in log file and in that i can see that the message under cancel button option for question message box is getting printed.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]This script runs perfectly when run directly or using [/SIZE][/FONT][FONT=Verdana][SIZE=2]**start-stop-daemon **command directly (exact command as typed in service config file above) on terminal, but not when this same command is executed using service file.[/SIZE][/FONT]
[SIZE=2][FONT=Verdana]Can someone please suggest me the solution and reason for such behavior when same command executed under different mode (using service or directly from terminal).[/FONT][/SIZE]
[SIZE=2][FONT=Verdana]If you guys require code, i can attach the files (currently i am in office so don't have access to these files.)[/FONT][/SIZE]

---

### Post by typhoon.2010 on 2011-06-23
Hi Guys,

Anyone please help me out on this.

---

