---
title: "Adding WinXP Win_7 2 Grub"
date: 2010-02-20
forum: General Help
---

### Post by sandman3838 on 2010-02-20
Hello
I just received Win 7 and I installed to a HD 2nd Half of my Win_XP Hard Drive.  

If this HD is set to Boot first in the BIOS I am able to access the both Win_xp and Win_7.

Now I just installed Ubuntu 9.10 64bit to its own HD. This OS I can access by switching this drive to boot first in the Bios.  But it boots straight into Ubuntu there is no Windows option?

With the HD as it is now, set at first boot and accessing Ubuntu I was thinking on running:

sudo dpkg-reconfigure grub-pc

sudo update-grub2

Is this correct and and what HD should I point Grub reconfigure to?

Take a look at the Results file its from a Script file meierfra put out.

Thanks for your help and let me know if you need more info.

---

### Post by sandman3838 on 2010-02-20
I just ran this:

kevin@kj-Linux:~$ sudo grub-install --recheck /dev/sda
[sudo] password for kevin: 

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

kevin@kj-Linux:~$

---

### Post by sandman3838 on 2010-02-20
If it helps here is some more Info.  

Both Windows version are on a partitioned HD and Ubuntu is on another HD.

Winxp was originally installed to the first partition my C drive.

To the second Partition of the C drive I installed Windows 7.

With this I can get into Winxp and Windows 7 via the Windows 7 boot mamager.

Next I changed my boot order so that my Ubuntu HD was first in the list.

Then installed Ubuntu 9.10  64bit to the other HD.

When Ubuntu boots I do see loading GRUB but it goes straight into Ubuntu.  There is no Grub menu.

Now If I want to get back into Windows I simply have to change my boot order so that my Windows HD is first.

I suspect that I'm going to have to add entries to the:

gksudo gedit /etc/grub.d/40_custom

Does this help?

---

### Post by sandman3838 on 2010-02-20
Update:

To get the GRUB MENU 2 appear I edited the 
gksudo gedit /etc/grub.d/30_os-prober
 An changed the time outs from 1 and zero to 

if keystatus --shift; then
      set timeout=-0
    else
      set timeout=20

The Grub menu now appears for 20 sec.

Also, I added this into the:
gksudo gedit /etc/grub.d/40_custom

menuentry "Microsoft Windows XP Pro (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows 7 (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 496C05A527BA4582
drivemap -s (hd0) ${root}
chainloader +1
}

Now both versions of Windows are now in the list.

However I suspect that Win_7 needs to be (hd2,2)  
When selecting this as it is now I get a message that the NTFS is missing.

Now here is the strange thing.
When I select Windows XP I get the Windows 7 boot menu?
From here I see the Windows Boot entries for WinXP and Win_7 and I can access Windows XP but like I said not Windows 7.

---

### Post by meierfra. on 2010-02-20
> Now here is the strange thing.
When I select Windows XP I get the Windows 7 boot menu?
From here I see the Windows Boot entries for WinXP and Win_7 

That is the normal behavior. Remember  what I told you earlier:

> Let do some more planning ahead. Usually Win 7 will overwrite the Win XP boot loader and add an entry for XP to the Win 7 boot menu. If that happens you won't be able to boot XP directly from the Grub menu, but via "Grub Menu->Win 7 Boot Menu-> XP"

To avoid this, I suggest to create the Window 7 partition before hand and put the boot flags onto the Window 7 partition. (You can do that with gparted in Ubuntu or with the XP disk management) Then Win 7 will put its boot files onto the Win 7 partition.


Well you did not put the boot flag on the Win 7 partition  and so Win 7 wrote its boot loader to the XP partition.  Anyway, that can be fixed fairly easily, but we'll worry about this later.

First  we have to figure out why Window 7 does not boot via "Grub menu->Win 7 boot menu".

Just to make sure. Is this the current situation?

If you set  your bios to boot from the Window drive, you get the Win 7 boot menu and you can boot into Win7 and XP

