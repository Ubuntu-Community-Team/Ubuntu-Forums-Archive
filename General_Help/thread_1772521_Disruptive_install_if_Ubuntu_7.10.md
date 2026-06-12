---
title: "Disruptive install if Ubuntu 7.10"
date: 2011-05-31
forum: General Help
---

### Post by E-Tramp on 2011-05-31
:confused:Yesterday I installed Ubuntu 7.10 on my already existant Windows XP harddrive.  My system is backed up with a PowerQuest Drive Image Special Edition, and when I installed the Linux operating system I tried at first to install manually but kept getting a message on the screen saying something like the partitions I was trying to put them on weren't designated as a root file system point or something of that nature.  It instructed me to change the partition with the partition menu.  I right clicked on the partition I wanted to install on and no matter what I used in the menu to try and designate it for the Ubuntu operating system it wouldn't accept it and proceed to the next step.

I then decided to take a chance and try to use the guided installation which gave me absolutely no control over where the program was installed.  Unfortunately it did just what I thought it would, it installed the Ubuntu program between the backup drive, and the windows operating system, AND it installed the swap file inside my backup drive, which is an extended drive to the main drive, effectively disabling my backup drive just by being where it is installed at.  PowerQuest DISE requires that the backup drive be installed immediately following and ajoined too the main drive partition.  Basically, this means that the Ubuntu programming must be installed  at the front of the disk, immediately followed by the swap file, then that followed by the main windows harddrive, followed by the extended backup drive, or on two of the partitions on my secondary drive, which is what I was trying to do with the manual setup. 

I have to be able to designate where my Linux programming is being installed exactly to keep my other systems operating properly and that means manual installation.

How do I get the program to install where I want it to not in a random fashion that will adversely effect my windows system?  As it stands right now, I can re-install my windows system and the back up software, and put the original backup files back into the backup drive and rewrite it back to where it was before the installation, but it will be a lot of work and if I want to reinstall Ubuntu after that I need to know how to do it manually and get it where I need it to be, not whereever it ends up.

How do I make a manual install, and will that allow me to install wherever I choose?

Finally, I have tried to find dialup modem drivers for this Linux install but, am not having much luck, where is there a site that has a freeware Linux modem driver that will do the job for me?  Mine is a generic V92, internal modem, but, I can do without the V92 capability if necessary.  Probably any generic modem Driver would do for now, though I would prefer a functioning V92 install and software to use it.  Thanks for any help you can give me here.

---

### Post by snowpine on 2011-05-31
Welcome to the forums! Ubuntu 7.10 is completely unsupported since 2009, you need to download and install a supported version such as the current 11.04 or the Long Term Support 10.04.

Second, you need to choose the Manual Partition option and then you'll have complete control over the partition scheme. I personally never trust "guided partition" options because I am a control freak. :)

Third, Ubuntu can be installed in several ways, it does not necessarily need a dedicated partition(s). You may find these alternate methods of interest:

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by newbymick on 2011-05-31
> **snowpine said:**
> you need to download and install a supported version such as the current 11.04  

 OH NO YOU DON'T - so many have tried and so many have failed :(


> **snowpine said:**
>  or the Long Term Support 10.04. OH YES YOU DO

Sorry - can't help with the dial-up modem thing.  Thought dial-up died a long time ago (except for a few hick areas of the USA) and was once told that Linux didn't really want to play with dial-up in the early days (sic).  You would better off with a 3 stick (almost plug and play - just takes a bit googling to configure.  If I can do it - so can you)

---

