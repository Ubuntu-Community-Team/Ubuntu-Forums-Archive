---
title: "Ubuntu 11.04 to 11.10  What the &quot;H&quot; happened to the interface"
date: 2012-09-08
forum: General Help
---

### Post by Engineeringtech on 2012-09-08
Ok, I will start this by saying I am not really interested in HOW Unbuntu works, just in using it.    I have used one version of Ubuntu or another since 8.X.  and I like it.  WHEN it is working.  All the highly technical discussions of how "superior" Linux is, will be meaningless to me unless I can get it working.

A couple years ago, I had a triple boot system I had setup myself, with DO S 6.22, Windows XP SP2, and Ubuntu 9.?, using the Windows boot manager.    Sorry, but I still NEED those other OS's.  I partitioned the drive, installed the OS's in sequence, and everything worked fine.    That is until Linux started hounding me  with popup messages to upgrade.   So I used the update manager to get  to 10..4?  The result of that upgrade was that it broke my triple boot, and no one could figure out how to fix it.   And the machine never shutdown again.  I did fresh installs, and fought with it for months, until one day, I finally got the triple boot working with GRUB, but never got the shutdown working.  I could live with that.

Then about a year ago, I was again hounded by  popup messages, and reluctantly  allowed the update manager to update to 11.04.  This time, it completely broke access to my data, Windows, and DOS partitions.   Yes, I could use Linux and get online.  And my drive partitions were still visible from GPARTED, but they could not be mounted.  Two local Linux experts couldn't figure it out.

Hounded by more popup messages, this morning I decided to update to 11.10.  I may be stupid, but I hoped that the upgrade might recover my partitions and triple boot.  Everything installed smoothly...   On reboot, I was presented with a wierd screen with a few large icons on the left.   None of the programs I hqe installed are represented.   I still have no drive icons or means of mounting my data partitions.  I absolutely HATE the look and feel of the thing, and can't see any reason why it would be better.  It takes up too much of my small monitor's desktop.   

I decided to come back to the computer later to see if anything could be done to revert to the classic interface.  So where is the shutdown?   WHERE IS THE SHUTDOWN?  WHERE IS THE SHUTDOWN?  20 minutes later, I STILL had not found out how to SHUTDOWN the thing!    I couldn't even find a HELP menu!    I FINALLY figured out that I could logout, and THEN shutdown.   (Of course the shutdown STILL doesn't work, but at least it brings me to a point where I can mash the power button.  )

I can't understand why the people who design these upgrades would want to make it so hard for new people to  figure out how to do simple tasks, like shutdown the machine.  How does that promote the OS?

---

### Post by cryptotheslow on 2012-09-08
There should be a Shutdown option on the menu that appears if you click the computer icon in the top-right corner.

As for finding your installed applications, click on the top icon on the launcher bar on the left to open the dash - start typing the name of the application and it should appear in the pane below the search box to be clicked on.

The old interface was Gnome2 based. The Gnome project decided to cease work on that and moved onto Gnome 3 - on top of which Canonical built the Unity desktop you now see in front of you. This may help you get your bearings: [https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html](https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html)

If you prefer the more traditional Gnome 2 style of desktop you could install any of the following DEs: MATE, Cinnamon, LXDE, XFCE.

Your shutdown issue sounds like an ACPI issue - is it an older motherboard?

---

### Post by tartalo on 2012-09-08
> **cryptotheslow said:**
> If you prefer the more traditional Gnome 2 style of desktop you could install any of the following DEs: MATE, Cinnamon, LXDE, XFCE.

KDE is another popular choice.

---

### Post by mastablasta on 2012-09-08
for shutdown you can probably go to dash and then type in shutdown and it will give you the shutdown... also i think it's in the top right corner.

anyway if you don't like the interface try Xubuntu or Kubuntu (windows like) instead. if you want to stay with gnome then you can go with Gnome fallback session or Cinnamon or Mate (fork of old gnome) desktops. also it was Gnome that decided firts to drasically chaneg the interface and have large icons and such. you can check how they did it if you install gnome shell. Unity is an attempt to make it easier for users.