If you set your  bios to boot from the Ubuntu drive, and choose  either of the Windows entries on the Grub menu, the Win 7 boot menu appears.  From  there you can boot into XP, but not into Win 7.

Is that correct?

What exactly happens if you pick Win 7 ? Any error messages?

Some Window 7 installations do not like the "drivemap" line. So change your second Windows entry in 40_custom to

menuentry "Microsoft Windows 7 (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

Save the file, run "sudo update-grub", reboot and see whether  the "Microsoft Windows 7" entry  on the Grub menu lets you boot into Win 7.

---

### Post by sandman3838 on 2010-02-20
HI!  Welcome back!

RESULTS:

If you set your bios to boot from the Window drive, you get the Win 7 boot menu and you can boot into Win7 and XP?

ANSWER = Yes Switching the HD I can access Winxp and Win_7

If you set your bios to boot from the Ubuntu drive, and choose either of the Windows entries on the Grub menu, the Win 7 boot menu appears. From there you can boot into XP, but not into Win 7.

Is that correct?

ANSWER = YES Switching to the Ubuntu HD I can access XP and not Win7 with the alterations I did in the 40_custom file.  But selecting the Window options in the GRUB menu drops me into the "Windows Boot Manager" first.

What exactly happens if you pick Win 7 ? Any error messages?

ANSWER = Yes Unlike with Winxp where I get the "Windows Boot Manager" Here I get no Win boot menu but:

BOOTMGR IS MISSING
PRESS CTLR+ALT+DEL TO REBOOT.

Some Window 7 installations do not like the "drivemap" line. So change your second Windows entry in 40_custom to

menuentry "Microsoft Windows 7 (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

Save the file, run "sudo update-grub", reboot and see whether the "Microsoft Windows 7" entry on the Grub menu lets you boot into Win 7.

ANSWER = I replaced what I had with what you suggested and I still get just:

BOOTMGR IS MISSING
PRESS CTLR+ALT+DEL TO REBOOT.

---

### Post by sandman3838 on 2010-02-20
You mentioned:

"Well you did not put the boot flag on the Win 7 partition and so Win 7 wrote its boot loader to the XP partition."

When you get the time, after all this, could you please send me to a like that explains this better?  Boot Flag?

I don't want to repeat this.  

Thanks

Just in case it might help here is another new run of your script file.

---

### Post by meierfra. on 2010-02-20
I'm still confused about one thing:

What happens if you do this:

Boot from the Ubuntu drive.
Choose Windows XP at Grub menu.
Choose Windows 7 at the Win 7 boot menu.

---

### Post by sandman3838 on 2010-02-20
I hope this helps....

With the Ubuntu HD as primary.

I get:

GRUB MENU - UBUNTU 	- ok  NO ISSUES

