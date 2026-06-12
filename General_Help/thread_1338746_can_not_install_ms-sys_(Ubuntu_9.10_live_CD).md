---
title: "can not install ms-sys (Ubuntu 9.10 live CD)"
date: 2009-11-26
forum: General Help
---

### Post by ilovecng on 2009-11-26
Trying to restore my Windows MBR, but can't install ms-sys

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

---

### Post by Virtual Liberty on 2009-11-26
Repositories no longer contain this package. You can download it from [SourceForge]("http://ms-sys.sourceforge.net/#Download").

---

### Post by mechro on 2009-11-26
Try *sudo apt-get install mbr*

Er... sorry, forget that... my bad. Synaptic says **mbr** is "Master Boot Record for IBM-PC compatible computers" but I think it'll only install a Windows MBR if you've already got a back up of one.

---

### Post by The Dood0 on 2010-01-10
Hi, im have the same problem, but im not quite skilled enough to dig through a "tarball" and turn it into a ubuntu app... could i please get some tutoring or something for this?  I have no skills in compiling at all :)

---

### Post by vinnywright on 2010-01-10
what ver of windows are you trying to restor the MBR of ?

do you have the windows cd?

do you have a floppey drive ?

inshort if you have acsess to a windows ver of fdisk then runing fdisk /mbr will fix it .....cant remember the exact typing mabey fdisk/mbr 

or frum a XP cd runing in the recovery console fixboot should do it.

VINNY

---

### Post by The Dood0 on 2010-01-10
HI! im trying to fix windows 7 on my lenovo y450...  right now im rinning the live cd (thank goodness for linux!) and am having issues with the windows cds... i cant get them to boot more than once and even the providers are a bit puzzled... i did some research and found that i can rebuild the boot stuff with ms-sys... however since linux doesent carry it anymore in the apt-get deal i had to get it manualy online,  ms-sys is the best bet to fix this.  

Could i get a tutorial or instruction on how to compile ms-sys?

---

### Post by Leppie on 2010-01-10
> **The Dood0 said:**
> HI! im trying to fix windows 7 on my lenovo y450...  right now im rinning the live cd (thank goodness for linux!) and am having issues with the windows cds... i cant get them to boot more than once and even the providers are a bit puzzled... i did some research and found that i can rebuild the boot stuff with ms-sys...
if you only need it to reset the mbr to factory default, use lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by The Dood0 on 2010-01-10
[LEFT]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; LILO configuration. &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           
 &#9474; WARNING!                                                                 
 &#9474;                                                                          
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block      
 &#9474; device. Either your fstab is broken and you should fix it, or you are     
 &#9474; using hardware (such as a RAID array) which this simple configuration     
 &#9474; program does not handle.                                                 
 &#9474;                                                                          
 &#9474; You should either repair the situation or hand-roll your own             
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  
 &#9474; again to retry the configuration process. Documentation for LILO can be   
 &#9474; found in /usr/share/doc/lilo/.                                           
 &#9474;                                                                          
 &#9474;                                  <Ok> 

This is my error on config.... any ideas on how to fix it?  im running on the LIVE cd BTW
[/LEFT]

---

### Post by Leppie on 2010-01-10
> **The Dood0 said:**
> [LEFT]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; LILO configuration. &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           
 &#9474; WARNING!                                                                 
 &#9474;                                                                          
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block      
 &#9474; device. Either your fstab is broken and you should fix it, or you are     
 &#9474; using hardware (such as a RAID array) which this simple configuration     
 &#9474; program does not handle.                                                 
 &#9474;                                                                          
 &#9474; You should either repair the situation or hand-roll your own             
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  
 &#9474; again to retry the configuration process. Documentation for LILO can be   
 &#9474; found in /usr/share/doc/lilo/.                                           
 &#9474;                                                                          
 &#9474;                                  <Ok> 

This is my error on config.... any ideas on how to fix it?  im running on the LIVE cd BTW
[/LEFT]
never mind the warning (the livecd fstab causes this to appear), it will still let you reset the mbr ;)

---

### Post by The Dood0 on 2010-01-10
dident work :( is there anyway to get an already compiled ms-sys? or mabye another idea?

---

### Post by Leppie on 2010-01-10
> **The Dood0 said:**
> dident work :( is there anyway to get an already compiled ms-sys? or mabye another idea?
try the 7 restore cd: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by The Dood0 on 2010-01-10
allready tried it... dont work, my computer goes to the background then locks up... i went through the whole thing with the cds but to no avail, i will try the windows 7 command prompt boot rebuild to see if it works... will update results :)

---

### Post by michy99 on 2010-01-10
Try downloading the .deb from here:

[http://packages.ubuntu.com/dapper/ms-sys](http://packages.ubuntu.com/dapper/ms-sys)

---

### Post by The Dood0 on 2010-01-10
thats the same one i downloaded... i dont know how to install it... could u possibly link a "noob" instruction manual or somthin plz? Im learning how to do this stuff but this is way beyond me.

-thanks for helping me BTW :)

---

### Post by michy99 on 2010-01-10
You can install a .deb by double-clicking it.

---

### Post by The Dood0 on 2010-01-11
[http://ftp.debian.org/debian/pool/main/m/ms-sys/](http://ftp.debian.org/debian/pool/main/m/ms-sys/)

I downloaded a few but keep getting the same error "wrong architecture"
any idea how to resolve this?

---

### Post by The Dood0 on 2010-01-11
holy smokes! found one that worked!

---

### Post by The Dood0 on 2010-01-12
It appears that ms-sys did something it wasent supposed to do...  now when i turn on my laptop it goes to the Lenovo splash, then the screen goes black except for the ms-dos curser blinking in the upper-left like its doing something... i left it on overnight to seee if it was just repairing itself, but to no avail.... any input?:confused:

---

### Post by Leppie on 2010-01-12
try downloading the 7 recovery disk: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by The Dood0 on 2010-01-12
got it downloaded... trying it now

---

### Post by The Dood0 on 2010-01-12
Wont accept my partition table.... says bad partition table or something close to that right after the lenovo splash

---

### Post by Leppie on 2010-01-12
ok, i'm starting to run out of resources...
try either the [Ultimate Boot CD]("http://www.ubcd4win.com/downloads.htm"), or Hiren's Boot CD.
they both contain many tools, among which partition manipulation and boot recovery.

---

### Post by The Dood0 on 2010-01-12
Im sorry, im learning this stuff as i go, this is all new. thanks so much for helping though.

---

### Post by Leppie on 2010-01-12
don't worry, we're here to help you ;)

---

### Post by fastness on 2010-02-12
get the same problem, 

installed ubuntu on a winxp pc. 
After ubuntu, can't start XP after restore windows partition with an old ghost XP image.
Can't install MS-SYS with ubuntu9.10 live CD, not available.

Is there any way to run my windows + iTune?

---

