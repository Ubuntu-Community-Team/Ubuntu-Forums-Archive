---
title: "Virus or trojan attack"
date: 2010-02-15
forum: General Help
---

### Post by valhalla2100 on 2010-02-15
Hello,

I can't log into my computer.  I think that I got infected
by a virus or trojan.

The computer starts up and get to the screen where there 
is the Ubuntu logo.  Underneath the logo is the following
message:

- One or more of the mounts listed in /etc/fstab can not be
- mounted.

- home:wait for UUID=OF35671b-8231-4d15-af3d-d027b6484e66

- press escape to enter the recovery.

I pressed and get to the command line.  
root@slinc01_: 

(slinc01 is computer's name)
It seems that I am to put something into the command line
but have no idea.  Can not access the on-line information.

My problem started when I went to a webpage that came in
a google alert for PhotoShop.  That webpage was on the 
screen for a few seconds before it automatically switched
to another site.  That site unleased a barrage of pop up
windows.  I tried to close the browser but could not.  I
turned the computer off.  I turned it back onl and was 
able to do something before I quit.

The next day I was able to get to the internet but I was
not able to get the Thunderbird e/m client to function.
I closed Thurnderbird a few times but that did not solve
the problem.  

I shutdown the computer and rebooted a few mintues later.
I then got the above message.  It won't allow me to get
to anything now.  

The problem must have been due to some attacked from the
website.  Everything was working okay before then.

Thanks in advance for advice.

Thomas

---

### Post by saif_held on 2010-02-15
Check this thread might help you:
[http://ubuntuforums.org/showthread.php?t=1318593&page=4](http://ubuntuforums.org/showthread.php?t=1318593&page=4)

I honestly don't know the reason behind this but I doubt a virus or a Trojan is capable of doing this. [personal opinion]

---

### Post by SlugSlug on 2010-02-15
quick fix:

sudo cp /etc/fstab /etc/fstab.bak

sudo nano /etc/fstab

will show something like this

# / was on /dev/sdb6 during installation
UUID=1a5f0500-a2c5-46a4-9668-fe101df32163 /               ext4    relatime,errors=remount-ro 0       1


make it look like this

# / was on /dev/sdb6 during installation
/dev/sdb6  /               ext4     relatime,errors=remount-ro 0       1

do that for all entrys  or just your / & /home

---

### Post by elliotn on 2010-02-15
Also try fsck and reboot

---