GRUB MENU - WINXP 	- "WINDOWS BOOT LOADER" - WINXP  (ok I'm able to access Winxp)
GRUB MENU - WINXP 	- "WINDOWS BOOT LOADER" - WIN_7  (system reboots)

( now I know that this is wrong, Windows Boot manager should not be coming up)

GRUB MENU - WIN_7	- ERROR - BOOTMGR IS MISSING  PRESS CTLR+ALT+DEL TO REBOOT.

You know if it helps you mentioned "flag the HD" is that before or after the Win_7 installation?  I'm writing all this through Ubuntu at the moment and I really haven't dome much to it I would have no problems just to re-install the thing?   Your call?

---

### Post by sandman3838 on 2010-02-20
Here is some more info:
I was reading around I I think what you were talking about "Flag" the HD was available in DPARTED.

I just installed but I didn't do anythig it shows 

/dev/sdc1    ntfs    WIN_XP      boot (flag)

/dev/sdc2    extended             lba
    /dev/sdc5     ntfs    WIN_7

---

### Post by meierfra. on 2010-02-20
> I would have no problems just to re-install the thing? 
I'm not sure that reinstalling will help.

> GRUB MENU - UBUNTU - ok NO ISSUES

GRUB MENU - WINXP - "WINDOWS BOOT LOADER" - WINXP (ok I'm able to access Winxp)
GRUB MENU - WINXP - "WINDOWS BOOT LOADER" - WIN_7 [COLOR="Red"](system reboots)[/COLOR]


GRUB MENU - WIN_7 - ERROR - BOOTMGR IS MISSING PRESS CTLR+ALT+DEL TO REBOOT.

All of this is just as expected. Except for the  "system reboots".

Lets have a look at your bcd:

Boot into Window 7 (by booting  from Window 7 drive)

Click on start.  Type "cmd" and press "Ctrl+Shift+Enter". This will open the Window 7 command line with administrative rights.

Type

```
bcdedit > C:\bcd.txt
```

This create the  file "C:\bcd.txt" on your C: drive.  Post the contents of that file.

---

### Post by sandman3838 on 2010-02-20
Question:

Could 
Click on start. Type "cmd" and press "Ctrl+Shift+Enter".
bcdedit > C:\bcd.txt

be something else?

All I get is access is denied?

---

### Post by sandman3838 on 2010-02-20
You know here is another thing.
I don't have that much on WIN_7 either.
Setting up "Boot Flag" and reinstalling WIN_7 and then Ubuntu could be a viable option?
  Your call

Think about it.  
Or is you find out something let me know.
It's getting late here I need to finish this in the morning.

Again thank you 1000 times over for helping me with all this.

---

### Post by sandman3838 on 2010-02-21
Wow i was trying to sleep and I was thinking this out.....
I need to get a life?  
Please be sure and check out my other postings above.

Still Good morning!

I found that original information you gave me on booting Win_7.

Quote:
"Let do some more planning ahead. Usually Win 7 will overwrite the Win XP boot loader and add an entry for XP to the Win 7 boot menu. If that happens you won't be able to boot XP directly from the Grub menu, but via "Grub Menu->Win 7 Boot Menu-> XP"
To avoid this, I suggest to create the Window 7 partition before hand and put the boot flags onto the Window 7 partition. (You can do that with gparted in Ubuntu or with the XP disk management) Then Win 7 will put its boot files onto the Win 7 partition.

You won't have to detach the Ubuntu drive to install Win 7 (although that is the safest way). Putting the Window drive first in the boot order should be enough. After you installed Window 7, just put the Ubuntu drive back in the first position in the Bios, boot into Ubuntu and run "update-grub". Update-grub should pick up "Windows 7" and "Win XP" and you should be able to boot all three OS directly from the Grub menu."

I did create the partition from DParted for Win_7 however I wasn't too clear about what you called Flagging the partition.  I think I found that option in DParted.  What if......

1.  With the Win HD as primary I drop in the Winxp CD and do a FIXMBR.  This should revert the system to boot straight into Winxp.

2.  Switch the HD back to Ubuntu as Primary access DParted and select the 2nd Partition (Win_7) as the Flagged HD.  Weither that means I need to Format and reinstall the Win_7 partition I'm not sure?  Note, Win_7 had only been on the system for two day and I have not even registered it yet.

3.  Switch the HD back to Win HD as primary and either Reinstall Win_7 or run Win Boot Manager?  It all depends on weither or not I had to format and re-install Win_7 or not?  

4.  Do as you said and switch the HD back so that Ubuntu is primary  and run Grub Update?

What do you think too much?

---

### Post by meierfra. on 2010-02-21
I don't think that reinstalling will solve your main problem ("system reboots" when trying to boot Win 7 via "GrubMenu->Win7 menu")
  
You can separate the Win 7 boot loader from the XP boot loader without reinstalling, but I rather figure out what is going wrong first.


If you really want to see whether reinstalling makes a differences you need to:

[LIST=1]
  [*] Boot to the repair console on your Window XP CD. Type "map" to determine the drive letter of your XP partition . Then  type "fixboot C:", but replace "C:" by the actual drive letter of  your XP partition.
  [*] Windows will not put boot the files onto a logical partition. So  boot into Ubuntu and open "GParted".  Delete your Window 7 (/dev/sda5) partition, delete the extended partition (/dev/sda2). Create a new primary ntfs partition. Right click on  the new partition and choose "manage flag" Choose "boot". Similarly remove the boot flag from the XP partition.
 [*]  Put your Windows drive first in the boot order and install Window 7
[/LIST]


> Could
Click on start. Type "cmd" and press "Ctrl+Shift+Enter".
bcdedit > C:\bcd.txt

be something else?

All I get is access is denied? 

Did you press "Ctrl+Shift+Enter" simultaneously? Did you get the "Do you want the following program to make changes to your computer"  Pop-Up? (Or a similar Pop-Up)

---

### Post by sandman3838 on 2010-02-21
Meierfra

You said:
"You can separate the Win 7 boot loader from the XP boot loader without reinstalling, but I rather figure out what is going wrong first."

If you want to see what wrong first that fine with me!
Totally your call.  I just thought you were getting tired of this and reinstalling might be a better way to go?  Again your call, If you want to do some more digging then I'm game if you are.

Do you still want me to do the three steps that you just mentioned?

Also about the:

Quote:
Could
Click on start. Type "cmd" and press "Ctrl+Shift+Enter".
bcdedit > C:\bcd.txt

Yes I did hit all three at the same tine but nothing happened, absolutely nothing.

Hey I don't know if it will help or not but here is some HW info.
Processor:
AMD Athlon 64 X2 Dual Core  6000+  3.00 ghz
Motherboard:
Gigabyte  GA-M55SLI-S4

---

### Post by meierfra. on 2010-02-21
> you were getting tired of this

I never get tired, unless I run out of ideas what to do next.

> Do you still want me to do the three steps that you just mentioned?

Not now.

> Yes I did hit all three at the same tine but nothing happened, absolutely nothing.


See whether this helps:

[http://www.lytebyte.com/2008/10/22/how-to-run-as-administrator-in-vista-command-line/](http://www.lytebyte.com/2008/10/22/how-to-run-as-administrator-in-vista-command-line/)

If that did not help:

Go to Start->Program Files->Accessories
Right Click "Command Prompt".
Choose "Run as administrator"

Hopefully that will open the Command prompt.

---

### Post by sandman3838 on 2010-02-21
That did it!
Right Clicking and Selecting run as administrator did it.

Here are the results:

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=E:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {bab8522c-1dd8-11df-9c7c-8940bb8e4c92}
displayorder            {ntldr}
                        {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Legacy OS Loader
------------------------
identifier              {ntldr}
device                  partition=E:
path                    \ntldr
description             Earlier Version of Windows

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {bab8522e-1dd8-11df-9c7c-8940bb8e4c92}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {bab8522c-1dd8-11df-9c7c-8940bb8e4c92}
nx                      OptIn


Now why "Ctrl+Shift+Enter" wasn't doing it's thing who knows?

You know I have to tell you although I might seem green to computers it's really just that I'm so new to Ubuntu and now Win_7.  Back in the day I sue to do tech support for Dos - Win31 - Win95 - Win 98 systems.  Ok so much for the bad flash back!  :)

So far I find Ubuntu/Linux systems totally fascinating!

---

### Post by meierfra. on 2010-02-21
Your bcd looks fine. But I just noticed that I had overlooked something. Would you add this to your 40_custom:


menuentry "Win 7  boot loader  on /dev/sdc1, no drivemap" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
chainloader +1
}

Run "update-grub".

Reboot and try the new menu item to boot Win 7.

---

### Post by sandman3838 on 2010-02-21
Will do!  I'm on my way!

In the mean time here is something to think about.....

I have been using thins motherboard for about 6 - 9 month now and about twice a week it shuts down.  Always at the "Loading Windows" splash screen.  Originally this was just a Winxp issue but it happened WIN_7 this morning.  And the really strange thing is that I have no issues like this with Linux/Ubuntu?

Check this link out I just found this while I was waiting on your reply.  

[http://www.techsupportforum.com/microsoft-support/windows-xp-support/202122-computer-shut-down-when-cold.html](http://www.techsupportforum.com/microsoft-support/windows-xp-support/202122-computer-shut-down-when-cold.html)

I just found this other MO that would run my HW.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813135075](http://www.newegg.com/Product/Product.aspx?Item=N82E16813135075)

Right now I trying to decide.....
Stick with this mo or get a new one before all the AMD2 Mo are no longer available?

---

### Post by meierfra. on 2010-02-21
> Stick with this mo or get a new one before all the AMD2 Mo are no longer available?
No idea. I'm  know nothing about hardware.

---

### Post by sandman3838 on 2010-02-21
Here is the  40_custom as it stands to date.

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Pro (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows 7 (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}
menuentry "Win 7 boot loader on /dev/sdc1, no drivemap" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
chainloader +1
}

RESULTS:

A.  MICROSOFT WINDOWS XP PRO  (ON /DEV/SDC1)
     - WINDOWS BOOT MANAGER
         - EARLIER VERSION OF WINDOWS = OK
         - WINDOWS 7 = REBOOT

B.  MICROSOFT WINDOWS 7  (ON/DEV/SDC1)
      - BOOT MANAGER IS MISSING   PRESS CTRL+ALT+DEL

C.  WIN 7 BOOT LOADER ON /DEV/SDC1,  NO DRIVEMAP
       - WINDOWS BOOT MANAGER
         - EARLIER VERSION OF WINDOWS = REBOOT
         - WINDOWS 7 = OK

---

### Post by meierfra. on 2010-02-21
> C. WIN 7 BOOT LOADER ON /DEV/SDC1, NO DRIVEMAP
- WINDOWS BOOT MANAGER
- EARLIER VERSION OF WINDOWS = REBOOT
[COLOR="Red"]- WINDOWS 7 = OK [/COLOR]

Great. I had diagnosed the problem correctly in my first post, but gave  you the wrong menuentry.

This should let you boot into XP and Win 7 directly from the Grub menu:

**Step 1 :   Edit 40_custom**

Add   this

menuentry "Microsoft Windows 7 (on /dev/sdc5)" {
insmod ntfs
set root=(hd1,5)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

to 40_custom
(Once everything is working you can clean up 40_custom  and deleted the other entries for Window 7)

The run

```
sudo update-grub
```


[B]Step 2 Copy the file  bootmgr and the directory Boot from the XP partition to the Win_7 partition via
[/B]

```
cd /mnt
sudo mkdir 1 5  
sudo mount /dev/sdc1 1
sudo mount /dev/sdc5 5
sudo cp -r 1/bootmgr 1/Boot 5
```

Due to your "raid" problem, the mount command may give you an error message. If this happens  you might try access to  your XP and Win_7 partition via "Places_>Computer" and copy "bootmgr" and "Boot" via the file browser. If neither of this works let me  know.


Once you succesfully copied "bootmgr" and "Boot":

**Step 3  Edit the bcd on your Win 7 partition.**

Boot into Window 7 and open a command prompt  via "Run as administrator" (just as before)

Then at the command prompt

```

bcdedit /store C:/Boot/bcd  /set {bootmgr} device partition=C:
bcdedit /store C:/Boot/bcd  /set {bootmgr} timeout 0
bcdedit /store E:/Boot/bcd  /set {bootmgr} default {ntldr}
bcdedit /store E:/Boot/bcd  /set {bootmgr} timeout 3

```

The last command sets the timeout of the Boot loader on your XP partition to 3 seconds. This will slow down booting into XP from the Grub menu by 3 seconds. But  if you set that timeout  to 0, you wont be able to boot into Window 7 when booting from the Windows drive. 


Reboot from your Ubuntu drive. You  should now  be able to boot into XP and Win 7 directly from your Grub menu.

---

### Post by sandman3838 on 2010-02-21
Before i go any further to STEP 3
I thought you would want to know that:

cd /mnt
mkdir 1 5
sudo mount /dev/sdc1 1
sudo mount /dev/sdc5 5
sudo cp -r 1/bootmgr 1/Boot 5

Didn't quite work Instead I ran:

cd /mnt
sudo mkdir 1 5
sudo mount /dev/sdc1 1
sudo mount /dev/sdc5 5
sudo cp -r 1/bootmgr 1/Boot 5

Now I looked through Places and Computer and there is a 1 & 5 folder in MNT and they are populated.

---

### Post by meierfra. on 2010-02-21
Looks good (sorry for the missing "sudo")

---

### Post by meierfra. on 2010-02-21
I just realized that you don't need to do step 4. So I removed it from the instructions.

---

### Post by sandman3838 on 2010-02-21
WOW That's good!

Because I was going to tell you that I can't seem to get the system to boot to the CD.

I have checked 3 times to see that items boot list reads.
 1. Floppy
 2. CDROM
 3. HD

I even tried
1.  CDROM
2.  CDROM
3.  HD

Now I just used the CD the other day?   Could we have changed something?

For now it's good to know that I I don't have to continue with the process.

Kevin   BACK in 15 min

---

### Post by sandman3838 on 2010-02-21
Ok Here is the menu as it stands not

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Pro (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
drivemap -s (hd0) ${root}
chainloader +1
}

** THIS FIRST ONE WORKED AS YOU SET IT UP WITH THE "WINDOWS BOOT MENU" SHOWING UP BRIEFLY FOR 2-3 SEC AND GOING RIGHT INTO WINXP.

menuentry "Microsoft Windows 7 (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

** THIS MENU DROPPED BE RIGHT INTO WINDOWS 7 WITH NO ISSUES.

menuentry "Win 7 boot loader on /dev/sdc1, no drivemap" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
chainloader +1
}

** THIS ONE WORKED AS FAR AS IT DROPS YOU INTO THE "WINDOWS BOOT MENU" I DIDN'T TRY THE "OLDER WINDOWS" OR "WINDOWS 7".

menuentry "Microsoft Windows 7 (on /dev/sdc5)" {
insmod ntfs
set root=(hd1,5)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

** THIS MENU ALSO DROPPED BE RIGHT INTO WINDOWS 7 WITH NO ISSUES.

---

### Post by sandman3838 on 2010-02-21
Is our final result for the Edit 40_custom going to end up like this?

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Pro (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 50600787600772d0
drivemap -s (hd0) ${root}
chainloader +1
}

menuentry "Microsoft Windows 7 (on /dev/sdc5)" {
insmod ntfs
set root=(hd1,5)
search --no-floppy --fs-uuid --set 496C05A527BA4582
chainloader +1
}

---

### Post by meierfra. on 2010-02-21
That's just as it should be.  To clean-up your Grub menu, delete the second and third Windows entry (named "Microsoft Windows 7 (on /dev/sdc1)" and  "Win 7 boot loader on /dev/sdc1, no drivemap" )
and  run "sudo update-grub".


> Now I just used the CD the other day? Could we have changed something?Nothing we have done should prevent you from boot  a CD.  Maybe something happened to the CD. See whether you can boot from the Ubuntu LiveCD.  Or maybe   you need to clean the lens of your CD drive.
Or maybe is related to the problems you have with your motherboard.

---

### Post by sandman3838 on 2010-02-21
Sorry for the delay i got a call from my mom and my dad was trying to fertilize the yard? He has a bad leg and shouldn't be doing that!  So I ran over there and got the job done.

Where were we....

Oh!  Everything is just fine now and the menu is all cleaned up.

As for that issues with the CD, Ubuntu CD worked just fine.  I'll have to find out whats the deal with the Win 7 CD later.

Again thank you so very much for all your help!  You are the best!  :KS

---

