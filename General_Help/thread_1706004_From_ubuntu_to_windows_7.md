---
title: "From ubuntu to windows 7"
date: 2011-03-13
forum: General Help
---

### Post by shankly769 on 2011-03-13
Hello this is my first post here,and sorry to tell you that i came here to seek help,

currently i had to install ubuntu through my friend because i had problem booting the win 7 cd for formating,i had the BOOTMGR is missing windows screen,a friend told me to install this so my pc will run normal settings again,my bios settings are set to run from cd,then i tried to run the win 7 but when i do restart ubuntu is appearing again and again

please can you help me by telling me how i can run the win 7 cd setup?so i can install win 7 again?do i have to ghanghed something from ubuntu settings?

thanks

---

### Post by grahammechanical on 2011-03-13
This is a support forum. Please do not apologize for seeking help. We do not have all the answers. We can share our knowledge and experience.

You say

> i had problem booting the win 7 cd for formating,

So, the problem with the CD not booting existed before Ubuntu was installed. And the problem with the CD not booting still exists after Ubuntu has been installed.

Is the CD clean? Are there any scratches on its surface? When you installed Ubuntu did you choose the option to install alongside the original operating system? Or , did you tell the installer to use the entire disc?

Regards.

---

### Post by shankly769 on 2011-03-13
hi,yes the cd is clean because before i had made another copy,so,at first i made reinstall win 7,because i was having problems cd booting from drive,after the reinstall i tried to format,but as i choosed the location it told me that i dont have enough space,i went back and a window for startup, errors apeard and i think i stopped it and made a restart,then it apeared the BOOTMGR is missing windows and nothing became bootable,i burned trough my friend a win n7 boot disc but it didnt heleped,the win 7 boot disc worked on my friends pc,but on mine no
So he told me install ubuntu and after install win 7

ubuntu installed perfectly great without no interuptions,

i put the win 7 cd ,bios are set to run from cd but it starting me ubuntu again,i made several startups but still ubuntu is comeing on

---

### Post by MARP1961 on 2011-03-13
Have you tried putting your Windows 7 Install CD in the drive before actually switching on?

---

### Post by shankly769 on 2011-03-13
> **MARP1961 said:**
> Have you tried putting your Windows 7 Install CD in the drive before actually switching on?

yes,

can i try to uninstall ubuntu,then try win 7 cd?how can i uninstall ubuntu

---

### Post by MARP1961 on 2011-03-13
You will need a working live CD of Ubuntu or Windows to delete any partitions. You need to find out why the Windows disk will not boot first. Anyone else know why?

---

### Post by shankly769 on 2011-03-13
> **MARP1961 said:**
> You will need a working live CD of Ubuntu or Windows to delete any partitions. You need to find out why the Windows disk will not boot first. Anyone else know why?

what u mean working live CD of Ubuntu or Windows?

i have ubuntu cd and the windows 7 cd

the ubuntu cd booted perfectly well

---

### Post by decrepit on 2011-03-13
sounds like your bios is not recognising the win7 cd as bootable.

What are you trying to achieve?
A working win7 machine or a dual boot ubuntu and win7 machine?

What and why do you want to format?

---

### Post by louieb on 2011-03-13
Sure sounds to me that your win 7 cd is bad and your out of luck.  

Did you have Win 7 up and running at one time on the PC?  If so maybe you can fix it with a [Vista/Win7 Recovery Disc &#8212; NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") 

also it would help us help you if you would post the output of [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  - instructions are in the iink.

---

### Post by shankly769 on 2011-03-13
> **decrepit said:**
> sounds like your bios is not recognising the win7 cd as bootable.

What are you trying to achieve?
A working win7 machine or a dual boot ubuntu and win7 machine?

What and why do you want to format?

no A working win7 machine,from ubunto,and if possible delete ubuntu

---

### Post by shankly769 on 2011-03-13
> **louieb said:**
> Sure sounds to me that your win 7 cd is bad and your out of luck.  

Did you have Win 7 up and running at one time on the PC?  If so maybe you can fix it with a [Vista/Win7 Recovery Disc — NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") 

also it would help us help you if you would post the output of [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  - instructions are in the iink.


yes m8 i was with win 7 ultimate,i had the win 7 boot disc but it did worked on my friend pc,on mine no,thats why he told me to run ubuntu so then i can run win 7 setup but it failed,maybe i can download it again ,i have the [Windows 7 Recovery Disc 32-Bit (x86) Edition ,]("http://neosmart.net/downloads/miscellania/Windows%207%2032-bit%20Repair%20Disc.torrent")

but it failed to run too,maybe i did something wrong in bios?but i set it boot from disc

and yes how can i use [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  -

---

### Post by shankly769 on 2011-03-13
hi i think i managed to save the file,

see if you can help

thanks

---

### Post by louieb on 2011-03-13
Thanks it helps. Win 7 has no boot files. This usually happens when a PC is set up to boot 2 versions of windows such as XP and Win7.  Microsoft by default will put the boot files in only one of the installs. 

Did you have another Windows install on the 160GB hard-drive at one time? 

Don't know for sure if the recovery disk can fix - but its worth giving a try. 

Before you try to fix - 1st set the boot flag on the Win7 partition (can use Gparted on the Ubuntu live CD for this) - this tells the recovery disk where to put the boot files. 

2nd - go into the bios setup and make the 30gb drive 1st in the boot order.

---

### Post by shankly769 on 2011-03-13
> **louieb said:**
> Thanks it helps. Win 7 has no boot files. This usually happens when a PC is set up to boot 2 versions of windows such as XP and Win7.  Microsoft by default will put the boot files in only one of the installs. 

Did you have another Windows install on the 160GB hard-drive at one time? 

Don't know for sure if the recovery disk can fix - but its worth giving a try. 

Before you try to fix - 1st set the boot flag on the Win7 partition (can use Gparted on the Ubuntu live CD for this) - this tells the recovery disk where to put the boot files. 

2nd - go into the bios setup and make the 30gb drive 1st in the boot order.

few minutes aga i thought i worked because by mistake i disconected the 160 disc instead,and it began instalation and gave me the 40 gb disc ,

hi,yes on the 160GB i had win 7 installed and yesterday eve i had made the reinstall ,and when i do the  30gb drive 1st in the boot order i have to install win 7 there?and how to use Gparted ?

how and where to go in bios to seek the boot drive?

---

### Post by louieb on 2011-03-13
Getting into BIOS setup varies by PC - when the PC 1st starts you press some key - which key is the question?  For example on my laptop its <F!2> but on my desktop its <F2>.  Other common keys are <esc>, <del>.  If you don't have the user doc then Google you PC model.  Sometime the key to press is displayed briefly at startup.    

Gparted has a good user interface here an old but still valid overview [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

Anyway right click on the partition - look for the option "Manage flags" - the boot flag can be turned on or off there. - Just remember after  setting the flag  - click on apply (the check-mark icon at the top.

---

### Post by Mark Phelps on 2011-03-13
> **shankly769 said:**
> no,thats why he told me to run ubuntu so then i can run win 7 setup but it failed,

You can't use Ubuntu to install Win7. 

It comes on a DVD, not on a CD.

If you're sure it's a CD, then it's likely a recovery CD or a repair CD.  If it's the first, it can only REINSTALL Win7, and will need a Recovery partition on your drive containing a Win7 image file.  If it's the second, it can NOT be used to install Win7; it can only be used to repair an existing installation.

---

