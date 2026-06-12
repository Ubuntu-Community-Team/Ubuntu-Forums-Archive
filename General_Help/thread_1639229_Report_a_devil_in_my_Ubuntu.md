---
title: "Report a devil in my Ubuntu?"
date: 2010-12-06
forum: General Help
---

### Post by fatharraxman on 2010-12-06
from time to time not always I log in to my Ubuntu, start few works then it auto reboot by itself, why? then every thing go smooth, every thing is working greatly, some days there is nothing like this happen today it happened once, I checked every thing no pitfalls any where? should I report a devil in my system

---

### Post by labinnsw on 2010-12-08
What is the brand of your computer and motherboard?

---

### Post by nolag on 2010-12-08
What apps where you running?  What kernel version do you have?  How much RAM do you have?  How much swap?  Please provide more info, it is hard to tell from what you have mentioned.

---

### Post by mastablasta on 2010-12-08
check the capacitors on your motherboard if they are bulged. this kind of issue you describing is usually caused by this or by failing power supply unit.

---

### Post by fatharraxman on 2010-12-08
Sorry
The slow response drew me to track answers from ICR chat but was not persuading to me (a bug?) .
I am using hp mini 110-1100 it is new and worked for three months with windows 7 starter before I erase windows into only Ubuntu desktop Maverik Meerkat 32-bit, it got 1gb RAM, 1.6 GHz, 1.6 GHz atom intel processor 130 free hard-disk, the Ubuntu was well and all basic problems were solved easily, I installed netbook interface and KDE to check sometimes, since 28 Oct, 5 days ago I obseved that when I restart or shut down and open computer again there is no pproblem until I open any application (Evolution,Terminal,any game, any browser, and so any application) the system auto-log out (as if the application I open got a log out button)into username screen, so I choose username and log in and every thing go as normal !!!  it only do that once at a session, but a new session will make it (restart or shut down), then gradually it started to be slower on start up, take a longer time at 'hp trade mark screen' where there is no response to any ctrl+alt+fsomething, I counted that to be an increasing time on start up, then it start to third problem after prolonged hibernate : a chaotic screen with black square at the quarter left of the screen , this happened three times and only restart will remove it to repeat the circle, all these problems occurred  in a Sequential phenomena that terrified me if  continued on who could expect what will happen so on 
any help?
please:P

---

### Post by labinnsw on 2010-12-09
Just to test if the problem is really with the OS. Free up a little space on the hard drive if possible and install something in that space. (Ubuntu, Mint, Fedora, SUSE or any other distro) Test everything over a periiod of time. If you do not encounter any problems, then you can rule out hardware.

The problem sounds to me like it is hardware related, but you are using hardware that I never heard of any problems with.

---

### Post by fatharraxman on 2010-12-09
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   14G  124G  10% /
none                  492M  288K  491M   1% /dev
none                  497M  7.6M  490M   2% /dev/shm
none                  497M  432K  497M   1% /var/run
none                  497M  4.0K  497M   1% /var/lock
/dev/sdb1             1.9G  1.7G  285M  86% /media/F9B9-FF2F
/dev/sdc1             961M  186M  775M  20% /media/Memory card
is his memory not enough or di I misunderstand you sir?

---

