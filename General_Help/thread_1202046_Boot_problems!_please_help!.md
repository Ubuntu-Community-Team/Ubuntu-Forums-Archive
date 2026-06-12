---
title: "Boot problems! please help!"
date: 2009-07-01
forum: General Help
---

### Post by jhp88 on 2009-07-01
New to Ubuntu and loving it, just one MAJOR problem.

I have a Dell Inspiron 1505 laptop that **was **running windows xp.
I recently partitioned my My Book (USB interface) to have Ubuntu but also left room for storage. I'm having no problems with Ubuntu so far on the My Book.

HOWEVER, after installing Ubuntu I was only able to run XP when the My Book was plugged in. 

This was a problem. I searched these forums and others and found similar issues. I tried: 
[http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html)

What I did:
> sudo su
password
grub
find /boot/grub/stage1   >>>>returned (hd1,4)
root (hd1,4)
setup (hd0)
exit

**Now I can't run XP at all, even with the My Book plugged in.**

Help would be much appreciated.

---

### Post by nothingspecial on 2009-07-02
Have a look [[COLOR="Magenta"]here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Main_Page")

---

### Post by Soul-Sing on 2009-07-02
> **jhp88 said:**
> New to Ubuntu and loving it, just one MAJOR problem.

I have a Dell Inspiron 1505 laptop that **was **running windows xp.
I recently partitioned my My Book (USB interface) to have Ubuntu but also left room for storage. I'm having no problems with Ubuntu so far on the My Book.

HOWEVER, after installing Ubuntu I was only able to run XP when the My Book was plugged in. 

This was a problem. I searched these forums and others and found similar issues. I tried: 
[http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html)

What I did:


**Now I can't run XP at all, even with the My Book plugged in.**

Help would be much appreciated.

Sorry to ask. did you ran this via a live-cd?
If you close grub, use quit.

---

### Post by lindsay7 on 2009-07-02
> sudo su
password
grub
find /boot/grub/stage1 >>>>returned (hd1,4)
root (hd1,4)
setup (hd0)
exit 


I think you need to change the commands to

sudo grub
password
find /boot/grub/stage1 >>>>returned (hd1,4)
root (hd1,4)
setup (hd1)
quit

Also, you may need to change the booting order of you hard drive in your bios if you have trouble booting to both windows and ubuntu after making the changes I suggest. I just had to do this on my computer.

---

### Post by jhp88 on 2009-07-02
Thanks for everybody's help so far, but still having issues. 

nothingspecial:
> Have a look [[COLOR=Magenta]here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Main_Page")I burned a super grub disk and followed the instructions here:
[http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)
no changes

leoquant:
> Sorry to ask. did you ran this via a live-cd?
If you close grub, use quit.     No I did not use a live cd.

lindsay7:
> I think you need to change the commands to

sudo grub
password
find /boot/grub/stage1 >>>>returned (hd1,4)
root (hd1,4)
setup (hd1)
quit

Also, you may need to change the booting order of you hard drive in your bios if you have trouble booting to both windows and ubuntu after making the changes I suggest. I just had to do this on my computerI've tried the commands you suggested. In my BIOS the boot order is Internal HDD, then CD, then USB.

Now when I try and run windows (with or without my external hdd) i get the error:
"Error loading operating system"
and I have no options. 

Additionally, when I go back to Ubuntu, I can no longer access my internal drive at all. It used to be NFS mounted right on the desktop. :confused::confused:

Would appreciate any more tips.

---

### Post by Soul-Sing on 2009-07-02
Has to be done in a live session, using a live-cd.....

---

### Post by jhp88 on 2009-07-02
Thanks for everyone's help: I have resolved the problem.

For those holding their breath, the solution was to load the fixmbr and then fixboot commands from a windows XP boot cd.

---

### Post by papenpj on 2009-07-02
Ok the problem you were having is the MBR was changed and was pointing to the boot partition of your MY BOOk. what you would need to do is resize the main drive on your laptop to allow you to have a 200MB partition(which should be more than generous) where you could locate the boot folder. That way when your mybook isn't connected grub can still point to the boot folder and allow booting of XP. But also you could connect your external and have it able to boot Ubuntu again because that is where all the system files would be located.

---

