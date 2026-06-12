---
title: "Routine update overwrites MBR"
date: 2011-11-08
forum: General Help
---

### Post by Rebelli0us on 2011-11-08
Update Manager did its usual thing, and in the process it destroyed the Windows MBR on the one and only hard disk on the system.

Windows was dual-booting Ubuntu through boot.ini, this Ubuntu installation was NOT self-booting by design.

There was a prompt from Update Manager, some techno-gibberish about grub, but at no time should a software update overwrite the MBR. 

Fix the code please!

---

### Post by dcstar on 2011-11-09
> **Rebelli0us said:**
> Update Manager did its usual thing, and in the process it destroyed the Windows MBR on the one and only hard disk on the system.

Windows was dual-booting Ubuntu through boot.ini, this Ubuntu installation was NOT self-booting by design.

There was a prompt from Update Manager, some techno-gibberish about grub, but at no time should a software update overwrite the MBR. 

Fix the code please!

Complaining here does **nothing** whatsoever to make any changes to packages.

If you want to lodge a bug saying that even though you were given choices you made the wrong one then use the existing systems for doing such things.

---

### Post by mcduck on 2011-11-09
> **Rebelli0us said:**
> 
There was a prompt from Update Manager, some techno-gibberish about grub, but at no time should a software update overwrite the MBR. 

Actually yes, it should, if it specifically asks you if you wish to do so and you say yes. :)

---

### Post by Fred Doolie on 2011-11-09
> **Rebelli0us said:**
> There was a prompt from Update Manager, some techno-gibberish about grub

Correct. It asked you "Do you wish to install grub" and you told it "yes". So it did. Just like you told it to.
 
Well the Windows MBR can be put back VERY easily.  

Google "restore windows mbr ubuntu". You can use just about ANY live Linux CD to do it. I like Puppy myself. It's a GREAT rescue CD!

I've overwritten my windows MBR on both my systems zillions of times and fixed it zillions of times. 
*Kisses my Puppy Linux CD*

"ms-sys -mf /dev/sda" is the command; assuming your Win drive is SDA.

---

### Post by Rebelli0us on 2011-11-09
> **dcstar said:**
> Complaining here does **nothing** whatsoever to make any changes to packages.

If you want to lodge a bug saying that even though you were given choices you made the wrong one then use the existing systems for doing such things.

Thank you. I'm hoping that the devs read or receive input through the forums. It's not really a bug, it's a bad UI, it inflicts all this techno-gibberish on average users

---

### Post by mcduck on 2011-11-09
It's very rare to see any developers around these forums. If you want to bring something to their attention you'll really have to file a bug report through [Launchpad]("https://launchpad.net/ubuntu").

---

### Post by oldfred on 2011-11-09
Grub knows where to reinstall, but you can make it forget. I would think you had to install it somewhere to create the boot image and that is what it remembered.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Another user posted this:
> I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep 'stage1' install in sync.


---

### Post by Mark Phelps on 2011-11-09
Word of advice in the Linux world -- do NOT ignore warning messages.  What you so glibly call "techno-gibberish" is often the only way that you can be warned about potential damage.

If you see a message and don't understand it, then EXIT from the change, come here with a question, and we can help you avoid the very problem that happened.

---

### Post by Rebelli0us on 2011-11-10
> **Mark Phelps said:**
> Word of advice in the Linux world -- do NOT ignore warning messages.  What you so glibly call "techno-gibberish" is often the only way that you can be warned about potential damage.

If you see a message and don't understand it, then EXIT from the change, come here with a question, and we can help you avoid the very problem that happened.

Thank you. It was not a warning, only a combo box with several meaningless choices. The average user does not even know what grub is nor should they care. The choices also meant nothing to me as windows developer. Updates should run unattended, and "glib" as those who ignore 99% of pc users.

---

### Post by Mark Phelps on 2011-11-10
Sorry if I came across a bit harsh. I misunderstood what you said.

And basically, you're right -- updates should be configured in such a way that any possible "damage" to the system is clearly indicated and the user is allowed to opt-out of the update.

Not going to get an arguement from me about that.

---

### Post by Fred Doolie on 2011-11-11
>The average user does not even know what grub is nor should they care.