as for the booting and file issues it is dificutl to help not knowing how your tripple boot is setup ( i am guessing something is wrong in the setup) and also how the disk is parittioned. perhaps to get better help try runnign from live CD/USB and run the bootinfo script(can also be found in boot repair tool): [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

then post results here in code (#) tags so it's easier to read.

and i suggets you go with version 12.04 since it is an LTS with 5 year support so you don't have to upgrade for 5 years (select to only upgrade LTS editions in the upgrade manager) and you will receive all security updates and some bug fixes. additionally it is slightly more polished than 11.10.

if you want to stay with Unity interface you can check the manual in my link. it has a very easy explanation of most things you might need to know.

---

### Post by Engineeringtech on 2012-09-08
> **cryptotheslow said:**
> There should be a Shutdown option on the menu that appears if you click the computer icon in the top-right corner.

As for finding your installed applications, click on the top icon on the launcher bar on the left to open the dash - start typing the name of the application and it should appear in the pane below the search box to be clicked on.

The old interface was Gnome2 based. The Gnome project decided to cease work on that and moved onto Gnome 3 - on top of which Canonical built the Unity desktop you now see in front of you. This may help you get your bearings: [https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html](https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html)

If you prefer the more traditional Gnome 2 style of desktop you could install any of the following DEs: MATE, Cinnamon, LXDE, XFCE.

Your shutdown issue sounds like an ACPI issue - is it an older motherboard?

Thanks for your reply.  There is NO shutdown option in the top right corner.  What is a DEs?   The motherboard is a Gigabyte GA-EP45-UD3P, which I purchased in 2009.  I had problems with the PCIe slots, and got it replaced.  The replacement has the latest BIOS update.  What exactly does one do to fix an ACPI issue?

---

### Post by cryptotheslow on 2012-09-08
Is there even a little computer icon up in the top right corner?

DE = Desktop Environment. It's the graphical interface you use. You can install alternative ones on Ubuntu and use them - they each bring a different look and feel.

This is what the XFCE DE looks like: [http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)
This is what the LXDE DE looks like: [http://lxde.org/image_galleries/screenshots](http://lxde.org/image_galleries/screenshots)

As for shutting down, what happens if you open a Terminal and enter this:
```
sudo shutdown -P now
```

**CAUTION - that will either halt or shutdown the machine so make sure you've saved your work first :)

---

### Post by Engineeringtech on 2012-09-10
> **cryptotheslow said:**
> Is there even a little computer icon up in the top right corner?

DE = Desktop Environment. It's the graphical interface you use. You can install alternative ones on Ubuntu and use them - they each bring a different look and feel.

This is what the XFCE DE looks like: [http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)
This is what the LXDE DE looks like: [http://lxde.org/image_galleries/screenshots](http://lxde.org/image_galleries/screenshots)

As for shutting down, what happens if you open a Terminal and enter this:
```
sudo shutdown -P now
```**CAUTION - that will either halt or shutdown the machine so make sure you've saved your work first :)

Sorry for the delay in answering people.  I've been having internet access problems.  

There is no little computer icon in the top right corner.    Up until late last night, the icon to the extreme upper right of the screen was a human head with my Logon ID.   None of the  pulldown menus contained an option for shutdown.   Nor could I find a place to pull up a terminal and enter "sudo shutdown".    However late last night, I discovered by changing the desktop theme from "High Contrast" to "Ambiance", I got an additional icon in the upper right, which looks like a gear.   That has a pulldown with a "shutdown" selection.   Why would the installation program default to a display that omits such an important pulldown menu?  That has got to be a bug!

Of course, just because I have a shutdown selection doesn't mean the thing will actually shutdown.  That hasn't been the case since I upgraded from 9.0? to 10.??.   The hardware never turns off,  but at least I can manually force a shutdown with the power button without corrupting the hard drive.   I think someone above suggested I check ACPI settings in the BIOS.   What do I look for?

I looked at the links you gave me.  Neither was quite like the desktop I got used to in Ubuntu 11.04.     Can you tell me what desktop environment I can install which would have the same pulldown menus as 11.04?   And how do I install a DE?   I can't even find help menus.......   The new desktop looks like a funky tablet computer.   

Does anyone have any idea on what I can do to see my drive partitions, which have been missing in action since upgrading to 11.04 last year?    Why can't I see my FAT, FAT32, and NTFS data partitions?    

Sorry I have so many questions.  It's just that nothing seems to ever work the way it is supposed to.

---

### Post by Engineeringtech on 2012-09-10
> **mastablasta said:**
> for shutdown you can probably go to dash and then type in shutdown and it will give you the shutdown... also i think it's in the top right corner..............
as for the booting and file issues it is dificult to help not knowing how your triple boot is setup ( i am guessing something is wrong in the setup) and also how the disk is parittioned. perhaps to get better help try runnign from live CD/USB and run the bootinfo script(can also be found in boot repair tool): [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) then post results here in code (#) tags so it's easier to read.

and i suggests you go with version 12.04 since it is an LTS with 5 year support so you don't have to upgrade for 5 years (select to only upgrade LTS editions in the upgrade manager) and you will receive all security updates and some bug fixes. additionally it is slightly more polished than 11.10.

if you want to stay with Unity interface you can check the manual in my link. it has a very easy explanation of most things you might need to know.

Thanks for the advice. on LTS versions and shutdown.

As for the triple boot, there was nothing wrong with it, until Ubuntu switched from Grub to Grub2.    It didn't just stop booting DOS and Windows.  It wouldn't run Ubuntu either.   I worked with other people in this forum and a local Linux expert for almost 12 MONTHS, trying to solve the problems.    I ran boot scripts and all sorts of utilities and diagnostics AD NAUSEUM for people but apparently they didn't lead to any conclusions.  I also did DOZENS AND DOZENS of repartitions, reformats, and reinstallations of my three OS's just to satisfy people that I hadn't made some stupid mistake.  But the highly touted Grub2 never detected my other OS installations, or got me to a Ubuntu DESKTOP!      I even replaced my motherboard, hard drive controller, and hard drive!    All during this time, I had no other computer to use, and believe me, I got sick of seeing a black screen with a flashing question mark.   I finally had the idea to boot from an ubuntu  installation disk and run Boot Repair.   I don't know what it corrected, but my machine worked for a few months more.     I had a working triple boot and my FAT and NTFS partitions were visible from Ubuntu's desktop.  Then another major Ubuntu upgrade, and no more partitions!  This time I don't even have access to EITHER OF MY brand new DVD writers!     Even Boot Repair couldn't fix that.  

Only reason I am telling you all this, is because at this point although I'd LIKE access to my long lost data partitions, and my still unused DVD writers, I'm NOT going to start from scratch AGAIN.   If I decide to post another boot info script, I don't want someone to just tell me I have to start from scratch.   Starting from scratch has gotten me no where.  I'll either fix what I have or keep using a crippled machine.

---

### Post by Cheesemill on 2012-09-11
I think that Ubuntu just might not be the most suitable distribution for you.

Ubuntu has always released a new version every 6 months, putting more emphasis on having the latest versions of software rather than reliability.

Compare this to Debian (on which Ubuntu is based), which only releases a new version when they think that it's ready, and only once it has been thoroughly tested. Because of these reasons Debian usually only make a new release every few years.

You may want to sit down and make a list of exactly what is important to you in an OS and try to make an informed decision about which distribution would fit your needs best, Ubuntu is not the best solution for everyone (for example I've switched to Arch on my personal workstation because I was getting tired of upgrading every 6 months, now I never need to upgrade at all).

---

### Post by Engineeringtech on 2012-09-13
> **Cheesemill said:**
> ..................

You may want to sit down and make a list of exactly what is important to you in an OS and try to make an informed decision about which distribution would fit your needs best, Ubuntu is not the best solution for everyone (for example I've switched to Arch on my personal workstation because I was getting tired of upgrading every 6 months, now I never need to upgrade at all).

That sounds like good advice.  I've been pulled every which way by Ubuntu, and it's time I found an OS that worked for me, rather than the other way around.

---

### Post by 2F4U on 2012-09-14
If you are looking for something that is really stable and has the old interface of Ubuntu 10.04 (Gnome2) that you might want to look at CentOS or Scientific Linux:

[https://www.centos.org/](https://www.centos.org/)
[https://www.scientificlinux.org/](https://www.scientificlinux.org/)

Support for the current verion of Scientific Linux ends in 2020, so you can expect to run the same GUI interface for a very long time, but still get security updates and bug fixes.

[https://www.scientificlinux.org/distributions/](https://www.scientificlinux.org/distributions/)

---

### Post by vasa1 on 2012-09-14
> **Cheesemill said:**
> ...

Ubuntu has always released a new version every 6 months, putting more emphasis on having the latest versions of software rather than reliability.
...
That bad?
I started off with 11.04 and have reached 12.04 without data loss. Yes, with the change from 11.04 to 11.10, some configuration options vanished but that got me interested in understanding how to tweak themes directly.

---

### Post by Engineeringtech on 2012-10-02
> **2F4U said:**
> If you are looking for something that is really stable and has the old interface of Ubuntu 10.04 (Gnome2) that you might want to look at CentOS or Scientific Linux:

[https://www.centos.org/](https://www.centos.org/)
[https://www.scientificlinux.org/](https://www.scientificlinux.org/)

Support for the current verion of Scientific Linux ends in 2020, so you can expect to run the same GUI interface for a very long time, but still get security updates and bug fixes.

[https://www.scientificlinux.org/distributions/](https://www.scientificlinux.org/distributions/)


Thanks.  I will check these out.  

I just can't deal with the constant change to the interface every time Ubuntu asks me to upgrade.   (They're counter intuitive, and I'm missing important stuff like administrative tools, system tools, etc.)     And remember, I lost access to all my partitions during the update.   I'm not just talking about missing drive icons.  I have no pulldown menus with partitions either.     (No one here offered to tell me how to recover them.)    Some of us feel that a computer should actually offer something other than access to the internet.  Which is all I have now.

---

