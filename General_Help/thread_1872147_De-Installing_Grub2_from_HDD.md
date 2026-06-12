---
title: "De-Installing Grub2 from HDD"
date: 2011-10-30
forum: General Help
---

### Post by glene77is on 2011-10-30
[SIZE=3]*  Have a customer who had someone install Ubuntu 
as WUBI, inside of Windows XP.
*  HD was booting via with dual-boot options on the XP HD. 
[/SIZE][SIZE=3]*  Customer has a Terabyte HD as an additional HD. 
*  Apparently the Terabyte HD is connected as Master. 

[/SIZE][SIZE=3]*  Customer decided that he wants 
Ubuntu installed in a separate partition "Beside" Windows XP.
*  ( So, Terabyte HD is master (for data only) 
and XP HD is slave  (with grub2 & Wubi) )
*  Customer [U]installed Ubuntu to his Terabyte drive, 
along with MBR and grub2. [/U]

Now, he finds his Terabyte HD booting first, giving options of 
(1) Ubuntu on Terabye 
(2) XP HD with XP and Ubuntu (Wubi)

So, he wants to boot directly into the XP HD, again, just like last week. 

Problem #1:
How to remove MBR from Terabyte HD 
and make the system boot from the XP HD   (XP & Ubuntu Wubi). 

Problem #2:
On the XP HD, Ubuntu (Wubi) was giving an out-of-space type error.
Is there a setting to give more container-space to Wubu ?
The XP HD is 80 G, with 60 G unused.  
This is why he got the Terabyte HD and (apparently) connected it Master. 


Solutions ? 
Can he remove the MBR ?
What is the network-error problem ?  
(He has no network, is standalone desktop)
(eth0 is running OK, has FireFox internet access). 

[/SIZE]

---

### Post by oldfred on 2011-10-30
You did not mention network error?

Is this system IDE? As you mention master/slave. Some newer BIOS let you choose which drive to boot if SATA. Or you can change Master/slave settings. Either jumpers on drives or locations on cable select.

Best just to set grub to boot windows first if that is what is wanted. You can use grub customizer or manually edit grub.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Changing size of wubi is not particularly easy. Best just to copy all configurations to full install.
Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Since you have it installed you just need to copy /home & installed programs list.
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by glene77is on 2011-10-30
[SIZE=3]
Thanks, OldFred, 
[/SIZE][SIZE=3]I know I am wordy, but maybe you will see 
some macabre humor in his mistakes. 
[/SIZE]
[SIZE=3]Do you know how it is when you try hard not to step on a customers toes , 
in order to fix a problem ?   :guitar:

(1) His first complaint was that his M$ XP HardDrive system had Ubuntu installed,    but he was not able to find a separate partition.   
I ran Parted-Magic and Puppy, and discovered it was Wubi, setup by tech #1. 

(2) The problem he was having was that Ubuntu warned him 
he was running out of space.   
Therefore the Terabyte HD which he installed. 

(3) To fix this, he told me he wanted to install Ubuntu in the "Side-by-Side" mode from the Live-CD.      So, the customer became tech #2. 

(4) But when he tried that, he selected the Terabyte Data Hard Drive, 
and did the full install.  Mistake #2
Then any cold-boot called the Terabyte Data HD, MBR, bootloader, grub.cfg, all proper.    But the M$ XP HardDrive does not boot first. 

(5) Now, I am curious if there is any way to wipe the MBR, 
so that the Terabyte HD cannot boot,  which I think will be the state of 
affairs before he installed Ubuntu onto the Terabyte HD. 

His computer is a DELL, 80Gig + additional Terabyte HD.
Bootup F2 shows "SATA" on the options for boot order. 
When I disabled the Terabyte HD, boot failed. 
Makes me think the Master/Slave address lines were installed improperly. 

> **oldfred said:**
> 
You did not mention network error?
*** That is what he 'vaguely' tell me happens 
every time he uses the Ubuntu Live-CD. . 

Is this system IDE? As you mention master/slave. Some newer BIOS let you choose which drive to boot if SATA.
*** That is true.   The bootup F2 allows some switching like that.  

 Or you can change Master/slave settings. Either jumpers on drives or locations on cable select.
*** He swears this is not the problem.   
*** I agree with you that this is a "probable" fix. 

