---
title: "wubi on windows 7"
date: 2010-08-20
forum: General Help
---

### Post by tejashs on 2010-08-20
does wubi work with windows 7
 earlier i had wubi installed on win XP and it was working near 100% but after i changed to WIN 7 it gives some error during boot up like
NTFS 5 wubildr is missing

my motherboard is ASUS M2N68-AM SE2

---

### Post by tejashs on 2010-08-26
come on guys, no one tried wubi on windows 7?

---

### Post by bcbc on 2010-08-26
Yes it works. If you still have the old wubi root.disk you can probably recover it. Or at least pull off any data you had on it.

---

### Post by tejashs on 2010-08-27
> **bcbc said:**
> Yes it works. If you still have the old wubi root.disk you can probably recover it. Or at least pull off any data you had on it.

i asked because when i installed ubuntu it doesn't show up on the boot menu

---

### Post by bcbc on 2010-08-27
> **tejashs said:**
> i asked because when i installed ubuntu it doesn't show up on the boot menu

Do you see any exceptions in the wubi-xxx.log file? (Under the %temp% directory). I assume you ran wubi.exe as an administrator.

---

### Post by tejashs on 2010-08-28
ya i ran it as an administrator, also tried  compatibility as windows xp SP3.
could not find the log file though

---

### Post by bcbc on 2010-08-28
> **tejashs said:**
> ya i ran it as an administrator, also tried  compatibility as windows xp SP3.
could not find the log file though

The log file should be in the following folder:
C:\Users\<yourusername>\AppData\Local\Temp

(entering %temp% should go there as well).

---

### Post by Mark Phelps on 2010-08-29
> **tejashs said:**
> come on guys, no one tried wubi on windows 7?

Lots of people have TRIED to use Wubi on preinstalled Win7 setups, but they ran into problems with the default two-partition installation scheme used by OEM vendors.

So, the default install more often than not, simply doesn't work.

But you're already getting some help in this area, so you may become an exception.

---

### Post by tejashs on 2010-08-29
i finally got it running, though i did noting but try installing in a different drive,
but, the problem i am facing now is that when i select ubuntu in the boot menu 
"try hd(0,0) wubildr missing"
or something similar appears for almost 2 minutes 
then ubuntu starts
i installed ubuntu in D: drive 
and also there are 2 primary drives C: and D:

---

### Post by bcbc on 2010-08-29
I installed on a win7 netbook with the oem boot partition - worked first time. But clearly there are some oddities with win7. Once it starts taking this much effort, then partitioning starts to look like less work.