### Post by E-Tramp on 2011-06-01
:(Actually I got this program 2 years ago, and was afraid to install it, but, recently ordered a couple of disks, one of Version 11 point something I think, and a recent version of Fedora, one of which I plan to use on a new computer build, and it got me started on the 7.10 again.  Unfortunately it went just the way I was afraid it would.  So is there any information I need to know for a manual install?  This version wouldn't get past about the 5th frame of the manual install because it wanted me to designate the partition for a root installation and I don't have any idea what that means.  Nothing I tried with the menu would urge it on past, and I tried everything the menu had on it, so there is something that I couldn't reason out that it wanted.

As for the dialup, you are right, it is pretty dead,(do I count as a hick? I live 10 miles from any town or city, and some connection types are not available to me here. Don't really know what is.). and the providers are beginning to let their maintanance slip, because I have had several incidents recently of not being able to log on to my server.  However, for now that is what I have to work with, and it will have to do until my budgetary restrictions are loosened up.  I am moving to Linux because I just don't want to spend 3 or 4 hundred dollars every three years for a new operating system that is moving more and more toward protecting software writers, rather than taking care of the people who are making Microsoft rich like me.  I just need a dialup modem to get these systems worked out for now, and I know they are there, and I will buy one if I have to, but, I would rather get a freebie for temporary, till I do move to a high speed connection.  I will check on the 3 stick, whatever that is, and maybe I will just have to buy a dialup program if there is no free ware available.  Hate to spend the money when I am soon to move up to something better.  Some of us are just die hards when it comes to spending money.

I should be getting the new disks next week, so, will see what you have to say after that.  I do have to solve this problem with my old windows program, and XP will probably be the last windows program I buy.  I suspect it will be looked back on with regret by many of the folks who continue to buy windows.

Another question I have is if I write over the current installation of 7.10 will the grub code go with it?  I won't be getting the  selection menu on boot will I?  that would be really a problem.

---

### Post by jocko on 2011-06-01
> **E-Tramp said:**
> So is there any information I need to know for a manual install?  This version wouldn't get past about the 5th frame of the manual install because it wanted me to designate the partition for a root installation and I don't have any idea what that means.  Nothing I tried with the menu would urge it on past, and I tried everything the menu had on it, so there is something that I couldn't reason out that it wanted.

The file system root is "/", so you have to assign the mount point for the partition to "/" (without the quotes).
But if I were you I would wait for the 11.04 cd to arrive. 7.10 is not supported anymore. The official software repositories are closed, so you will end up having to manually switch the package manager to use other sources.

It was several years ago I tried using dialup, but when I did I had no serious problems. The restricted hardware manager suggested a software modem driver which I installed, and then I could set up a dialup connection (but I had to google a bit to find out how...).
Of course it probably depends on what modem you have. 

> **E-Tramp said:**
> 
Another question I have is if I write over the current installation of 7.10 will the grub code go with it?  I won't be getting the  selection menu on boot will I?  that would be really a problem.
Not sure if I read this question correctly...

Do you mean that you have a current install of 7.10 (I thought the install failed long before grub was installed, which is why I think I may have misread your question), and you are worried that you will loose grub if you delete it?
In that case the answer is yes. Deleting the ubuntu partition will delete the grub directory, leaving you without a functional boot loader, so not even windows will boot (unless you reinstall the windows boot loader).

Or do you mean "If I install ubuntu, will I get grub and a grub boot menu?" Then the answer is also yes. Installing ubuntu will always install grub (unless you yourself tell it not to), and if you do it on a computer that already has windows installed, you will automatically get a boot menu.

---

### Post by E-Tramp on 2011-06-01
No, the Ubuntu install failed in the manual mode and I decided to try installing it using the guided mode, and it installed in a working fashion but, between my backup drive and my main Windows program disabling my backup drive.  I can delete the division in my backup drive partition and restore it to the original size, then replace the original backup files, and run the backup program and it will install the previous size harddrive right over the ubuntu install I think, if I delete the partition.  The question arises from the fact that the grub code is before either system boots up, does it disable the whole system then, when I delete the partition that Ubuntu is installed on, and once I reinstall the windows operating system over it, does that restore the original boot code?

---

### Post by mcduck on 2011-06-01
Yes, removing Ubuntu partition will break Grub, and so does making a fresh Widnows install.

The solution is simple, though. Boot into windows and reinstall it's boot loader before you remove Ubuntu partitions.

Both bootloaders can be installed from a working system Grub from any running Linux system and Windows bootloader from any running Windows system. In addition Grub can be installed from any Ubuntu live-CD, and the Windows install CD should also be capable of recovering the Windows bootloader.

There's also tools like Super Grub2 CD and Ultimate Boot CD which allow repairing and installing different boot loaders in case you don't have appropriate OS CD at hand.

I also agree with others that you should go for a more up-to-date Ubuntu release, 7.10 will be of very limited use to anybody, it's unsupported and it's software repositories have been closed down. I'd personally recommend trying 11.04 first,and only if you happen to be unlucky and it doesn't work for you, then 10.10 or 10.04 LTS. And the correct mount point for the root partition is "/". :)

---

### Post by E-Tramp on 2011-06-01
So, your saying that I should have probably bought a disk for 10.04, because the 11.04 has had problems on dual installation platforms, making it less reliable on installation? 10.04 is the tried and tested program?

Also, I really should be able to install the whole program and restore my system to preinsallation state, because I rewrote my backup drive just before I tried the installation in case I had to get rid of the installation.  As long as the installation didn't also disable the backup drive loader.  I won't know that for sure until I delete the Ubuntu partition and attempt a rewrite of the harddrive.

In the meantime, I really have never tried to re-install just the boot loader, and am not sure what that would entail, unless it would require using a function from the installation disk/repair disk.  What can you tell me about the process.  I know your expertise isn't really in windows operating systems, but, I am sure this question has come up a time or two.

---

### Post by mcduck on 2011-06-01
Actually I'm recommending trying the latest version, 11.04, first. It should work just fine for you, just like it works for most users.

_Every_ time a new Ubuntu version is released, the Internet fills with people complaining about it and recommending some older release instead to everybody. Then goes 6 months, and a new release is made, and suddenly the previously "unusable and horrible" version becomes the one that is recommended instead of the new one. It's been lie that at least as long as I've been using Ubuntu, since 5.04, so I pretty much already expect the same thing after every new release. :D In some cases older version might indeed work better, but most of the time such recommendations are either result from peoples own problems (pretty much hardware-specific stuff) or their dislike for some change in the latest version.

I always recommend at least trying the latest version first. Any reasons why it wouldn't work would be hardware-specific, and therefore trying it is the only way to see if it works or not on your computer. Nobody else can tell you that, unless they have *exactly* the same hardware as you.

(and no, 11.04 has no problems with dual-boot setups. :))

