---
title: "No root file system is defined."
date: 2009-11-02
forum: General Help
---

### Post by wolfemancs on 2009-11-02
I had Wubi installed and working fine for version 9.04, and decided to try upgrading to 9.10.  I had planned to have the evening to do it, but my girlfriend surprised me with a visit, and I figued I'd let it keep installing while we went and did something else.  While it was installing, I switched my monitor cable and keyboard over to my other box (usually just running as a DC cruncher w/ no input required), so I could look up bowling alleys on the internet.  When I moved the keyboard back over to the upgrading box 4-5 hours later, it shut off (this box has always seemed to have problems w/ plugging and unplugging devices while it's running)  So I re-booted it and it wouldn't boot into Ubuntu.  I don't remember the error message but I think it's the one I'm still getting which I'll get to later.  I assumed that the install blew up when the power dropped so I rebooted into Windows.

I uninstalled Wubi, and downloaded and ran the Wubi 9.10 installer.  It went through fine, until it asked for the re-boot.  When I selected Ubuntu from the boot menu, the following came up on the screen:
Completing Ubuntu Installation
[Ubuntu logo in white getting brighter and dimmer]
[Desktop background appears]
Checking Installation
Setting up Clock
Checking Installation [% complete gets up to 457% (yes over 100)]
Setting up Partitioner

and then I get:
ERROR
No root file system is detected.
Please correct this from the partitioning menu

But all I have is an ok button, and when I press the OK button, the window disappears and then reappears.  