Linux is *NOT FOR* the "average user". It is for people who want to know how the system works, want to customise it and want as much "Techo-babble" as possible. It's like Legos. The "average user" buys a toy car. The Linux User buys a box of Lego car parts and build their own cars. 

>The choices also meant nothing to me as windows developer. 

So you just ignored them and chose "yes". Then were SHOCKED when it did EXACTLY what you told it to do.

> Updates should run unattended, and "glib" as those who ignore 99% of pc users. 

Not Linux updates. They are for people who WANT to know what's going on every step of the way and have a hand in/choices in the process. 

So put back your Windows MBR. Super simple. Use either EasyBCD in Windows or the ms-sys command in Linux. It will take you 10 seconds to fix it. Ten seconds!

---

### Post by Rebelli0us on 2011-11-12
> **Fred Doolie said:**
> >The average user does not even know what grub is nor should they care.

Linux is *NOT FOR* the "average user". It is for people who want to know how the system works, want to customise it and want as much "Techo-babble" as possible. It's like Legos. The "average user" buys a toy car. The Linux User buys a box of Lego car parts and build their own cars. 

>The choices also meant nothing to me as windows developer. 

So you just ignored them and chose "yes". Then were SHOCKED when it did EXACTLY what you told it to do.

> Updates should run unattended, and "glib" as those who ignore 99% of pc users. 

Not Linux updates. They are for people who WANT to know what's going on every step of the way and have a hand in/choices in the process. 

So put back your Windows MBR. Super simple. Use either EasyBCD in Windows or the ms-sys command in Linux. It will take you 10 seconds to fix it. Ten seconds!

Thank you, I fixed the MBR. We need an alternative to Windows for average people, Linux is at 1% market share so I think they should try harder. I'd fix it myself if they'd let me.

---

### Post by Fred Doolie on 2011-11-13
> **Rebelli0us said:**
> We need an alternative to Windows for average people

Very true. I agree with you. There is one that is very close to that. Ylmf.  It is a Linux that is so "Windows-ized" that the average user would say "Oh, cool, a new (but kinda different) version of Windows!"

[http://en.wikipedia.org/wiki/Ylmf_OS](http://en.wikipedia.org/wiki/Ylmf_OS)

---

### Post by jocko on 2011-11-13
> **Rebelli0us said:**
> The average user does not even know what grub is nor should they care. 
The "average user" don't run linux from the windows boot loader. That requires quite a lot of work and knowledge about how to configure the windows boot loader...
The "average user" lets the installer install grub to the mbr, and let grub take care of the dual boot setup.
So the "average user" would not have had *any* problems with this update, even if they did not care to read the prompts during the update.
If you know enough to set up the windows boot loader for a dual boot setup with linux (which it is not designed for), you should also be able to read a message that ask you if you want to install grub to the mbr or not, and make the proper decision based on which boot loader you want in your mbr...

But if the message was really so technical that you did not know what the different options meant, then that's a bug that needs to be reported.

---

### Post by Rebelli0us on 2011-11-13
> **jocko said:**
> The "average user" don't run linux from the windows boot loader. That requires quite a lot of work and knowledge about how to configure the windows boot loader...
The "average user" lets the installer install grub to the mbr, and let grub take care of the dual boot setup.
So the "average user" would not have had *any* problems with this update, even if they did not care to read the prompts during the update.
If you know enough to set up the windows boot loader for a dual boot setup with linux (which it is not designed for), you should also be able to read a message that ask you if you want to install grub to the mbr or not, and make the proper decision based on which boot loader you want in your mbr...

But if the message was really so technical that you did not know what the different options meant, then that's a bug that needs to be reported.

Ubuntu installation has a simple option to NOT install boot loader. Once installed that way, the OS must respect that choice. If there’s no grub on the mbr, Linux must assume that’s how the user wants it.

Creating UI/shell is a very fine art. Microsoft had a very gifted UI guy in the late 1990s, Linux never had one so it has a Mickey Mouse UI and tries to compensate by adding a lot of useless Bling.

You guessed right, I’m not an "average user" ;)

---

### Post by Fred Doolie on 2011-11-14
> **Rebelli0us said:**
>  Linux never had one so it has a Mickey Mouse UI and tries to compensate by adding a lot of useless Bling.