### Post by ldarby on 2010-12-09
HP not linux friendly but usually there is a log event that helps identify the problem. With this kind of issue, my approach is to delete all the files in /var/log to get a clean start (sudo rm /var/log/*log* messages ) then reboot (init 6). As soon as it comes up, log in and capture all the logs (cat /var/log/*log* messages >/tmp/all.log)
go through /tmp/all.log file and delete anything that looks OK or not relevant) then investigate whatever remains.
The suspend resume issue might be completely separate from the crashes, but that event will definitely leave records in the logs of what happened.  Look closely at the kernel log.
When you do reboot, look closely at screen messages.  Latest kernels don't do boot logging as well as in the past so there may be messages here you won't see in the logs.

---

### Post by fatharraxman on 2010-12-09
> **ldarby said:**
> HP not linux friendly but usually there is a log event that helps identify the problem. With this kind of issue, my approach is to delete all the files in /var/log to get a clean start (sudo rm /var/log/*log* messages ) then reboot (init 6). As soon as it comes up, log in and capture all the logs (cat /var/log/*log* messages >/tmp/all.log)
go through /tmp/all.log file and delete anything that looks OK or not relevant) then investigate whatever remains.
The suspend resume issue might be completely separate from the crashes, but that event will definitely leave records in the logs of what happened.  Look closely at the kernel log.
When you do reboot, look closely at screen messages.  Latest kernels don't do boot logging as well as in the past so there may be messages here you won't see in the logs.

It is very difficult to me to understand what you are talking about am new in linux and need a step by step instructions please

---

### Post by ldarby on 2010-12-09
understanding what the logs are telling you is an essential skill for working with Linux. Anytime a linux system does something you don't understand or don't want it to the first step to solving this in every case is to look at the logs in /var/log and see if there is a hint as to what went wrong.  I gave you some specific commands to run to reduce the amount of messages you have to look at. log in to ubuntu, start a shell applications/accessories/terminal and type in all the commands I gave you ie "sudo rm /var/log/*log* messages". this will produce a temporary combined log file for you to edit.  start the editor gedit and open /tmp/all.log.  you will see things that the system records in the logs. You have to determine if any of the messages are relevant to the problem you are having.

---

### Post by Sky Aisling on 2010-12-09
I am also trying to understand this process and I am new to Linux.

Could you give us directions of what to do in a simple line-by-line format?

Thank you

---

### Post by fatharraxman on 2010-12-09
rm: cannot remove `messages': No such file or directory

---

### Post by fatharraxman on 2010-12-09
the above is the result of sudo rm /var/log/*log* messages so what then? please

---

### Post by fatharraxman on 2010-12-09
What if I deleted files; messages , from system > var > log , manually without terminal usage ??:rolleyes:

---

### Post by ldarby on 2010-12-09
Good Job! you are guessing at the intent rather than just accepting what I told you. My fault on the messages, it should have been /var/log/messages.
The objective is just to look at all the logs in /var/log.  Removing the logs first is just to reduce the amount of stuff you have to look at. It is OK to do it any way that works. There are many ways to do things in Linux, the way I am showing you is just one.
If you look at the permissions on the files in the /var/log directory you will see they are owned by a user other than the one you are logged in with.  When you use the file manager nautilus to look at files you are doing so under your own account and can't delete files owned by someone else. To remove a file you do not own, you must become root.  The shell command sudo lets you become root temporarily. You could also use the command ( sudo nautilus /var/log ) to run the file manager as root.

---

### Post by fatharraxman on 2010-12-10
ldarby you are very very wonderful 
what about another file called messages.1 ??

---

### Post by fatharraxman on 2010-12-10
I removed the messages but terminal is not back to home should I kill it and reboot any way??


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177986&stc=1&d=1291958869[/IMG]

---

### Post by ldarby on 2010-12-10
the application called logrotate takes the current logfiles and backs them up, then recreates a new empty log file.  The most recent is given an extension of .0, .1, or .old.  older files are compressed and givenan extension of .gz.
delete all of those before you reboot.
reboot and run the command 
cat /var/log/*log* /var/log/messages >/tmp/all.log
This will capture the things recorded during the boot so that later messages do not cloud the issue.
then 
gedit /tmp/all.log
spend some time looking at the logs and trying to understand what each one means.
Gotta get so I can be ready for my day job. Good Luck!

---

### Post by fatharraxman on 2010-12-10
> **ldarby said:**
> the application called logrotate takes the current logfiles and backs them up, then recreates a new empty log file.  The most recent is given an extension of .0, .1, or .old.  older files are compressed and givenan extension of .gz.
delete all of those before you reboot.
reboot and run the command 
cat /var/log/*log* /var/log/messages >/tmp/all.log
This will capture the things recorded during the boot so that later messages do not cloud the issue.
then 
gedit /tmp/all.log
spend some time looking at the logs and trying to understand what each one means.
Gotta get so I can be ready for my day job. Good Luck!

I pasted the results in this [link]("http://paste.ubuntu.com/541903/") but it still auto-log out as soon as I opened an application

---

### Post by ldarby on 2010-12-10
Make sure you are fully up to date (apt-get update, apt-get dist-upgrade)
if that does not fix it, look up the errors that I filtered from your pastebin on the web and try some of the solutions you find.  There are known problems that produce this kind of issue.
1. permissions with an application called dbus
2. corrupt profile
3. out of date system files.
gdm-session-worker[1393]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

gnome-session[1515]: EggSMClient-WARNING: Desktop file '/home/fatharrahman/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
gnome-session[1515]: WARNING: Could not launch application 'cairo-dock.desktop': Unable to start application: Failed to execute child process "cairo-dock" (No such file or directory)
gnome-session[1515]: WARNING: Could not launch application 'docky.desktop': Unable to start application: Failed to execute child process "docky" (No such file or directory)

dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.74" (uid=1000 pid=2216 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.7" (uid=0 pid=1044 comm="/usr/sbin/console-kit-daemon))
gdm-binary[1001]: WARNING: Unable to find users: no seat-id found
gdm-simple-greeter[1391]: WARNING: Unable to lookup user name fatharra: Success

---

### Post by uRock on 2010-12-10
To see all log messages in one place, go to System> Administration> Log File Viewer.

---

### Post by fatharraxman on 2010-12-11
> **ldarby said:**
> Make sure you are fully up to date (apt-get update, apt-get dist-upgrade)
 There are known problems that produce this kind of issue.
1. permissions with an application called dbus
2. corrupt profile
3. out of date system files.


I am fully updated and upgraded and I tried all what you have said but still am very upset by my system, I observed that the second problem is solved so thank you the system is starting up very quickly following the the deletion of messages files at var/log but the first problem and the third problem still , and there is a new look for the first problem and that is at the auto relog in the theme is changed automatically into a customized thing that is not and not one of the damn known themes on earth 
Thanks to guys at IRC@freenode Udienzand & yofel who helped me report this problem at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/687641")

---

