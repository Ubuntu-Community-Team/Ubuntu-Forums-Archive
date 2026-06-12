---
title: "Basic Linux Commands for the Absolute Beginner"
date: 2010-09-09
forum: General Help
---

### Post by YasirMX on 2010-09-09
Hi,

I've been gathering up some commands which I believe will help novice users get acquainted to Linux. If possible move this to sticky

Getting used to Linux seems to be a daunting task for Novice users as it is considered as a completely different exposure to an environment. In fact, the Linux Terminal (after the kernel) is the root of the system since it is a means of system administration and here you’ll learn some basic commands which are followed by a brief description of its utility.[INDENT]lpr file.ext
[/INDENT]Send the filename “file” with extension “ext” to the printer[INDENT]ls -ar
[/INDENT]List all files in the current directory using recursive mode[INDENT]cd /etc/
[/INDENT]Switch to the directory /etc[INDENT]who
[/INDENT]List users who are currently logged in[INDENT]tty
[/INDENT]List active Terminals – There are up to 7 terminals on Linux. You can switch to e.g terminal 5 by Holding ALT and Pressing F5[INDENT]cp file1 file2
[/INDENT]Duplicate file1 – Give it the name file2[INDENT]system-config-display
[/INDENT]Configure the display – Triggers the display manager using the above command[INDENT]cat /etc/fstab
[/INDENT]Display contents of the file /etc/fstab to the terminal[INDENT]rm file1.txt
[/INDENT]Delete file1.txt from current directory[INDENT]pwd
[/INDENT]Prints Working Directory – Tells the user the current directory[INDENT]mkdir dir1
[/INDENT]Create directory dir1 – Note Directory are case-sensitive Dir1 and dir1 are not the same[INDENT]rmdir dir1
[/INDENT]Deletes the Directory dir1[INDENT]useradd user1
[/INDENT]Adds a new user names user1[INDENT]userdel user1
[/INDENT]Deletes user1 from the system[INDENT]passwd user1
[/INDENT]Sets the password of user1[INDENT]su user2
[/INDENT]Switch to user2&#8242;s profile – Terminal will prompt for password if user2 is password protected[INDENT]groupadd hello
[/INDENT]Creates a new group called hello[INDENT]groupdel hello
[/INDENT]Deletes the group hello[INDENT]ln file.txt /home/user/Desktop/file2.txt
[/INDENT]Creates a hard link, in other words if file1.txt is deleted file2 is not and contains contents of file1.txt[INDENT]ln -s file1.txt /home/user/Desktop/file2.txt
[/INDENT]Creates a soft link – A shortcut! if original file is deleted shortcut cannot like to original file[INDENT]ps -ax
[/INDENT]Lists all processes and their pid[INDENT]ps axjf
[/INDENT]Prints a process tree – Parent and Child Process format[INDENT]kill -9 2304
[/INDENT]Sends signal SIGKILL (-9) to pid 2304. In other words, kills the process 2304


**Changing File Permissions**[INDENT]chmod +x file1.sh
[/INDENT]Set file1.sh to executable mode. In other words, typing **./file.sh** in the terminal will execute the script. To make the file read, write and executable, running the command **chmod +rwx file1.sh** will do so. Additionally if the file was set to read, write and execute and you want it to be read-only, **chmod -xw file1.sh** will do the trick.
 Note:
 
[LIST]
[*]r stands for read
[*]w stands for write
[*]x stands for execute
[*]introducing +w will introduce write mode while -w will remove write mode. This is same for other switches like **x** and **r**
[/LIST]
 **Finding files**[INDENT]locate fstab
[/INDENT]This command will list the locations where the expression “fstab” was found. Alternatively if you are looking for the file **fstab** the following command will help you out.[INDENT]find / -name fstab
[/INDENT]Notice the “/” and the switch “-name”. The “/” tells the find command to look in the root directory while “-name” switch tells find to locate the filename. The above command returned the following[INDENT]/etc/fstab
/usr/share/doc/mount/examples/fstab
[/INDENT]**Advanced File Display**[INDENT]head /proc/cpuinfo
[/INDENT]Returns the first 10 lines of the file /proc/cpuinfo. Alternatively **head -n11 /proc/cpuinfo** will return the first 11 lines of the file.[INDENT]tail /proc/cpuinfo
[/INDENT]Returns the last 10 lines of the file /proc/cpuinfo. Using the command **tail -n12 /proc/cpuinfo** will return the last 12 files of the file /proc/cpuinfo[INDENT]more /proc/meminfo
[/INDENT]This will allow the user to scroll from top to bottom of the screen. Use the **enter key** to scroll down.[INDENT]less /proc/meminfo
[/INDENT]Allows scrolling through the screen in both directions (UP and DOWN) using the ENTER, Page UP and Page Down Keys.
 **Listing Hardware Information**[INDENT]lsusb
[/INDENT]Lists usb devices/buses[INDENT]lspci
[/INDENT]Lists pci devices[INDENT]lshal
[/INDENT]Lists HAL(Hardware Abstraction Layer) devices.
 **Memory Information**[INDENT]free
[/INDENT]Displays information about physical memory and swap space.[INDENT]top
[/INDENT]Displays real time memory usage (see screenshot below)
 [IMG]http://img713.imageshack.us/img713/7665/screenuo.png[/IMG]Linux Memory Usage

 **System Shutdown and Restart**
 The piece of information below has been used with permission from [geekscribes]("http://www.geekscribes.net").[INDENT] shutdown [- shutdown parameters] [ time parameter] [ optional message ]

shutdown parameters: r = reboot, h = halt, c = cancel shutdown (time parameter is then not required)

Some examples:

shutdown -r now    <-- **Reboot immediately**
shutdown -h 19:00  <-- **Shutdown (Halt) the system at 19h**
shutdown -h +5 "System will shutdown"   <-- [B]Shutdown the system in 5 mins from now, and tell users why.

[/B] [/INDENT]I hope this helps you guys out. Alternatively, I've set up a Linux blog at [http://killershock.online.fr](http://killershock.online.fr) 

Regards,
Yasir

---

