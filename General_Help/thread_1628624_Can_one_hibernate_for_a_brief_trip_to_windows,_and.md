---
title: "Can one hibernate for a brief trip to windows, and return?"
date: 2010-11-22
forum: General Help
---

### Post by phoenix17 on 2010-11-22
Eh, I'm sure you guys (and ladies :))can. I'm just new to this, and excited to learn!

First of all, I searched the forums but I couldn't find anything- I don't want to be the poster who posts something that's been solved 14 times already;)

Anyway, primary question first and then "why" below- I was wondering if there was a quick way to hibernate Ubuntu to Swap -> boot to Windows 7 and work -> Hibernate Windows 7 -> boot to Ubuntu and work, repeat until Windows glitches;)

I have, new Acer Aspire:
i3 370M
4GB RAM
640GB HDD as follows, from inside to outside:
X GB 3 Primary Windows partitions, 125 GB unnallocated, 50GB /home, 6 GB .boot, 4 GB SWAP


Ok, why would I want to do that?
I ask because while Ubuntu boots fast at just under 1 minute at the end of my hard drive (90Mbps, I had it install from "end" when I partitioned the boot file), Windows boots slowly at about 2.5 minutes on the inside of my drive (23sh Mbps). To be able to switch between them would be useful for iTunes, ProEngineer, Matlab, and other stuff that is Windows based. Windows boots much faster from hibernation.
I love Ubuntu, the speed and simplicity and the actual FRIENDLY atmosphere (what a concept WINDOWS;)) But I find myself needing to do some quick editing in Windows, then I can go back to my business on Ubuntu. Is there some kind of selective boot managing like GRUB that I can bring up after telling one to hibernate? Because once on SWAP, it should hold relatively indefinitely until I return, right?? 

Any ideas??? It sounds like some clever Terminal coding could manage the Linux side of the booting, but Windows might have to be tricked into a selective boot... They don't like to play with others lol

---

### Post by t4thfavor on 2010-11-22
Suspend to disk from Ubuntu, not sleep, but hibernate. Then select Windows from the GRUB menu. When your done, shutdown or hibernate, and pick Linux. It should* resume just fine, and your off to the races!

---

### Post by wilee-nilee on 2010-11-22
With my setup it takes hibernate as long to start up as a regular startup. Personally I wouldn't do that, but it may be a safe practice hopefully we will actually find out.

I would just think about the down side of doing this, can you afford to have your computer go south so to speak, at any time.

---

### Post by oldfred on 2010-11-23
Some who hibernate windows say it works, until they decide to copy something from Ubuntu into windows and corrupt the hibernation and have to totally reinstall windows. 

Since windows does not write into the Ubuntu partition it is a little less risky, but like wilee-nilee my boot is just as fast as recovery from hibernation and then you know you have a good system.

I do create a shared NTFS partition for firefox and thunderbird profiles and any data I may want to share. Then I do not have to write into windows, but I still would not recommend hibernation in a dual boot environment.

---

### Post by phoenix17 on 2010-11-23
Success! I guess the first time I tried it I hibernated windows, booted ubuntu, hibernated ubu, then as i was booting again i looked away and it did the countdown and booted straight to ubuntu again. Or something like that.

But now I can boot to windows faster. My personal results are as follows:

Windows response is much faster both in booting and powering down (hibernate mode).
Ubuntu is twice or more slower to power down in hibernate, but about the same time to boot. So I guess if stuff is worth saving all open, it's at least an option.

I will keep Windows hibernated all the time now!

Thanks for the quick responses guys!:D Linux is going to rock. I want to learn to code some ****. All I know about coding now though is Matlab. I can write control code for motors and sensors, but applications is my next step ;)

Now, what's with the little coffee bean things? I said "green bean" when I first saw it... but Idk if that's on the mark or not?

---

