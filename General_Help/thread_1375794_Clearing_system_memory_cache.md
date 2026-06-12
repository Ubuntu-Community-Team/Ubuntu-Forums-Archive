---
title: "Clearing system memory cache"
date: 2010-01-08
forum: General Help
---

### Post by Mahngiel on 2010-01-08
Is there an equivalent for this in Ubuntu?

[quote=http://www.tomstricks.com/how-to-clear-memory-cache-in-windows-vista-to-speed-up-your-computer/]
Running multiple applications simultaneously in Windows Vista for long periods leads to a gradual decrease in system performance over time.Often the only option to this is a Windows Vista Reboot. Even if you close the application in the[** Windows Task Manager**]("http://www.tomstricks.com/check-performance-of-your-computer-with-windows-task-manager-and-resource-monitor/"), the tasks/threads associated with the application are not released completely, depleting the system’s memory resources making the system unstable and sluggish.
 Follow the below steps to create shortcut for clearing memory on your Windows Vista Desktop.
 
[LIST]
[*]Right-click on your desktop and Select New > Shortcut
[*]In type the location of the item path: Enter below information
[/LIST]
 **%windir%\system32\rundll32.exe advapi32.dll,ProcessIdleTasks**
 
[LIST]
[*]Click Next. In the next screen, Type a name for this shortcut: Ex: **Clear Memory or Process Idle Tasks**
[*]Click on Finish
[/LIST]
 Your **Clear Memory or Process Idle Tasks** shortcut is now created and whenever you feel that your Windows Vista computer is busy not responding to commands, just run this command and it should free up the system.Also note that this tweak works fine in Windows XP also.[/quote]

---

### Post by Kevbert on 2010-01-08
Please take a look at [[COLOR="Red"]bleachbit[/COLOR]]("http://bleachbit.sourceforge.net/news/test-bleachbit-070-beta"). It's in the repos, so you can install via Synaptic.

---

### Post by Mahngiel on 2010-01-08
this worked nicely, thank you.

---

