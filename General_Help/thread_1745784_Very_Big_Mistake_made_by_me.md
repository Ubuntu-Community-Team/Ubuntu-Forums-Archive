---
title: "Very Big Mistake made by me"
date: 2011-05-01
forum: General Help
---

### Post by kmkmahesh on 2011-05-01
I did a big mistake with my stupid thinking,

i did 

> 
sudo chmod 777 /etc/*.*


like that i did a stupid thing,

but now i am getting so many problems so plz help me

i am getting these type of errors

1. while i am using sudo
> sudo: can't open /etc/sudoers.d/README: Permission denied
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting


2. synaptic startup manager not starting now

3. service mysql start
> 
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.48" (uid=1000 pid=6704 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))


plz help me abt this 

i tried lot of tricks

some are provided below
[http://ubuntuforums.org/showthread.php?t=1585242](http://ubuntuforums.org/showthread.php?t=1585242)
[http://ubuntuforums.org/showthread.php?t=1586269](http://ubuntuforums.org/showthread.php?t=1586269)


4. i installed fedora 14 for some important issue, after that i tried to add the ubuntu for grub used in fedora, but it wont work, so i reinstalled grub from ubuntu cd and worked fine, 

i attached my results.txt file which contains my hard disks details

so please help me how to add the fedora option to grub 


5. please suggest my i just want to install the virtual machines in ubuntu i mean i just want to try windows and linux too i tried qemu but i cant add any virtual hard disk to install any operating system

Please help me for this i cannot reinstall any operating system now, because lot of things done in every operating system, 


6. can any one tell me how to upgrade the ubuntu using the cd/dvd i cannot use to upgrade the operating system using internet connection bcz i am using very slow connection of speed 115.2kbps i can download(ask) the cd/dvd image from another place(person)


Help is really appreciated

Thnx in advance

---

### Post by dragonfly41 on 2011-05-01
Looks like you are in for a reinstallation .. read this thread ..

[http://ubuntuforums.org/showthread.php?t=1718582](http://ubuntuforums.org/showthread.php?t=1718582)

---

### Post by WorMzy on 2011-05-01
Oh dear. Reinstalling would be your best bet, but if you want to struggle with it and see if you can fix it manually, start with this: [http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo").

---

### Post by _joecrawford on 2011-05-01
A fresh reinstall would save you a lot of hassle and headaches.

---

### Post by Rhubarb on 2011-05-01
If you do want to boot off a live CD to change all the individual file permissions back to the correct ones, then this is what you're in for:
[LIST=1]
[*]You need a list of all the permissions for all the files and directories in /etc
[*]According to the output of "sudo ls -lR /etc", you'd be in for changing about 4340 files and directory's permissions.
[/LIST]
So, if it took you 10 seconds to chmod a file, it'd then take you around 12 hours non-stop to do.

You'd be much better off backing up your /home/username directory, re-install ubuntu, install your apps, then copy back the contents of your /home/username directory.
- Depending of course how much you need to backup, and how fast your internet connection is.
Re-installing requires less attention and less brain power, and usually less time.

Having said all this, it should be possible to make a bash script to read the file permissions of a healthy /etc directory contents, and apply those file permissions to your corrupted /etc directory contents - I won't volunteer this as I'm sleepy and will probably make a silly mistake too.

Hopefully after your silly mistake you'll have more respect for sudo and bash - I've learnt a few lessons the harder way (like back up your files regularly, secure delete can be very nasty!).

Hope you get it all fixed soon.

---

### Post by kmkmahesh on 2011-05-01
> **WorMzy said:**
> Oh dear. Reinstalling would be your best bet, but if you want to struggle with it and see if you can fix it manually, start with this: [http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo").

i tried so many of the above i hardly installed LAMP in my ubuntu it takes more than 15hours to install, because of my slow connection

i want to triple boot windows, fedora & ubuntu also, 

i want to know is it possible to install the LAMP server softwares using cd/dvd but not using the internet

as a beginner i dont know any thing 

so i want to fix this problem

Thnx for replies

---

### Post by ninjaaron on 2011-05-01
what's the "777" do? I've never used that one.

---

### Post by polardude1983 on 2011-05-01
> **ninjaaron said:**
> what's the "777" do? I've never used that one.

I believe that makes every file of his act as an executable if I'm not mistaken

---

### Post by kmkmahesh on 2011-05-01
some thing worked 

[http://ubuntuforums.org/showthread.php?t=1556403](http://ubuntuforums.org/showthread.php?t=1556403)


but i am getting the error while i am using sudo and then asking for password
> sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700
this is solved with the help of this 
[http://ubuntuforums.org/showthread.php?t=1556403](http://ubuntuforums.org/showthread.php?t=1556403)
mysql problem solved by these links
[http://ubuntuforums.org/showthread.php?t=926504](http://ubuntuforums.org/showthread.php?t=926504)
[http://ubuntuforums.org/showthread.php?t=627374](http://ubuntuforums.org/showthread.php?t=627374)


now my synaptic package manager also running, but i dont know why mysql is not running

i want to upgrade to ubuntu 11.04 using cd/dvd  media

and i want to add the fedora to my grub

 plz help

---

### Post by Vaphell on 2011-05-01
> what's the "777" do? I've never used that one.
777 means read, write, execute permissions for owner, group, others
r = 4, w = 2, x = 1, just add the numbers to get desired combination
rwx = 7
r-x = 5
rw- = 6
etc.
you can see rwxrwxrwx notation when you use ```
ls -l
``` command

and this is what happens when you try to screw with permissions for a bit of convenience.

---

### Post by kmkmahesh on 2011-05-05
just help me to add fedora 14 in my grub

---

### Post by vahnx on 2011-05-05
They need to add a permissions backup by default in Ubuntu in-case this happens. Or some sort of System Restore... by default.

---

