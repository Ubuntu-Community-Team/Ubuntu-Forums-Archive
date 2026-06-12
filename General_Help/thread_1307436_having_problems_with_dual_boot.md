---
title: "having problems with dual boot"
date: 2009-10-31
forum: General Help
---

### Post by Gatorade on 2009-10-31
I'm trying to setup a dual boot pc. after windows xp is installed and working, I tried to install ubuntu 9.04.

after going through everything, however, I tried to boot windows again and it says starting up... but it just hangs there.if I restart and choose ubuntu , it boots into it no problems.

I did this exact same procedure on my dell inspiron 8200 and it worked fine. tried it on my friends desktop but I don't understand why it screwed up the windows install.

can anyone help me out here?

---

### Post by Gatorade on 2009-10-31
I was just wondering , can I install ubuntu first , and then install windows xp after and still get dual boot? or do I need to install windows first?

I was gonna try it this way instead since I'm experiencing problems doing it the other way.

---

### Post by Herman on 2009-10-31
It's a little easier to have Windows XP installed first, to a primary partition, and then install Ubuntu later.
Most people do it that way simply because most computers come with Windows already installed in them when they're new from the store so they don't have any choice in the matter. Unless we build our own computer we normally have Windows foisted upon us whether we like it or not.
Ubuntu is well designed to take over the role of dual booting because it uses GNU GRUB, which is a the world's best boot loader and  multiboot compliant, it automatically adds Windows to the boot menu. Normally no editing needs to be done by hand and no settings need adjusting. Ubuntu has an able partitioning program too. Only a very small percentage of times there are various kinds of problems, but then hey, that's computers for you. :D

It doesn't matter which end of the disk Windows is in, it might even be a little better to put Windows in the last half of the disk and install Ubuntu in front of it.
The actual physical position on the hard disk doesn't seem to matter, and neither does the partition number, Windows XP will boot okay as long as boot.ini has the right details.
I have tried all kinds of crazy experiments with Windows XP and have always been able to get it to boot. Sometimes people even bring me old computers that haven't booted for years and I get them fixed and running again.

I'll tell you a secret, a lot of people spend a lot of time defragging Windows, but most people forget that Windows needs a file system check too. A good file system check once in a while. The best way to run a file system check in Windows is from a Windows XP 'Installation CD', (or the CD for appropriate version of Windows).
Unfortunately, a lot of computers are sold without any CD, but just a recovery disk or a recovery partitions nowadays. But if you can get hold of a Windows 'Installation Disk, you can use the 'Recovery Console' in that to run CHKDSK /R from the command line and that fixes a lot of Windows problems.
That might even be your problem too. It is recommended to run a file system check in Windows right after resizing with GParted, and usually Windows will do so automaticlly but your friend's computer isn't quite getting that far. Maybe you need a Windows Installation Disk.
Here's a link that might help you with the Windows XP Recovery console, (in the 'Installation' Disk,  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").
Sometimes Windows needs a file system check, followed by defrag or two, followed by a good cleanout of temporary (junk) files, and another CHKDSK followed by another defrag and so on.

It's possible to do it the other way around and install Ubuntu first. 
If you do then Ubuntu will install GRUB in the first hard disks' MBR and since there will be no other operating system at that time it will not be automatically set up with a boot entry for Windows.
Then when you install Windows it will overwrite the MBR again with it's boot loader code, only Windows doesn't have the ability to easily be configured for booting other operating systems, you can do it with EasyBCD if you want to though.

---

### Post by Herman on 2009-10-31
If you install Ubuntu first, then Windows XP and you want to boot with GRUB, it's a simple matter of re-installing GRUB to your first hard disk's MBR and overwriting the Windows boot loader code again.
Don't worry, the boot sector is made of the same material as the rest of the hard disk, it won't wear out, we can copy and overwrite boot loader code there almost forever and it won't hurt anything.
The other half of the MBR has the partition table in it, that's the part to be careful with, but now there are good programs for working with that and fixing it too. The MBR doesn't deserve the fear that has followed it from the old days when people didn't have any easy way of seeing and controlling what happens there. 

Then you'll need to manually edit GRUB's menu.lst file with a boot entry for Windows.

It doesn't really matter if you boot with Easy BCD in Windows or GNU GRUB in Ubuntu, but GNU GRUB is free and 'open source', meaning it's possible for programmers to read the source code and make sure there's no nasty surprises in it, and they're free even to improve it if they want.
It's presumed that if you're taking the time and going to the trouble of installing an open source operating system like Ubuntu that you're sick and tired of being a victim of closed source (binary) programs. Most of them are okay, but how do you know for sure? 
I'm pretty sure EasyBCD is okay though.

Just use whichever boot loader you like and install either OS first, it doesn't really matter. Either will work. :D