There is a bug about the delays in booting you are experiencing and a proposed workaround to make it boot faster. [https://bugs.launchpad.net/wubi/+bug/566490](https://bugs.launchpad.net/wubi/+bug/566490)

---

### Post by tejashs on 2010-08-30
I got that corrected thank you very much.
But i dunno why but my keyboard does not work
And also it goes into command line mode.
the reason might be the copying of wubildr or the latest updates those are the only changes that has happened 

i had experienced these things before 
but not together before it had not happened together and i used to type startx or restart with mouse 
but now i need to power down my computer.
any suggestions

---

### Post by bcbc on 2010-08-30
Not likely the wubildr. Do you get any errors in your /var/log/syslog?

Did you say you had Ubuntu running before on the same computer without any problems, or did you have the same issues? Were you running a different version of ubuntu?

Note: it's also not good for wubi to be doing hard shutdowns...

---

### Post by tejashs on 2010-08-30
ya i was running ubuntu on win XP before, some times the keyboard used to stop working and i used to shutdown using mouse
and some other times it used to go to command line mode and i would type startx to return to graphical mode 
but now both things happen together so i had to power down the hard way

---

### Post by Frogs Hair on 2010-08-30
I don't know what to say , I've helped 6 people install Ubuntu with Wubi on W7 and it has worked great every time. Each was with a single hard drive with no other partitions. The last was yesterday with the latest Wubi exe.

---

### Post by bcbc on 2010-08-30
> **tejashs said:**
> ya i was running ubuntu on win XP before, some times the keyboard used to stop working and i used to shutdown using mouse
and some other times it used to go to command line mode and i would type startx to return to graphical mode 
but now both things happen together so i had to power down the hard way

Post your syslog - or check it to see if there are any errors.

Also you could try searching for your exact pc specs (motherboard, graphics card etc.) and see if there are any known issues with 10.04. You could try some boot options (noacpi, noapic etc.) to see if that makes a difference.

---

### Post by tejashs on 2010-08-31
> **bcbc said:**
> Post your syslog - or check it to see if there are any errors.

Also you could try searching for your exact pc specs (motherboard, graphics card etc.) and see if there are any known issues with 10.04. You could try some boot options (noacpi, noapic etc.) to see if that makes a difference.


>>where do i find syslog

>>my motherboard is ASUS M2N68-AM SE2  
([http://reviews.cnet.com/motherboards/asus-m2n68-am-se2/4507-3049_7-33632758.html?tag=specs](http://reviews.cnet.com/motherboards/asus-m2n68-am-se2/4507-3049_7-33632758.html?tag=specs))
with AMD processor
2Gb RAM
500 Gb sea-gate HDD

>>as for the boot options
i am a no brainier as far as these are concerned, most of the knowledge i have is from the past problems i had experienced.
thank you in advance

---

### Post by bcbc on 2010-08-31
> **tejashs said:**
> >>where do i find syslog

>>my motherboard is ASUS M2N68-AM SE2  
([http://reviews.cnet.com/motherboards/asus-m2n68-am-se2/4507-3049_7-33632758.html?tag=specs](http://reviews.cnet.com/motherboards/asus-m2n68-am-se2/4507-3049_7-33632758.html?tag=specs))
with AMD processor
2Gb RAM
500 Gb sea-gate HDD

>>as for the boot options
i am a no brainier as far as these are concerned, most of the knowledge i have is from the past problems i had experienced.
thank you in advance

Do you use the nvidia drivers? or the generic ones?

If you haven't installed nvidia drivers, have you tried booting with nomodeset: Hit 'e' on grub menu entry, add nomodeset after 'quiet splash' i.e. 'quiet splash nomodeset' (no quotes) and then CTRL+X to boot. See if that gives you issues.

---

### Post by tejashs on 2010-09-01
Yes nvidia drivers have been installed.
and the above things does not happen every time i boot, 
but occur once every 5 to 10 times i boot. 
should i still try the above mentioned procedure?

---

### Post by bcbc on 2010-09-01
> **tejashs said:**
> Yes nvidia drivers have been installed.
and the above things does not happen every time i boot, 
but occur once every 5 to 10 times i boot. 
should i still try the above mentioned procedure?

Not if you already have the correct drivers installed. Check syslog (System, Administration, Log file viewer)

---

### Post by tejashs on 2010-09-02
i have loaded 2 of the log files when i suspect the error took place
[http://ubuntuforums.org/attachment.php?attachmentid=168243&stc=1&d=1283432895](http://ubuntuforums.org/attachment.php?attachmentid=168243&stc=1&d=1283432895)
[http://ubuntuforums.org/attachment.php?attachmentid=168244&stc=1&d=1283432895](http://ubuntuforums.org/attachment.php?attachmentid=168244&stc=1&d=1283432895)

---

### Post by bcbc on 2010-09-02
> **tejashs said:**
> i have loaded 2 of the log files when i suspect the error took place
[http://ubuntuforums.org/attachment.php?attachmentid=168243&stc=1&d=1283432895](http://ubuntuforums.org/attachment.php?attachmentid=168243&stc=1&d=1283432895)
[http://ubuntuforums.org/attachment.php?attachmentid=168244&stc=1&d=1283432895](http://ubuntuforums.org/attachment.php?attachmentid=168244&stc=1&d=1283432895)

It's complaining about your BIOS. Make sure you have the latest version. (I can't say if this would resolve the problems) There are a few other things in there that raise questions, but now we're getting to an area where you need some expert help.

EDIT: try the BIOS update first, if that fails, try these suggestions.

Suggestion1, [create a bug in launchpad]("https://help.ubuntu.com/community/ReportingBugs"). Hopefully a developer will be able to get the correct information and help you. But the process is unlikely to be resolved quickly.

Suggestion2, try the 32bit Ubuntu. I know the 64bit is not recommended for daily use, but not sure why (flash is one reason). I also know that wubi will automatically download the 64bit if your cpu is capable of it. I don't think it matters if the chip is AMD or intel, I understand that i386 works on all chipsets and so does AMD64 on all 64bit chipsets.

---

### Post by tejashs on 2010-09-03
i think the 3 things you asked will take some time to execute as i have some exams coming for next week and you had hinted that the data saved in ubuntu can be preserved  and carried on to the next installation. can you elaborate how?

---

### Post by bcbc on 2010-09-03
> **tejashs said:**
> i think the 3 things you asked will take some time to execute as i have some exams coming for next week and you had hinted that the data saved in ubuntu can be preserved  and carried on to the next installation. can you elaborate how?
You can extract data from a root.disk by booting from a live CD and [mounting it]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?"). It sounds like you will have issues with this method since you can't boot Ubuntu successfully. 

You can also download programs that will let you browse the root.disk from windows e.g. [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (I haven't tried this myself but it's mentioned in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?") and supports ext4 file systems).

Taken from **ext2read.blogspot.com**
> FEATURES:
...
View/Read Ext2/ext3/ext4 partitions.
...
Support for disk and filesystem  images. For eg. Wubi users can just open their root.disk file through this program.

---

