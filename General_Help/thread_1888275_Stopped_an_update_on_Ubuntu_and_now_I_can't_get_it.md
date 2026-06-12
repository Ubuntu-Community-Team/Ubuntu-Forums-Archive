---
title: "Stopped an update on Ubuntu and now I can't get it to load"
date: 2011-11-28
forum: General Help
---

### Post by Emilee on 2011-11-28
I need help! I was doing an update on Ubuntu and had to restart the computer... I went back to try and get on Ubuntu and it wouldn't load. It went to the sign in screen but wasn't all the way loaded. How do I get it back? Hoping it's an easy fix :(

---

### Post by mikewhatever on 2011-11-29
Hi, and welcome to the forums.

When at the login screen, hit ctrl+alt+f1. You should be presented with a black screen with the login prompt. Type your username and password to login. If that works, use the following commands to complete the update:

```
sudo apt-get install -f

sudo apt-get update

sudo apt-get dist-upgrade
```

To return to the login screen, hit ctrl+alt+f7.

---

### Post by Emilee on 2011-11-29
Hi,
It doesn't take me to the log in screen anymore. When I do press ctrl + alt + f1 it takes me to a black screen where it says to log in. I tried entering the codes there but no luck.

---

### Post by nothingspecial on 2011-11-29
No luck in what sense?

What happened when you entered the commands?

---

### Post by digithal on 2011-11-29
Login to tty1 (ctrl+alt+f1) and type:
```
sudo dpkg --configure -a
```
When everything is done, restart with **sudo reboot**.

---

### Post by Emilee on 2011-11-29
> **nothingspecial said:**
> No luck in what sense?

What happened when you entered the commands?
The commands just didn't help when I restarted and tried getting on Ubuntu

When I entered...
sudo apt-get install -f

This is what happened with this command
Reading package list... done
Building dependency tree
Reading state information... done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded 

Next command
sudo apt-get update

This is what I got
First it did a whole lot of downloading of many different things, it went so fast I couldn't really see what it all was.
Reading package done

Next command
sudo apt-get dist-upgrade

Same as the first command
Reading package list... done
Building dependency tree
Reading state information... done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Then I pressed ctrl + alt + f7 and nothing happened.

---

### Post by Emilee on 2011-11-29
> **digithal said:**
> Login to tty1 (ctrl+alt+f1) and type:
```
sudo dpkg --configure -a
```When everything is done, restart with **sudo reboot**.
When I entered that command, nothing happened. It didn't say anything. Then I did the sudo reboot and it rebooted my computer but the command didn't help.

---

### Post by Emilee on 2011-11-30
Bump

---

### Post by Scott Baker on 2011-11-30
It sounds as if you've tried the common fixes. Unfortunately you may not be able to fix it. I'm guessing that you killed the power to your machine before the update was finished. When that happens, you'll have packages that are only partially loaded. These packages can SIGNIFICANTLY effect the other packages and their operation within the OS. At this time, I could only recommend the following. Start with a fresh install of Ubuntu. I know it's extreme, but even if you do get your installation working, you may be likely to continue to have problems. Good luck with your problem. ](*,)

---