### Post by phoenix17 on 2010-11-23
> **oldfred said:**
> Some who hibernate windows say it works, until   ...............     but I still would not recommend hibernation in a dual boot environment.



Duly noted! I think at the most I will drag files *from* Windows, but not vice versa. For internet settings, I use Chrome, and they do their own server sync which is especially convenient in this case.

I do understand that there could be some disk permission confusion and one causing the other to fail. However I sync all my Windows important files with my main desktop using Live Mesh when windows is running (thats how i transferred them to this computer actually), so if Windows, or even this entire hard drive has to be wiped and redone, I won't cry. I have my most important things saved.

But I will note what you said about files into windows- that would be a huge pain to have to re do it, I really don't want to have to deal with that.

Would you say that grabbing a file from Windows from Ubuntu would cause problems if Windows is in hibernation?

---

### Post by wilee-nilee on 2010-11-23
Just have your W7 HD imaged on a external and backups of what your doing. W7 has a excellent backup setup that will make a image of the whole thing, all the files, and the little dog to.;) You can reload that whole image and it will still be activated with the Key.

---

### Post by oldfred on 2010-11-23
Reading from windows should not cause problems. I run a .bat file to copy the data files in windows to my shared NTFS partition that I do not directly save into it. As long as you understand the risks...

One of the issues is windows hides files & folders to prevent users from damaging system. With Ubuntu all those hidden files & folders are shown and easy to modify causing problems. Some recommend to only mount the windows system partition read only. Also using a Linux text edit on a Windows text file can cause line ending issues. Some editors are better than others at knowing if windows or Linux line endings.

---

### Post by phoenix17 on 2010-11-23
Yeah. Before I came to Linux, I was pretty efficient with Windows. Starting with XP, and then to 7, avoiding the steaming pile of Vista. So I know what to mess with and not to mess with, ironically from TRYING to mess with it removing a rootkit from my... uh... friend's computer... Lie. I got it from AIM. That started my long trek of freeware Windows protection software. That's all for other forums though.

The read only idea is excellent, I'm going to put that to work now. As well as partition more space for Ubuntu and transition to making Ubuntu my primary. I want to make it a slow shift though so I can get to know it here first. The information you guys are giving me helps immensely!

I'm going to mark this "solved" tomorrow. I have more questions... Should I search/post new forum or just ask directly here? (one is about partition formats and the other is about Wine)

---

### Post by tajiknomi on 2010-11-23
[SIZE=2]I think the best way to get answer is ..... 1st **Google your Question**, it will be more ***easy an fast***,if u don't get a suitable answer's ,then Post on Forum...:p

Moreover for Partitioning,an easy Tool ...> [/SIZE][http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by HermanAB on 2010-11-23
Howdy,

Dual booting is sooo 20th Century...
;)

Do yourself a favour and install Virtualbox or VMware Player and create a Windows XP virtual machine.  Then you can run Windows in a window, where it belongs and you won't look back.

---

### Post by wilee-nilee on 2010-11-23
> **HermanAB said:**
> Howdy,

Dual booting is sooo 20th Century...
;)

Do yourself a favour and install Virtualbox or VMware Player and create a Windows XP virtual machine.  Then you can run Windows in a window, where it belongs and you won't look back.

Hey, oh your always right we know that already.;)

---

### Post by tajiknomi on 2010-11-23
[SIZE=2]Virtual-Machine is Good but its not for **Game's**.... may be he is an ***Online-Gammer ;)***[/SIZE]

---

### Post by HermanAB on 2010-11-23
Games, sure, Windows is unbeatable for that - but then he would not want to return quickly to Buntu.

---

### Post by phoenix17 on 2010-11-23
Haha thanks guys. For games I'll use my desktop probably. I don't do much online stuff.

I'll check out that partitioning info. What I want to see is if it makes a difference which format to use for the home or boot logicals. I just followed some guy's directions I found online. It works great but I just want to sate my curiosity.

Thanks for all the help! :D

---