edit: I don't know the command for installing the windows bootloader in Vista/7, but at least in XP it was "fixmbr". And the repair install option from the install disk should also do the trick.

For Grub and Grub2 this guide should cover pretty much everything (don't be fooled by the long guide, it's actually just a couple commands you run, the guide really just covers things in pretty detailed way :)): [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by linuxinstalledfromhdd on 2011-06-01
Sure, but there are many more write ups to fix issues for older versions, naturally. The longer they have been around, the more users have posted instructions on how to fix them, thereby making it easier for the novice Ubuntu user to resolve them quickly and easily.  Didn't they change Grub in the latest version of Natty? 

If you want to help develop the latest version of Ubuntu when it is released, fine.  I'm really happy with 10.10 at the moment. 

> **mcduck said:**
> Actually I'm recommending trying the latest version, 11.04, first. It should work just fine for you, just like it works for most users.

_Every_ time a new Ubuntu version is released, the Internet fills with people complaining about it and recommending some older release instead to everybody. Then goes 6 months, and a new release is made, and suddenly the previously "unusable and horrible" version becomes the one that is recommended instead of the new one. It's been lie that at least as long as I've been using Ubuntu, since 5.04, so I pretty much already expect the same thing after every new release. :D In some cases older version might indeed work better, but most of the time such recommendations are either result from peoples own problems (pretty much hardware-specific stuff) or their dislike for some change in the latest version.

I always recommend at least trying the latest version first. Any reasons why it wouldn't work would be hardware-specific, and therefore trying it is the only way to see if it works or not on your computer. Nobody else can tell you that, unless they have *exactly* the same hardware as you.

(and no, 11.04 has no problems with dual-boot setups. :))

edit: I don't know the command for installing the windows bootloader in Vista/7, but at least in XP it was "fixmbr". And the repair install option from the install disk should also do the trick.

For Grub and Grub2 this guide should cover pretty much everything (don't be fooled by the long guide, it's actually just a couple commands you run, the guide really just covers things in pretty detailed way :)): [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by E-Tramp on 2011-06-02
OK, I don't have 7 or Vista, so this will do.  I will re construct my programming next week and see if I can reinstall 11.4.  I got the disks today.  Will be in touch if I need anymore help.

---

### Post by mcduck on 2011-06-03
> **linuxinstalledfromhdd said:**
> Sure, but there are many more write ups to fix issues for older versions, naturally. The longer they have been around, the more users have posted instructions on how to fix them, thereby making it easier for the novice Ubuntu user to resolve them quickly and easily.  Didn't they change Grub in the latest version of Natty? 

If you want to help develop the latest version of Ubuntu when it is released, fine.  I'm really happy with 10.10 at the moment.

True, but on the other hand all the new versions of all the packages that come with a new distribution release will also bring loads of bug fixes and support for new hardware etc. And often those are the kind of fixes that can't even be added into old release.

So many of the bugs you might have to fix manually in older Ubuntu version would already be fixed by developers in the new version.

...of course new stuff always tends to bring new bugs, but if any of them occur on your computer or not, that's something everybody has to try themselves.

---

### Post by Bartender on 2011-06-04
I'm on dial-up.  Have been for years.  Wish I wasn't but that's the way things are.

I'd recommend sticking with the LTS releases just because it's a major hassle to get everything back the way you wanted it unless you have broadband.

I'm still running 9.04 on our main desktop PC because I don't want to go thru the ordeal.  Sooner or later we'll upgrade, but I'm beginning to think about installing a newer version of Ubuntu to a different PC, getting it close to where we need it to be, then swapping out PC's.

I'm considering bringing pizza & beer with me to someone's house with broadband, and updating the new Ubuntu PC as much as possible on their connection.  Then take it home.

---

### Post by mcduck on 2011-06-04
> **Bartender said:**
> I'm on dial-up.  Have been for years.  Wish I wasn't but that's the way things are.

I'd recommend sticking with the LTS releases just because it's a major hassle to get everything back the way you wanted it unless you have broadband.

I'm still running 9.04 on our main desktop PC because I don't want to go thru the ordeal.  Sooner or later we'll upgrade, but I'm beginning to think about installing a newer version of Ubuntu to a different PC, getting it close to where we need it to be, then swapping out PC's.

I'm considering bringing pizza & beer with me to someone's house with broadband, and updating the new Ubuntu PC as much as possible on their connection.  Then take it home.

You could also set your computer to dualboot between two Ubuntu versions. That way you'd always have the old install available while trying the new version on another partition.

Just add a separate storage partition so you can access your files from both installs, and you'll have a safe setup for upgrades. (you might not want to use a shared home, just to keep the setting files from each version separate from each other, so separate storage is instead a better idea.)

---

