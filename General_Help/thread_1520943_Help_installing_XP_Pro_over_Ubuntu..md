---
title: "Help installing XP Pro over Ubuntu."
date: 2010-06-30
forum: General Help
---

### Post by SkizzyMane on 2010-06-30
I just can't get it to work. I installed Ubuntu on the family PC, and my mom hates it with a passion and wants me to place XP back onto the PC.

I've tryed countless things, deleting all the partitions using GParted and setting them up for NTFS...NO HELP. 

I've tried adding a second partition and trying to install XP...NO HELP.

My issue is when say, I delete the partitions and set them for NTFS...I boot the XP Pro CD, and it gives me a blue " Windows is setting up " and after a short minute or two, it goes to a darker blue screen and displayes some error about my hardrives.

Any suggestions/help?

P.S. i've asked on other forums about this same issue, like... [http://www.ipodtouchfans.com/forums/showthread.php?p=2217891#post2217891](http://www.ipodtouchfans.com/forums/showthread.php?p=2217891#post2217891)

---

### Post by Smart Viking on 2010-06-30
It could be a faulty CD.

---

### Post by howefield on 2010-06-30
> **SkizzyMane said:**
> displayes some error about my hardrives.

This might be useful as opposed to the rest of your post, don't you think ?

---

### Post by Rubi1200 on 2010-06-30
If you want, you can also boot the Ubuntu CD and choose to try not install. Then click on the link at the bottom of my post and follow the instructions there. This information can help us get a better idea of what is going on.

---

### Post by ramnarayan on 2010-06-30
> **SkizzyMane said:**
> 


My issue is when say, I delete the partitions and set them for NTFS...I boot the XP Pro CD, and it gives me a blue " Windows is setting up " and after a short minute or two, it goes to a darker blue screen and displayes some error about my hardrives.

Any suggestions/help?

/showthread.php?p=2217891#post2217891[/URL]

1. What are the hard drive errors

2. Do you have a working version of wince expee, if you are not sure then install Virtual Box inside your existing Ubuntu and try and see if it installs from there.

3. Use a live Ubuntu CD and then the System -Administration - Disk Utilities - this some times shows errors in your hard drive which gparted may not

As the previous poster said be a bit more accurate with the errors it might be easier to help then.

---

### Post by SkizzyMane on 2010-06-30
The error is stop: 0x0000007B followed by some more zeros and random letters.

Now, I have ripped images of windows 2000 and another XP that I got on disc from ages ago. What can I use, within Ubuntu, to burn those images correctly?

And can you link me to a reliable Virtual Machine?

---

### Post by mocoloco on 2010-06-30
A common problem installing XP is when your system has a newer SATA hard drive but your XP disc is old and doesn't have SATA drivers.  If that's the case then options are finding a newer XP disc, or creating a slipstream XP install disc that includes the right drivers using something like [nLite]("http://www.nliteos.com/").

---

### Post by celldweller1591 on 2010-06-30
A driver issue may be caused by old hardware drivers !
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103) see this page for details .

---

### Post by wilee-nilee on 2010-06-30
Here is a link to a legit xp download it is the home version, you might download it and burn it to see if it loads like it will install, to confirm whether it is your cd that is faulty. You also have to have sata drivers with any XP install otherwise set the HD to ide. Also XP wont install to ntfs built by gparted. Use a XP cd to build the partitions.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Any oem key will activate this version, and maybe a regular key, it is just a slipstreamed sp3 ISO. You just have to have a legit key to be legal

---

### Post by SkizzyMane on 2010-06-30
What program, and settings, do I use to burn the images..?

---

### Post by szaboz on 2010-06-30
> **SkizzyMane said:**
> What program, and settings, do I use to burn the images..?


hi;


brasero will do it...

---

### Post by Seanlol on 2010-06-30
> **SkizzyMane said:**
> What program, and settings, do I use to burn the images..?

Ubuntu comes with "Brasero Disc Burner." You can use that. The settings are self explanatory.

EDIT: but if you're having to boot into Ubuntu via a Live CD, you'll need 2 CD/DVD drives in the computer.

---

### Post by davidmohammed on 2010-06-30
...

why go to all through all of this,

stick to ubuntu, just add the [XP theme]("http://ubuntu.online02.com/node/14") so that your mum thinks she is using XP!

---

### Post by wilee-nilee on 2010-06-30
> **SkizzyMane said:**
> What program, and settings, do I use to burn the images..?

If you have Ubuntu I like gnomebaker better than brasero as you can burn the image at a slower speed, in a windows environment if you right click on the ISO you can burn the image with the built in program. Gnomebaker is in synaptic, if brasero doesn't work for you.

---

### Post by mocoloco on 2010-07-02
> **davidmohammed said:**
> ...

why go to all through all of this,

stick to ubuntu, just add the [XP theme]("http://ubuntu.online02.com/node/14") so that your mum thinks she is using XP!

I would agree. Don't want you to get into trouble, but if she's only unhappy with how it looks, you can re-arrange things to look more familiar, like one panel on the bottom with the "Main menu" instead of the "menu bar".

Now if you're mom is missing certain Windows apps that's another story, and you'd have to find equivalents, run apps in Wine, or yes go back to Windows.

---

### Post by pricetech on 2010-07-02
I'd boot to the live CD and remove any and all partitions on the hard drive, then let XP make its own at install time.

---

### Post by SkizzyMane on 2010-07-02
She is missing certain apps, like iTunes for my little brother, and Zune Media Manager for her. What VM would you recommend?

---

### Post by Sarrus on 2010-07-02
Using a Boot-Up Floppy Disk, you should be able to use the Format Program (I think fdisk and / or format) to first clear the partitions and then format for NTFS or whatever..

---

### Post by Yvan300 on 2010-07-02
Virtualbox would work fine. How much RAM do you got?

---

### Post by SkizzyMane on 2010-07-03
I got 2.7 gigs of RAM. That should do for VM, correct?

---

### Post by davidmohammed on 2010-07-03
yes that is adequate - just give 1gb memory to the VM guest.  You can get zune to auto start - make sure  virtual box starts you guest in seamless mode (you can do this via a command line option) - Create a desktop icon that when launched starts your VM and automatically switches to seamless.

Seamless mode is a good way to make it look like that an XP application runs as if it was running on ubuntu - i.e. the application shares the same desktop and doesnt appear to run in a separate window.

As to your little brother - just show him Rhythmbox - it does the same as itunes and even connects to most ipods.

---

### Post by Yvan300 on 2010-07-04
Yeah, that's more than enough. I run my XP vm fine with only 1gb. Lucky you :D

---