Best just to set grub to boot windows first if that is what is wanted. You can use grub customizer or manually edit grub.
*** Have manually edited grub.cfg on the booting Terabyte HD 
*** just to show him that I had found the files.    Now he is nervous.


HOWTO: Grub Customizer Updated for grub 1.99
The Grub 2 Guide (formerly Grub 2 Basics) manual way
Changing size of wubi is not particularly easy. 
Best just to copy all configurations to full install.
*** Understand.  It would be beyond him. 
*** He wants to install into a separate partition anyway. 

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
*** I will check this out, thanks. 
*** May be one of the things I should suggest to him. 

Since you have it installed you just need to copy 
/home & installed programs list.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) [/SIZE][SIZE=3]
*** Sounds like part of the fix. Thanks. 

I am running five different OS on my computer,   :D
and since I don't do strange things, I don't have strange problems. 
So, I don't have many solutions for other folk's strange problems.   :confused:

Your suggestions should be very helpful.
Thanks from an old electrician.   :P


[/SIZE]

---

### Post by oldfred on 2011-10-31
SATA does not have the master/slave settings. Only PATA/IDE. If using SATA drives you have to have a BIOS that allows changing boot order. But I have seen a few old Dell's that only booted the IDE drive and had one SATA port.

If Windows was the first drive its boot.ini will be mis-configured as it will only be looking for rdisk(0) not 1.  You can manually edit boot.ini but have to be careful with Linux editors on the line endings. But probably better to keep Windows as sda and make the new 1TB drive sdb if you can. Some mixed IDE/SATA systems automatically make the IDE drive sda.

---

### Post by glene77is on 2011-11-01
[SIZE=4]Thanks, OldFred.
That may be his best option.   
Just live with the Terabyte booting drive. 
From the bootup menu, 
there is a secondary option to reboot into the XP drive.  
He should just live with it.  

We don't setup problems like this, so . . .   :confused:[/SIZE]

---

### Post by DrBarley on 2011-11-05
I am Glene77is's customer and I want to explain how I solved this problem, in case it helps anyone else.

In Windows, I located and installed a small program called MBRfix.  Then I used Disk Manager to delete the partition on the Terabyte drive where the new Ubuntu installation was (thereby deleting GRUB and the ability to boot the computer).  Immediately I ran MBRFix and, well, it fixed the Master Boot Record.  It only took a second.  I rebooted and ascertained that I was back where I had been before this drama unfolded.

I turned off the computer, opened the case, and disconnected the data cable for the Terabyte, then booted the computer with the Ubuntu installation disk in the appropriate drive.  This forced the installation to occur on drive :0, instead of on the Terabyte as before.  (How Ubuntu decides to choose its drive is a mystery to me.)

So now I'm running 11.10 from my first drive alongside of Windows.

---

### Post by critin on 2011-11-05
Good for you!  I love having these issues to work out, and doing it--don't you?

 > (How Ubuntu decides to choose its drive is a mystery to me.)

Actually it doesn't choose for me.  I have to agree with what it wants to do and click 'forward'  or it just sits there.  lol  There is a radio button to click (where the drive shows) to choose another disk if you don't want the one that appears.   :P

---

### Post by DrBarley on 2011-11-05
> **critin said:**
> There is a radio button to click (where the drive shows) to choose another disk if you don't want the one that appears.Yes, I tried to do it that way, but when I chose a partition, it gave me an error message which I couldn't understand (as usual).  What's strange to me is, when I chose the option "alongside of Windows," it placed it as far from Windows as it could get!  (Until I disconnected the Terabyte.)

---

### Post by oldfred on 2011-11-06
Glad you got it resolved. If you can disconnect a drive that guarantees grub2's boot loader will not be installed to the wrong drive. Grub on any of the auto installs defaults to sda, but some systems do not make sda the drive you think it is and when installing to a second drive you want it on the same drive.
I partition in advance and manually install by choosing partitions and then with the combo box can choose where to install grub2's boot loader.

You could also reinstall the Windows boot loader with a Window repairCD or XP install disk. FixMBR is the command. And you can use Ubuntu or many Linux repair CDs to install a Windows compatible boot loader. Many ways to fix it and as long as you found one that works that is great.

Happy Ubuntu-ing.:)

---