Actually Linux (OK, Unix/X-Windows) had a GUI well before 1990.  

Which of the multiple Linux UIs are you referring to?  Personally I'll take KDE, Gnome or LXDE over the Windows UI any day.  I've said it before and I will repeat. My system FLIES with the LXDE UI. SUUUPER fast! Folders open and fill with icons before I can get my finger off the mouse button (With the correct 173 Nvidia Driver that is).

Even Gnome and KDE are faster than Windows and I'm using the rotating cube desktops and all the fancy exploding/burning/shattering window effects. 

If that's "Mickey Mouse" I'll take it.  Please, I'm not trying to have a fight. Why is the Linux UI "Mickey Mouse"? 

The Win UI was made by people who are being paid to make things the way that one person wants for the sole purpose of making money. The Linux UIs were designed by many for the sole purpose of easy use of their systems.

---

### Post by jocko on 2011-11-14
> **Rebelli0us said:**
> Ubuntu installation has a simple option to NOT install boot loader. Once installed that way, the OS must respect that choice. If there&#8217;s no grub on the mbr, Linux must assume that&#8217;s how the user wants it.
I partially agree with you, but I also think that a user that does something advanced like booting linux from a windows boot loader should also understand that there may be a few problems doing so.
It should be possible to set grub not to do anything:
```
sudo dpkg-reconfigure grub-pc
```You'll get a few questions about what you want grub to do. Leave the first ones as they are, but when you get to the point where you can choose which mbr to install to, just deselect everything (or if you want it in the mbr of another drive or in a partition boot record, choose the appropriate option).
Hopefully this would stop grub from overwriting your mbr in the future.
If this works, then there is no reason why choosing not to install grub during the ubuntu install would not do the same. Either way, you should report it as a bug, otherwise no developer will even know about your problem, and it will never get fixed.