### Post by Emilee on 2011-12-09
Ugh, not something that I wanted to hear. :( How do I uninstall Ubuntu? It was put on my computer so that I can either choose to use Ubuntu or Windows.

---

### Post by oldtimer7777 on 2011-12-09
> **Emilee said:**
> Ugh, not something that I wanted to hear. :( How do I uninstall Ubuntu? It was put on my computer so that I can either choose to use Ubuntu or Windows.

Download Ubuntu from the Ubuntu web site. Create a installation disc and follow these instructions carefully, and make sure to read everything you are doing first:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Users hose their systems all the time beyond the point of simply repairing them from the command line.  That guide would have gotten you back in shape in less time than it took to try to help you with all of these other suggestions too. At least you tried everything else you could. Goodluck.

---

### Post by oldos2er on 2011-12-09
> **Emilee said:**
> Ugh, not something that I wanted to hear. :( How do I uninstall Ubuntu? It was put on my computer so that I can either choose to use Ubuntu or Windows.

Which version of Ubuntu are you using? And can you tell us your hardware specs please.

---

### Post by Scott Baker on 2011-12-10
WHOA!! Fresh new info here. You're now saying that you installed Ubuntu on a machine so that you can use BOTH Ubuntu and Windows (dual-boot,as it's known). This was info you should have provided when you first posted. It can make a HUGE difference in the way your problem is addressed. That said, how did you install you Ubuntu? Was it side by side with Windows, or within Windows in what is known as a WUBI installation (in a WUBI install, Ubuntu is installed like any other program that you would install in Windows). [-X

---

### Post by Emilee on 2011-12-13
It was installed on my computer from a family friend. He said it was dual-booted. Like once I start up the computer I have the option of choosing Ubuntu or Windows. I'm not sure how he installed it, all I know is that I can choose which one I wanted to go on. Sorry for not posting that info, I didn't know it would be that important.

---

### Post by JKyleOKC on 2011-12-13
When you power up the machine, and you get the menu for choosing between Ubuntu and Windows, does that menu have just the two choices, or does it have at least three? If it's just two, it's a WUBI install within Windows; if more than two, it's a true dual-boot installation. (This may not always be true, but it usually is and is a good first try at telling which is which.)

In either case you should be able to boot into Windows, although a true dual-boot setup may fail with cryptic messages about "grub" depending on just how badly damaged the Ubuntu side of things has become.

If it's a WUBI installation, you can remove it through the Windows control panel's add-remove programs utility, which will put the machine back into a purely Windows configuration. If you have the CD that your friend used to do the installation, you can put it into the drive, boot to the "Live CD" (automatically), and then re-install the WUBI setup. You will lose any files, pictures, music, and so on that were stored in the Ubuntu system by doing so, but it should not do any harm to the Windows side.

If it's true dual-boot and cannot boot into Windows, then you may need to do some more complicated repairs. However let's not get into that area unless it turns out we have to!

---

### Post by Scott Baker on 2011-12-13
Ok, new questions here. Do you want to continue trying to "dual-boot" with the windows? Would you rather try just Ubuntu? Do you want to go back to just windows? You need to decide, that way the proper answer can be provided. If you want to go with just Ubuntu, the process of installing and setting up is normally very easy. If you want to keep your windows, the process is more involved, as it requires changing things around on your hard drive (NOT TO BE ATTEMPTED BY SOMEONE THAT DOESN'T KNOW ***[COLOR=Red]EXACTLY[/COLOR]* **WHAT THEY'RE DOING !!) Also, as was requested previously, please provide your machines info (make, model, RAM, age if you have it.) One BIG sticking point with some installations is that wireless is sometimes problematic on certain models. Sharing your machine info will allow the rest of us to help guide you. (As a final thought, if you're not a hard core gamer that NEEDS windows based games, Ubuntu, and it's related software, should cover pretty much all of your normal computing needs.) \\:D/

---

### Post by Emilee on 2011-12-13
Here's what my start up screen says.

Top of the screen - GNU Grub version 1.99 - 12ubuntu5
Ubuntu, with Linux 3.0.0 - 13 Generic
Ubuntu, with Linux 3.0.0 - 13 Generic (recovery mode)
Memory test (memtest 86t)
Memory test (memtest 86t, serial console 115200)
Windows Vista


Make of my computer is Dell
Age I would say about 5-6 years old
RAM is 1.00 GB
The model I have is a Dimension C521

I would really like to have both Ubuntu and Windows. I need Windows because I have a few programs that I really need to keep. I like Ubuntu a lot better since it's so much faster then Windows on my computer. I'm sure you all know by now that I'm not too computer savvy, but thanks for being patient :)

---

### Post by MARP1961 on 2011-12-14
You can reinstall really easily once you get yourself an Ubuntu disk: [http://www.ubuntu.com/download/ubuntu/download. ]("http://www.ubuntu.com/download/ubuntu/download")

Download the file and burn the image to a disk (get someone with a working computer to do this). This disk is bootable. Simply make sure the computer is powered up **with the CD already inserted.** Now your computer will load the live Ubuntu demonstration. You will have a choice to TRY UBUNTU or INSTALL UBUNTU. Choose INSTALL.

The disk will check to see what's on your hard drive. You can let it install over the old (broken) Ubuntu, leaving the NTFS (Windows) partition untouched. The guide will take you through each stage. If you are unsure then just quit the install and check with us first.

If you really want to 'bite the bullet' then choose the 'Do Something Else' option and create separate partitions for your Ubuntu system ( / partition) and your data, settings and files (/Home partition). Doing this means that if you ever need to reinstall Ubuntu again then you can keep all your stuff untouched by choosing** not to format** the** /Home **partition.

In any event,** do not delete or format the Windows partition** **(keep NTFS)**. All Ubuntu partitions need to be **ext4 journaling file** **system**. The Ubuntu system needs at least **15GB of space (/ partition)** and if you decide on a Home Partition as well then give it as much space as you afford and the mount point will be **(/Home)**. There should also be a small **Swap** partition. This stays as it is. If this is all 'as clear as mud' then get back to me/us. Good luck!

---

### Post by MARP1961 on 2011-12-14
This may be simpler than I thought at first!

The CD for the latest version of Ubuntu (Oneiric Ocelot 11.10) also gives you the option of 'Upgrade Ubuntu'. Although I've not tried it, it looks like it will reinstall a broken Ubuntu system whilst preserving your data, files and installed software. If this is indeed the case, you can simply choose this option and not worry about partitions at all. 

Once Ubuntu is reinstalled, you should be able to boot Windows or Ubuntu as before.

---

### Post by MartijnNL on 2011-12-14
If the upgrade option MARP1961 mentions doesn't work, you might also want to consider inviting your family-friend over to do the re-installation. As Scott Baker says: working with partitions if you don't know what you're doing is very risky, if you want to keep your windows working.

---

### Post by Scott Baker on 2011-12-17
First thanks for providing info on your install and your machine. I hopefully will save you some further headaches here. First and foremost, it helps greatly to now know that you are running a Dell. If you go back to the forums home page, you'll find a whole section devoted to Dell machines. Dells ( and a few other select machines ) have some issues that HAVE to be addressed when installing Ubuntu on them. Common issues are normally related to sound, displays, and most importantly, WIRELESS connectivity. This is not saying that you can't or shouldn't run Ubuntu on your Dell. It just means you WILL have issues that have to be corrected on your machine. But, once set up, Ubuntu is a fantastic O/S to run on most machines. If your friend is available, and has some installation experience under his belt, you may want to have him do this install for you. While you don't need to be a computer engineer to correct the issues that turn up, it helps greatly if you have someone nearby that understands how to work from the terminal ( which will be necessary to correct the post install issues. ) Make sure to keep us up to date. Thanks, Scott
P.S. If it helps, it IS possible to run Ubuntu on a Dell. I'm currently running JUST 11.04 on a Dell M90 Precision, but it took a couple of LONG hours to get the wireless corrected. ](*,)

---

### Post by MARP1961 on 2011-12-17
Hang on a minute! 'Emilee' had Ubuntu running on her computer! I assume she had the wireless running OK. Her concern was reinstalling and keeping Windows. If she follows the advice given to reinstall, she can sort out any wireless problems later. Dells are not a problem. Wireless drivers can be sorted.

---

