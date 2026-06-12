---
title: "Persistent USB User Questions"
date: 2009-11-06
forum: General Help
---

### Post by DrMarcusAurelius on 2009-11-06
Hi,

I find myself using my Ubuntu Live USB all the time when I'm away from home and without my laptop.  I just created a new 9.1 version but, unlike my old 9.04 version, when I remove it from a computer and reboot, the system time is all out of whack.  Now my relatives don't want me booting from this on their computers.  Any idea how to make it so that I have the correct local time inside Ubuntu and the host computer's clock is not reset when others reboot in windows?

Also, I would love to change the way this boots so that the USB boots up more like a regular install.  That is, right now it boots to a menu asking what language you want, and then to another menu asking whether you want to install or run it live.  Is there any way to get this to boot to a login screen where I could be prompted to enter a user name and password?  Right now, if you set a user name and password on the main account it won't survive rebooting.

Thanks in advance to anyone who takes the time to reply.  I'm new to Ubuntu but I love it and check out the forums all the time.  This is my first post.

DrMarcus

---

### Post by DrMarcusAurelius on 2009-11-07
Nobody?

---

### Post by efflandt on 2009-11-07
System, Adminitration, Users and Groups.  Add yourself as an administrative user with password.  Then log out as ubuntu and log in as your user.  From there you change settings, add programs, etc. assuming you allotted disk space within your Linux system if you used the tool in System, Administration, USB Startup Disk Creator.

I could not seem to set time zone, etc. from System, Admin, Date and Time at first because it was grayed out.  But after right clicking on the time at the top of the screen  and playing around with that until it asked for a password, seems to have enabled System, Admin, Date and Time.

I am currently trying 9.10 on a 4 GB USB stick with 1.1 GB extra space allotted for the Linux filesystem besides the image files, plus 2 GB vfat space left on the stick (apparently mounted as /cdrom).  This is with java and flash added for browsing, color laser printer and cups-pdf printer configured, date/time set to auto update from time servers, ssh keys, browser cache, etc.

efflandt@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.1G  427M  616M  41% /
udev                  502M  272K  501M   1% /dev
/dev/sdb1             3.8G  1.8G  2.0G  48% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  502M  148K  502M   1% /dev/shm
tmpfs                 502M   64K  502M   1% /tmp
none                  502M   88K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw

efflandt@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1002        962         39          0         50        510
-/+ buffers/cache:        401        600
Swap:         2052          0       2052 (automatically found on hard drive)

efflandt@ubuntu:~$ date
Sat Nov  7 13:31:30 CST 2009

I am amazed. A complete Linux system in your coin pocket that can be securely run from any PC.

---

### Post by DrMarcusAurelius on 2009-11-07
When you add yourself as an additional user and set a password, do those changes remain after you close down and reboot?  Can you edit something to make the drive boot to this new account and bypass the default user altogether?  

Thanks

DrMarcus

---

### Post by Sud on 2009-11-07
Hi,

I am facing the same problem too.  Live USB (try without installing) is working but Persistence is not working for me as expected!

I created a persistent live usb image of Ubuntu 9.10 using the "USB Startup Disk Creator" tool on a 4GB USB stick with 1.5 GB allocated for Persistence.  Every time I boot through the USB stick, I am always prompted with Language selection and a menu to confirm whether I should try ubuntu without installing etc.   I was able to create a new user; I was able to switch user to this newly created id, but the new user created is not appearing in the login screen after boot.  In fact the login automatically happens with the default user.

If anyone was able to make persistent USB work with Ubuntu 9.10, please help and provide the instructions.

Thanks.

---

### Post by efflandt on 2009-11-08
If you assign it linux disk space when you create the bootable USB it creates a "casper-rw" file that it mounts as a loop device during boot, or if you have another suitable linux partition on the drive (not fat or ntfs) with a volume name of "casper-rw" (in small letters) it will use that to keep persistant configuration info and added programs between boots.

But regardless of what I do, even assigning a password to the ubuntu user and/or attempting to require password on login (which clears next boot), I cannot stop it from going directly into ubuntu user with no password (apparently root does an "su - ubuntu").  I have not found a script yet that controls that.  So it is not as secure as I thought unless you actually "install" Unbuntu to USB instead of just using a bootable install image.

But still it is more more flexible to configure in advance and easier to carry than a CD for testing things.  And if you really have something you need to keep a secret, you could use file encryption.

---

### Post by DrMarcusAurelius on 2009-11-08
Ok, there is a way to set a password on a persistent USB install.  Here is the link:

[http://forums.remote-exploit.org/backtrack-4-howto/25193-enable-bt-login-prompt-persistent-liveusb-mode-allow-password-changing.html](http://forums.remote-exploit.org/backtrack-4-howto/25193-enable-bt-login-prompt-persistent-liveusb-mode-allow-password-changing.html)

There is also a nice tutorial at Pendrivelinux.com on how to access the non-Ubuntu portion of the usb drive, here:  [http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/](http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/)

If anyone has advice on how to keep my Ubuntu usb from changing the time on the computer that boots it, I would be grateful.

---

### Post by dcstar on 2009-11-11
> **DrMarcusAurelius said:**
> 
.........
If anyone has advice on how to keep my Ubuntu usb from changing the time on the computer that boots it, I would be grateful.

When your persistent USB system has booted:
```
sudo dpkg-reconfigure tzdata
```

---

### Post by Sud on 2009-11-12
Hi DrMarcus,

I tried the instructions in "[http://forums.remote-exploit.org/bac...-changing.html]("http://forums.remote-exploit.org/backtrack-4-howto/25193-enable-bt-login-prompt-persistent-liveusb-mode-allow-password-changing.html")" but it still autologins with "ubuntu" user after reboot.   I still get the language selection menu and a menu prompt to confirm whether I should try ubuntu without installing after a reboot.

Are you able to get to the regular login screen after reboot?

Thanks.

-Sud.

---

### Post by DrMarcusAurelius on 2009-11-13
I have not tried this with my 9.1 live usb.  It worked on my 9.04 version, so there is that.  I haven't tried it in part because I'm not a programmer of any kind and when I tried the second tutorial above, it didn't work because 9.1 has changed some of its file configurations since 9.04.  For instance, the instructions tell you to unzip a file that no longer exists in 9.1.  I think the basic idea still works, but I'm not sure what code to substitute in the instructions.  So I'm hoping that in time the pendrivelinux folks will update their instructions.

As for the password protection, if I recall, you may have to disable automatic login within Ubuntu in order to get the password prompt.  Have you done that?

Good luck and let me know if you get it to work.  I'm sorry I'm no help.  Perhaps someone else who knows something about programming could weigh in.

DrMarcus

---

### Post by woop on 2009-11-14
[http://ubuntuforums.org/showthread.php?p=8317934#post8317934](http://ubuntuforums.org/showthread.php?p=8317934#post8317934)

I believe if you do a full install(treat the flash as a hard drive) as opposed to a live cd with casper for storing changes  that you dont get the languague screen and slow boot time. As of yet I dont know how.

itd be nice if someone would help :)


EDIT: right so on further research I found this
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

it explains that a flash usb drive isnt sufficient for a full install, as the write cycles will eventually trash it

something like this would be more suitable 
[http://www.everythingusb.com/external_hard_drives.html](http://www.everythingusb.com/external_hard_drives.html)

I remember reading this before but I forgot the specifics, maybe its slightly different for the new distros but I doubt it. I am going to stick with my slow live cd install unless others have ideas

---