I re-uninstalled Wubi, ran Windows chkdisk, defragged my hard drive (trying to get rid of any history of Wubi (also nothing in the add/remove programs in Windows) but I'm pretty n00b-ish) and re-ran the Wubi 9.10 install only to have the same problem.

I found something in the release notes about "Unable to Load Linux Drive" thought that sounded promising, tried to work through the Grub 2 stuff, uncommented the "GRUB_DISABLE_LINUX_UUID=true" line, but when I run "sudo update-grub" I get:
grub-probe: error: cannot find a device for /.

Any thoughts?
Thanks,
Craig

---

### Post by wolfemancs on 2009-11-03
Summary of long post above:

Wubi 9.04 installed and working
Attempted upgrade to 9.10 through update manager
Lost Power to computer during upgrade
Uninstalled Wubi
Installed Wubi 9.10 Windows portion

Restarted computer, and during installation verification get the error, "No root file system is defined.  Please correct this from the partition menu"

Tried the "Unable to Load Linux Drive" help from the installation notes, when running update-grub get the error:
grub-probe:  error:  cannot find a device for /.

Any thoughts would be appreciated.
Thanks a lot,
Craig

---

### Post by coffeecat on 2009-11-03
I have virtually no experience of Wubi, but googling "no root system is defined wubi" brought up a lot of hits with earlier version of Ubuntu. I couldn't find anything helpful for 9.10. From what I understand of wubi, it's a virtual machine held in one file in C:/ubuntu, so this sort of message sounds like a problem within the file itself, so Windows' chkdsk is unlikely to help.

You might want to keep an eye on the forums. As more people use 9.10 in Wubi this may come up more with, hopefully, a fix.

In the meantime you may want to reinstall Jaunty as that seemed to work OK in Wubi. And if you don't want to do a conventional dual-boot install with Ubuntu on its own partition(s), you could look at [VirtualBox]("http://www.virtualbox.org/"). So long as you have enough RAM, you could have Karmic in a VBox guest machine and Jaunty in Wubi. Karmic is running OK for me as a VBox guest with MacOS as the host, so it should do just as fine with Windows as a host.

Last thing. I'm afraid you helped your thread to disappear by bumping it after only 2 hours. There is an unanswered posts team which might have picked this thread up had you left it unbumped for 24 hours. I only came across it by chance. I thought I'd point that out because this is a very busy forum, and it's difficult for new members to know what to do when their posts don't get answered.

Good luck!

---

### Post by wolfemancs on 2009-11-03
Thanks for the help.  I did reinstall the 9.04 Wubi, and I'll just continue using that until I see a solution pop up on here for my problem, or until there's some sort of minor update that happens.  

I don't want to run it in a VirtualBox version because the reason I'm running Ubuntu at all is so I can run 64-bit since I only have 32-bit Win XP.

Thanks for the forum info as well. . . I'll keep that in mind in the future, I was just hoping to get it fixed last night while I had a free evening, and I didn't know when I'd have time to get back to it.

CW

---

### Post by BubuXP on 2009-11-14
I have this problem too.
Downloaded and burned the 32bit iso.
Made a fresh install of Windows 7 and installed wubi.
At the restart the installation checking said 457%, then the percentage restarted and when arrived to 100% the "No root file system is detected" message appeared continuously.
I have to post something to receive better help? Like the installation log I see on a similar 1-year-old thread?

---

### Post by MJRogers on 2009-11-15
I had the same problem.  When the computer first boots there is a prompt to press escape for boot options.  I selected demo and it did boot.  It basically ran the same as the live CD.  It didn't save any changes or details after shutdown, but but did run.

---

### Post by BubuXP on 2009-11-16
> **MJRogers said:**
> I had the same problem.  When the computer first boots there is a prompt to press escape for boot options.  I selected demo and it did boot.  It basically ran the same as the live CD.  It didn't save any changes or details after shutdown, but but did run.

Yes, but it's not like installing. It doesn't retain my custom settings in this mode.
Nobody knows where the problem could be? I was thinking about not adequate ext4 support, but this problem happened in previous release of wubi also...

---

### Post by blahdieblah on 2009-11-20
I too have this problem. Running Windows 7 and attempting to install Ubuntu Netbook Remix.

---

### Post by duckdown on 2010-01-20
Same problem here.

Running brand new single Windows 7 installation, single SATA drive in PC.  Chose 17GB default partition for wubi.exe and downloaded Ubuntu 9.10 desktop image.  

After I reboot into ubuntu, it says Checking Installation and then just repeats "No root filesystem is defined.  Please correct this from the partitioning menu" over and over..

People have been mentioning this in similar threads for all this time, and its still not fixed?

What is the deal here?

---

### Post by duckdown on 2010-01-22
bump for help.

still no root filesystem defined.

wheres all the WUBI support?  I even posted logs, is this all for nothing?

---

### Post by lionclaw on 2010-01-28
Same problem here :(  I'm certainly willing to help troubleshoot the problem if someone can point me in the right direction.

Installed win7 64-bit, installed wubi, restart and I get the "no root file system is defined" error after selecting Ubuntu.

---

### Post by Robster2 on 2010-01-28
Wubi does not work with Windows 7 straight up.   You have to change the compatibility mode to Vista.

Right click wubi.exe 

Select properties 
Go to the compatibility tab 
Check "Run this program in compatibility mode for:" 
Select Windows Vista from the drop-down list.
Press Apply and OK
Run the installation as normal.

[http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html](http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html)

---

### Post by lionclaw on 2010-01-28
Just gave it a try, no go.  Still "No root file system is defined" after boot and selecting Ubuntu.

A bit about my machine - Intel e6300 on a dg965wh mobo w/4gb ram.  Two 320gb sata drives setup in raid 0.  Win 7 is installed.  I'm trying to install Karmic via Wubi.

I also tried installing Karmic in a new partition after shrinking the win7 partition.  It installs fine but when it restarts it goes straight to windows, no grub.

---

### Post by ketav7786 on 2010-02-05
I got same error message today... I tried to install it in different drive but its still there...
 
 
I dont think wubi 9.10 has any problem of compatibility with windows 7 64bit... previously I installed wubi 9.10 and ubuntu was running perfectly...
 
 
Any one has the solution for this problem..?

---

### Post by fred.marceau on 2010-05-12
Same issue here, trying 9.04/9.10 or 10.4 and Wubi in Windows 7. Any improvement on this ?

---

### Post by praveen18 on 2010-05-17
Even i am facing the same issue when trying it boot into ubuntu 10.4 (wubi install) in my sony vaio laptop (VGN-NW265F). My current operating system is Windows 7 (64 bit) in Intel Dual Core processor. 

Let me know if someone found out a solution for it.

---

### Post by malc3D on 2010-07-18
I was wondering if anyone has found a solution to this problem yet as I have just run into the same issue.

I am also on windows 7 64bit.

It seems to get to the stage where it is getting the time from the network time server the percentage shoots up to 271% then I get the continuous no root file system is defined error and I can only get out of this by powering off the laptop. I am also able to run the demo mode

Is there anywhere I can find older versions of Wubi so I can try getting one of the working versions?
Has anybody managed to get any versions of this working in windows 7 64bit?

thanks in advance

---

### Post by bobttt on 2010-09-28
I've manage to resolve this issue. Running HP Mini 210 Windows XP with Ubuntu 10.04.

**- Try reducing the number of Primary Partition in the hard disk to 2 before installing.**

The default HP hard drive comes with 3 primary partition (1 boot, 1 recovery, 1 tools), and 1 extended partition where the OS goes.

You can use Windows Disk Manager (XP/Vista/7) to view the hard disk partitioning structure.

I used EASUES Partion Master tool (freeware [http://www.partition-tool.com/](http://www.partition-tool.com/)) to remove the last Tools Partition to leave only 2 Primary partitions, then installed via Wubi in Windows XP.

Important Warning :
- You may want to backup the deleted partition data beforehand.
- Even if you backup, the default recovery tools/CD/DVD might not work after the partition removal.

Proceed at your own risk.

---