> **Rebelli0us said:**
> Creating UI/shell is a very fine art. Microsoft had a very gifted UI guy in the late 1990s, Linux never had one so it has a Mickey Mouse UI and tries to compensate by adding a lot of useless Bling.
I guess you mean gnome and kde are "Mickey mouse" UIs. (And by "Mickey Mouse" you mean amateurish or poor quality?)
That's a matter of taste, but I prefer having complete control over my computer's resources, rather than having some guy at Microsoft decide which useless services to run at startup.
Why, for example, should a completely new computer with a core i5 cpu, 4 Gb ram and a reasonably good dedicated graphics card take more than two minutes to boot up into a usable state (and when it's fully booted, constantly read or write something unknown from/to the hard drive without me asking it to do anything, making everithing really slow). That's my experience of Windows 7 on my laptop (which boots up in 20 seconds with a standard Ubuntu install, fully usable and without any unknown services putting on the breaks).
The "bling" you talk about, in which way is it different from the "bling" in windows vista, 7 or Mac OSX (I assume you refer to graphical effects). Sure some of the compiz effects are probably completely useless and just examples of bad taste (burning, exploding or spinning windows), but others are quite useful (desktop cube or wall, zoom etc) or at least make the gui feel more alive (as the more subtle window animations).

---

### Post by Rebelli0us on 2011-11-14
> **Fred Doolie said:**
> Actually Linux (OK, Unix/X-Windows) had a GUI well before 1990.  

Which of the multiple Linux UIs are you referring to?  Personally I'll take KDE, Gnome or LXDE over the Windows UI any day.  I've said it before and I will repeat. My system FLIES with the LXDE UI. SUUUPER fast! Folders open and fill with icons before I can get my finger off the mouse button (With the correct 173 Nvidia Driver that is).

Even Gnome and KDE are faster than Windows and I'm using the rotating cube desktops and all the fancy exploding/burning/shattering window effects. 

If that's "Mickey Mouse" I'll take it.  Please, I'm not trying to have a fight.** Why is the Linux UI "Mickey Mouse"? **

The Win UI was made by people who are being paid to make things the way that one person wants for the sole purpose of making money. The Linux UIs were designed by many for the sole purpose of easy use of their systems.

It’s just my professional opinion. I used to make a living in UI design, retired in my 40s to do other projects. Also the 1% Linux market share speaks volumes.

---

### Post by Rebelli0us on 2011-11-14
> **jocko said:**
> I partially agree with you, but I also think that a user that does something advanced like booting linux from a windows boot loader should also understand that there may be a few problems doing so.
It should be possible to set grub not to do anything:
```
sudo dpkg-reconfigure grub-pc
```You'll get a few questions about what you want grub to do. Leave the first ones as they are, but when you get to the point where you can choose which mbr to install to, just deselect everything (or if you want it in the mbr of another drive or in a partition boot record, choose the appropriate option).
Hopefully this would stop grub from overwriting your mbr in the future.
If this works, then there is no reason why choosing not to install grub during the ubuntu install would not do the same. Either way, you should report it as a bug, otherwise no developer will even know about your problem, and it will never get fixed.



I guess you mean gnome and kde are "Mickey mouse" UIs. **(And by "Mickey Mouse" you mean amateurish or poor quality?)**
That's a matter of taste, but I prefer having complete control over my computer's resources, rather than having some guy at Microsoft decide which useless services to run at startup.
Why, for example, should a completely new computer with a core i5 cpu, 4 Gb ram and a reasonably good dedicated graphics card take more than two minutes to boot up into a usable state (and when it's fully booted, constantly read or write something unknown from/to the hard drive without me asking it to do anything, making everithing really slow). That's my experience of Windows 7 on my laptop (which boots up in 20 seconds with a standard Ubuntu install, fully usable and without any unknown services putting on the breaks).
The "bling" you talk about, in which way is it different from the "bling" in windows vista, 7 or Mac OSX (I assume you refer to graphical effects). Sure some of the compiz effects are probably completely useless and just examples of bad taste (burning, exploding or spinning windows), but others are quite useful (desktop cube or wall, zoom etc) or at least make the gui feel more alive (as the more subtle window animations).

Yes I mean exactly that. Gratuitous, tasteless bling, the taskbar panels in particular are a user interface disaster because of the mouse-over effects.   I don’t like Vista or Vista Lite 7 either but for different reasons than you, even XP irks me because it calls home every time it boots, 2000 is my favorite.

I still use Linux though, recommend it, and install it on friends’ machines because the invisible part (the kernel) is more stable than MS, it’s open source, and overall it’s more than adequate for 95% of people. I promote it because the MS monopoly is too much and people need a viable alternative.

It’s a very interesting topic. . . Ubuntu boots faster than any Windows but it’s annoying that they cut corners to do so, e.g. the start menu is not loaded so the first time you click it takes too long to load. Basic stuff like waking the machine by tapping the keyboard is easy to do in Windows but it's a nightmare in Linux [even for experienced users]("http://ubuntuforums.org/showthread.php?t=884039"). From a pure UI design/usability/intuitiveness standpoint, Gnome and KDE have yet to match windows 98 from 13 years ago. It probably won’t matter now because portable devices are the future, and Linux already has an advantage there.

---

### Post by Fred Doolie on 2011-11-14
> **Rebelli0us said:**
> Also the 1% Linux market share speaks volumes.

Ah yes. The fact that M$ (and Apple) spends many millions on advertising and Bill cut a deal with computer makers that 99.99% of all new PCs ship with Windows(tm) on them has nothing to do with it. 

Try to buy a new off-the-shelf computer with*OUT* Windows on it. It's a "special order" and may cost more. Also the sales-droid will tell you that you HAVE to have Windows (or MacOS) or the computer won't work!  

Walmart use to have a few Linux computers but people said "What's Linus?" then bought the ones that said "Windows" because that's what they saw on TV.

---

### Post by Fred Doolie on 2011-11-14
> I still use Linux though, recommend it

I may have misjudged you or misread your posts. Apologies.

>start menu is not loaded so the first time you click it

Oh that's why. I thought my system was messed up. ty

>usability/intuitiveness

Also an interesting discussion. Usability vs Intuitiveness. One example being a word processor.  Intuitiveness is deleting five words by using pull-down menus, mouse drags and icons. Usability is just typing "D5W" in command mode.

---

### Post by Fred Doolie on 2011-11-14
> **Rebelli0us said:**
> If there’s no grub on the mbr, Linux must assume that’s how the user wants it.

IMHO if there is no Grub found in the MBR Linux must assume that the install is damaged or incomplete.

---

