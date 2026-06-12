---
title: "Xubuntu freezes on start up."
date: 2009-12-21
forum: General Help
---

### Post by feltopi4 on 2009-12-21
Hello, I am new to this whole Linux thing, so please bear with me.I decided to give the Xubuntu a try and installed it. I installed Xubuntu 9.10 on a separate partition to Windows. I used the ext3 file system with a "/" and "/home" partition.

The newly installed copy just froze (and I didn't do anything crucial like updating it or installing anything). It occurred after; leaving the computer unattended (mostly three minutes the longest); just plainly going through different windows; or right clicking the mouse (not too sure on that). I am beginning to think it is just at random.

After a manual restart (the only way to get out of the big freeze) Xubuntu refuses to boot up (through GRUB); leaving a black screen after the splash screen of the mouse glowing disappears. This happens with every installation.

Nothing is wrong with the computer because Windows XP works fine on the first partition.
How do I fix this problem without reinstalling Xubuntu again? What did I do wrong, was I supposed to use "/boot" instead of "/"? Would it be a problem caused by the copy of Xubuntu I got?

---

### Post by Bucky Ball on 2009-12-22
You also need:

/swap

Maybe starting again might be easiest. 9.10 can also be pretty buggy for some as it has only been out for a couple of months (nearly) and perhaps not the best place to start. :)

---

### Post by feltopi4 on 2009-12-22
"You also need:

/swap

Maybe starting again might be easiest. 9.10 can also be pretty buggy for some as it has only been out for a couple of months (nearly) and perhaps not the best place to start."


Actually, I do have a /swap partition (set to 1GB).

---

### Post by Bucky Ball on 2009-12-22
You didn't mention that. ;)

---

### Post by feltopi4 on 2009-12-23
"You didn't mention that." 

Sorry, I sorta looked over that one. Well while I am at it, I am installing the Xubuntu on a Dell Dimensions 2400 with 256MB of RAM and Intel 2.80GHz pentium 4. 

I reinstalled Xubuntu but the same problem came back(this time I managed to go so far to update it). Would it have anything to do with my computer set-up?

---

### Post by feltopi4 on 2009-12-23
OH, well nevermind. I seen to have fixed it, by following looking through some of the other threads in this forum. All I did was use "gdm" in the root thing of the recovery mode and then used the terminal to remove xsplash once the desktop booted up.

---

### Post by feltopi4 on 2009-12-23
"OH, well nevermind. I seen to have fixed it, by following looking through some of the other threads in this forum. All I did was use "gdm" in the root thing of the recovery mode and then used the terminal to remove xsplash once the desktop booted up. "


Yeah, scratch that last post by me. Unfortunately, the problem came back after restarting my computer. Now I am just fed-up.

---

### Post by Bucky Ball on 2009-12-24
Your small RAM could be the problem. Try Crunchbang or install from Alternate ISO rather than the Desktop. It is same but text based install. Odd though. 128mb is suggested on the site but these things happen and it seems to be slightly different for different machines in my experience.

I _strongly_ suggest you try the enterprise release, 8.04 LTS, and see if that works. If it doesn't nothing will as it is rock solid and that would clearly show whether a tweak is required for your machine and Xubuntu to be friends or it is yet another 9.10 bug (would wait a few months myself, probably not the best place to start).

---

### Post by feltopi4 on 2009-12-25
"Your small RAM could be the problem. Try Crunchbang or install from Alternate ISO rather than the Desktop. It is same but text based install. Odd though. 128mb is suggested on the site but these things happen and it seems to be slightly different for different machines in my experience.

I strongly suggest you try the enterprise release, 8.04 LTS, and see if that works. If it doesn't nothing will as it is rock solid and that would clearly show whether a tweak is required for your machine and Xubuntu to be friends or it is yet another 9.10 bug (would wait a few months myself, probably not the best place to start)." 


Thanks for your reply. I kinda knew my RAM would be below requirements event though the website did say it could run on 128mb; but I was reluctant to believe my assumption. I had already uninstalled Xubuntu and installed OpenSUSE 11.2 with xfce. This is running alot more stable on my computer than the other distros I tired (Kubuntu, Ubuntu and Xubuntu; in that order).

---

### Post by droadtrip on 2009-12-25
[FONT=Georgia][SIZE=3][COLOR=Navy]Your number one cause is tiny ram. Very few Linux Distros can operate on less than a gig of ram, even if you have the minimum required amount. Just a few common programs in the OS and the whole thing will freeze and panic. It happened to me on my netbook before I got rid of it. [/COLOR][/SIZE][/FONT]

---