---

### Post by Gatorade on 2009-10-31
hi Herman,

thanks for the replies so far.

I went ahead and installed windows first since I spoke to somone else and he said it would be easier that way.

I was just watching a youtube video where a guy installed a dual boot setup within windows.

I was thinking of trying it this way instead. I just wanted to know how it was going to run though. if its going to be slower or not, and if there's any benefits of installing it side by side that you don't get when installing it within windows.

also, does this require the cd all the time?

---

### Post by Brain-free on 2009-10-31
> I was just watching a youtube video where a guy installed a dual boot setup within windows.

Are you talking about [this]("http://wubi-installer.org/")?

If so, from what I know it's pretty safe, just not as fast as it would be if installed in a separate partition.

And no, it needs the live CD solely for the installation within Windows.

---

### Post by Gatorade on 2009-10-31
yes, that's the one he recommended.

here's the youtube vid [http://www.youtube.com/watch?v=UdI8_92QTkQ&feature=related]("http://www.youtube.com/watch?v=UdI8_92QTkQ&feature=related")

---

### Post by gadolinio on 2009-10-31
> **Gatorade said:**
> hi Herman,

thanks for the replies so far.

I went ahead and installed windows first since I spoke to somone else and he said it would be easier that way.

I was just watching a youtube video where a guy installed a dual boot setup within windows.

I was thinking of trying it this way instead. I just wanted to know how it was going to run though. if its going to be slower or not, and if there's any benefits of installing it side by side that you don't get when installing it within windows.

also, does this require the cd all the time?

As far as i know, installing ubuntu within windows has the vulnerability of ubuntu depending on windows's health. So if windows has some problem that forbids it from booting/working properly/etc, you could loose your ubuntu install as it is a program depending on the former OS.
I have both installed in separated hard drives. I bought the computer with windows, then bought another HD drive in which i installed ubuntu. No configuration was needed: every time i turn the computer on, the GRUB prompt appears and i choose between winXp and ubuntu. That's it.
The CD is not required after the installation.

---

### Post by Gatorade on 2009-10-31
just an update...


I ended up installing it from the cd , inside windows and its working fine.

I was going to download wubi, but it was going to take 5 hours.
doing it from the cd was very fast.

---

### Post by Herman on 2009-10-31
:D I haven't tried installing Ubuntu inside Windows, I always install them side by side. 
Once or twice I have installed Windows inside Ubuntu though, and that's pretty cool!
The good thing about it is we can have Windows running inside one workspace and Ubuntu has lots of other workspaces, (I always set Ubuntu up with 12 workspaces). That way it's easy to just click on Windows workspace when a person wants Windows, the rest of the time one can be using Ubuntu. It does slow the computer down though, I think it requires a PC with pretty good hardware to get any decent speed when two operating systems are running at the same time, understandably when I think about it.

With dual booting, either operating system is faster, but at first most people find themselves rebooting a lot to go do things the way they're used to in Windows. It can be quite a nuisance for people going through that stage of the learning curve. Soon most people learn how to use Ubuntu and they don't need to reboot so often.  :D

---

### Post by gadolinio on 2009-11-02
> **Herman said:**
>  Once or twice I have installed Windows inside Ubuntu though, and that's pretty cool! 

How do you do that? Does it require a special software?

---

### Post by Herman on 2009-11-03
I have tried VboxGtk and it seems to meet my requirements.

You should be able to install that easily in Ubuntu via Add/Remove or Ubuntu Software Center, or Synaptic or apt-get.

---

### Post by Gatorade on 2009-12-25
> **Herman said:**
> I have tried VboxGtk and it seems to meet my requirements.

You should be able to install that easily in Ubuntu via Add/Remove or Ubuntu Software Center, or Synaptic or apt-get.

what's VboxGtk?

is that how you installed windows inside Ubuntu? I might try it out.

how do virus' and spyware affect a machine if windows is installed within Ubuntu?

---

### Post by repairman1946 on 2009-12-25
I've just installed Ubuntu. How do I get the **GRUB's main menu** dual boot option to come up? Rebooting my computer only loads windows. I installed Ubuntu to a separate hard drive, than where windows is.

---

### Post by Gatorade on 2009-12-25
> **repairman1946 said:**
> I've just installed Ubuntu. How do I get the dual boot option come up? Rebooting my computer only loads windows. I installed Ubuntu to a separate hard drive, than where windows is.

it should come up right away and you hit the down arrow to select which one to boot.

I'm not sure how it works if you install it to a separate HD, I've always done it on the same drive.

I was thinking of trying this method.

[http://www.youtube.com/watch?v=74Eyx4VDEWU]("http://www.youtube.com/watch?v=74Eyx4VDEWU")

---

### Post by repairman1946 on 2009-12-25
> **Gatorade said:**
> it should come up right away and you hit the down arrow to select which one to boot.

I'm not sure how it works if you install it to a separate HD, I've always done it on the same drive.

I was thinking of trying this method.

[http://www.youtube.com/watch?v=74Eyx4VDEWU]("http://www.youtube.com/watch?v=74Eyx4VDEWU")
I installed it to a separate drive, because the drive where windows is has no partition, and when I format "C" drive and install XP I don't get the choice to partition that drive.
And it doesn't come up at all.
The Grub folder is there where I installed Ubuntu.

---

### Post by ticthak@AOL.com on 2009-12-25
The install didn't put the GRUB list in the MBR (it should have overwritten the Windows menu)- if it did, the only problems I have run into have been glitches w/ the Windows boot, rather than the Linux). GRUB uses the grubconf menu.lst, GRUB2 (which I have still have frequent problems with) uses grub.cfg, which is not directly editable. Both are in the repos, and the man pages and tutorials are pretty good.

---

### Post by ticthak@AOL.com on 2009-12-25
I neglected to mention that gparted could have put your Ubuntu install on the Windows drive by safely resizing the Windows partition and creating a new one for the install (it should have been one of the options as you installed, but may only have been available through the "manual" option; the way you did it has certain advantages- you can pull the Linux drive and slap it into just about anything to use the OS, f'rinstance. Also, your Windows drive may not be as easily screwed by inadvertent actions. Are you sure your BIOS boot options are the way you want? If you have GRUB on the Linux drive only, selecting it in the BIOS as 1st HDD for booting will give you GRUB and any boot options you want to configure, selecting the Windows drive in the BIOS will only give you the Windows menu unless you expressly install(ed) GRUB there.

---

### Post by repairman1946 on 2009-12-26
> **ticthak@AOL.com said:**
> The install didn't put the GRUB list in the MBR (it should have overwritten the Windows menu)- if it did, the only problems I have run into have been glitches w/ the Windows boot, rather than the Linux). GRUB uses the grubconf menu.lst, GRUB2 (which I have still have frequent problems with) uses grub.cfg, which is not directly editable. Both are in the repos, and the man pages and tutorials are pretty good.

Hi [email]ticthak@AOL.com[/email]

What is MBR?
My GRUB uses grub.cfg
Where are the repos, and tutorials?

---

### Post by repairman1946 on 2009-12-26
> **ticthak@AOL.com said:**
> I neglected to mention that gparted could have put your Ubuntu install on the Windows drive by safely resizing the Windows partition and creating a new one for the install (it should have been one of the options as you installed, but may only have been available through the "manual" option; the way you did it has certain advantages- you can pull the Linux drive and slap it into just about anything to use the OS, f'rinstance. Also, your Windows drive may not be as easily screwed by inadvertent actions. Are you sure your BIOS boot options are the way you want? If you have GRUB on the Linux drive only, selecting it in the BIOS as 1st HDD for booting will give you GRUB and any boot options you want to configure, selecting the Windows drive in the BIOS will only give you the Windows menu unless you expressly install(ed) GRUB there.

Hi [email]ticthak@AOL.com[/email]

Where is the Windows drive? I didn't see that options during install. How would one find the "manual" option?
The BIOS is the way it was before the install. If select it in the BIOS as 1st HDD for booting, would I have to change the BIOS again for windows start?

---

### Post by ticthak@AOL.com on 2009-12-26
THE ONLY REASON I SAY "RTFM" TO SOMEONE IS I SAY IT TO MYSELF MANY TIMES EACH DAY

>>>What is MBR?
_MBR_ is tha _M_aster _B_oot _R_ecord, which is like firmware written to the beginning of whichever was the boot HDD at the time of OS install or formatting (editable, but not typically frequently edited), usually by the install or format scripts-it will include the partition table, which is what gparted or other partition tools edit. _BE VERY CAREFUL AND ATTENTIVE_ when working with the MBR, and nobody gets hurt. Those partitioning tools and gpart (and recording your partition table info) make it pretty straightforward even for us noobs, _IF YOU RTFM_ and focus on what the display tells you, much of this stuff is intuitively obvious, but only in hindsight...
>>>My GRUB uses grub.cfg
You have GRUB2, which wasn't the default boot manager for Ubuntu 9.04 originally, but is now (and is default for Koala.) You use "sudo mkconfig-grub" to edit the grub.cfg file and "sudo grub-update" to save this configuration. GRUB2 Wiki is [here]("http://grub.enbug.org/Manual")
>>>Where are the repos, and tutorials?
The repos (repositories) are the software libraries directly available from Ubuntu (see the Free Software line on your Appications menu?) or others (if you enable other libraries in Synaptic, thousands of .deb packages are available)- the tutorials are on the Ubuntu support pages and many other places (all over YouTube, of course, but lots of other places)
>>>Where is the Windows drive?
     That's indicated in your BIOS as 1st, 2nd, etc., whether IDE, SATA,etc.; your GRUB2 will see it as hdX or sdX (X is the drive#)and if it doesn't find it automatically, can be a headache, but as long as your BIOS finds it, the Ubuntu install will- you may only recognize it by its label or parameters, but unless your drives are the same size and model, you can figure out the difference.
>>>I didn't see that options during install. How would one find the "manual" option?
     I think it's step 2 of the Ubuntu install, it's a tick box the wording of which has changed somewhat with version but allows you to select the drive, partition, and file system type.
>>>The BIOS is the way it was before the install. If select it in the BIOS as 1st HDD for booting, would I have to change the BIOS again for windows start?
     Presumably, then, your Windows drive was your 1st HDD boot choice in BIOS and therefore GRUB2 has not correctly installed as the boot manager on that drive, you can leave the BIOS untouched and install GRUB2 (just the MBR part) there, or set your Linux drive as 1st, install GRUB2 there (definitely easier and less error-prone--RTFM!) Neither will require resetting the BIOS to boot your Windows partition, but GRUB2 will default boot Linux (after the timeout) as it will put that in the list first unless you expressly configure it otherwise (RTFM!)

---

### Post by repairman1946 on 2009-12-26
> **ticthak@AOL.com said:**
> THE ONLY REASON I SAY "RTFM" TO SOMEONE IS I SAY IT TO MYSELF MANY TIMES EACH DAY

>>>What is MBR?
_MBR_ is tha _M_aster _B_oot _R_ecord, which is like firmware written to the beginning of whichever was the boot HDD at the time of OS install or formatting (editable, but not typically frequently edited), usually by the install or format scripts-it will include the partition table, which is what gparted or other partition tools edit. _BE VERY CAREFUL AND ATTENTIVE_ when working with the MBR, and nobody gets hurt. Those partitioning tools and gpart (and recording your partition table info) make it pretty straightforward even for us noobs, _IF YOU RTFM_ and focus on what the display tells you, much of this stuff is intuitively obvious, but only in hindsight...
>>>My GRUB uses grub.cfg
You have GRUB2, which wasn't the default boot manager for Ubuntu 9.04 originally, but is now (and is default for Koala.) You use "sudo mkconfig-grub" to edit the grub.cfg file and "sudo grub-update" to save this configuration. GRUB2 Wiki is [here]("http://grub.enbug.org/Manual")
>>>Where are the repos, and tutorials?
The repos (repositories) are the software libraries directly available from Ubuntu (see the Free Software line on your Appications menu?) or others (if you enable other libraries in Synaptic, thousands of .deb packages are available)- the tutorials are on the Ubuntu support pages and many other places (all over YouTube, of course, but lots of other places)
>>>Where is the Windows drive?
     That's indicated in your BIOS as 1st, 2nd, etc., whether IDE, SATA,etc.; your GRUB2 will see it as hdX or sdX (X is the drive#)and if it doesn't find it automatically, can be a headache, but as long as your BIOS finds it, the Ubuntu install will- you may only recognize it by its label or parameters, but unless your drives are the same size and model, you can figure out the difference.
>>>I didn't see that options during install. How would one find the "manual" option?
     I think it's step 2 of the Ubuntu install, it's a tick box the wording of which has changed somewhat with version but allows you to select the drive, partition, and file system type.
>>>The BIOS is the way it was before the install. If select it in the BIOS as 1st HDD for booting, would I have to change the BIOS again for windows start?
     Presumably, then, your Windows drive was your 1st HDD boot choice in BIOS and therefore GRUB2 has not correctly installed as the boot manager on that drive, you can leave the BIOS untouched and install GRUB2 (just the MBR part) there, or set your Linux drive as 1st, install GRUB2 there (definitely easier and less error-prone--RTFM!) Neither will require resetting the BIOS to boot your Windows partition, but GRUB2 will default boot Linux (after the timeout) as it will put that in the list first unless you expressly configure it otherwise (RTFM!)


RTFM??

I was confused before, now I'm even more confused.

Maybe I should un-install and re-instal.

---

### Post by repairman1946 on 2009-12-27
[SIZE=3]Well I un-installed Ubuntu. Then rebooted my computer with the Ubuntu disc in the drive[/SIZE],[SIZE=3] and am now using Ubuntu. I am having difficulty importing my Firefox bookmarks. I looked in help under web browser bookmarks / Mozilla Firefox. Following the instruction listed I get a message "No program that contains bookmarks, history or password data could be found. I have hundreds of bookmarks in Firefox when I use windows.[/SIZE] [SIZE=3]How do I import my bookmarks?[/SIZE]

---

