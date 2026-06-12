---
title: "Ubuntu desktop fails to display properly; i screwed my drivers up... where to proceed"
date: 2009-06-29
forum: General Help
---

### Post by KaiserJ on 2009-06-29
hi everyone! ubuntu newbie here; i just installed this impressive OS on a dual boot with vista about a week ago; i was looking for a good alternative to windows that could run the spring engine; and am very happy with what i've found.
 
to business... i was trying to install the xorg ATI driver for my integrated 2100 radeon, and somewhere along the line, i think i deleted something that was crucial to my display settings... now when ubuntu boots up, i can see the loading screen (ubuntu logo and progress bar) but when it reaches the point where the desktop would be displayed, i see the scrambled bars that are indicative of a non-compatible display mode.
 
so a bunch of questions... im sure some of them will be "stupid" ones, as i'm very new to this OS. keeping in mind, Vista was installed first, and still works fine (however im using GRUB instead of MBR for my booting.) there is nothing of "worth" in my ubuntu install, i didn't actually use it to do any work, so wiping everything and beginning again is a viable option.
 
1) is there any way to repair this problem without a re-install? as far as i can see from booting in safe mode, it still loads into the same scrambly screen... is there some way i can revert to my old setup?
2) is there a way to wipe and then re-install ubuntu on the partition it currently resides in without hopelessly borking my computer? how might i go about doing that; will it screw up my booting if i were to do it?
3) is there a way to change from GRUB to MBR without using my Vista install disk (i bought my computer at future shop, for whatever reason, they don't give out vista disks)
 
any information, or even somewhere to begin, would be really appreciated.
 
thanks in advance for reading my long-winded and noobish post
 
cheers, your pal kaiser!

---

### Post by askreet on 2009-06-29
Hi Kaiser,

Sounds like you've done some of your homework here, ATI drivers are notoriously a pain in the butt.  How did you go about installing them, could you provide the URL to any guides you used?

Also, a side note that MBR simply stands for "Master Boot Records".  GRUB is in fact installed in your MBR, windows uses a different bootloader that is installed in the MBR instead.

On the topic of re-installs.  You can reinstall the same way you did the first time and select Manual Partitioning, then select the "Linux" partition to be used at "/".  It's fairly intuitive.  be sure not to use the NTFS parititon for anything and you should be good.  GRUB will be re-installed and will re-configure automatically for Ubuntu+Vista.

On the topic of reinstalling the Windows bootloader over grub, you can boot into a Windows Recovery Console (I don't recall how this is done in Vista, in XP it was an option during the install CD screen).  Once in here there is a command called "FIXMBR" which does exactly that.

Re-installing may be the simplest approach at this point.


HTH,
- Kyle

---

### Post by Laysan_A on 2009-06-29
Hi KaiserJ,

I've tried at least three different attempts to get ati's fglrx to work. Each time the graphics were messed-up.

You didn't mention if you'd tried anything at all yet. Usually rebooting into recovery mode and selecting to reconfigure the graphics solves the immediate problem of getting back to the desktop. Sometimes the ati drivers need to be removed before your graphics can be restored. I don't know why the x recovery system seems so arbitrary some times.

Give this a shot first:
sudo apt-get remove xorg-driver-fglrx

You didn't mention what kind of system you have, but whatever, you should also remove catalyst. Thing is, I don't know if amd means amd processor, or amd/ati...
Well, either way it won't hurt anything to try.
sudo apt-get remove fglrx-amdcccle

You shouldn't have any problem restoring your graphics to the open source drivers once the fglrx drivers are gone. Just boot into recovery and arrow down to the graphics line (it's not visible, I think).

Alternatively, you can try this. I have it on good authority that it's effective:
[http://ubuntuforums.org/showpost.php?p=5717943&postcount=2](http://ubuntuforums.org/showpost.php?p=5717943&postcount=2)

After you're done, you might just go ahead and do a *sudo apt-get -f* in case anything was left broken.

There are a few good threads here addressing ati's propriatary drivers. It's only a matter of time before these issues get sorted - they worked beautifully in Intrepid. Search for ati and, who knows, you might find what you need.

---

### Post by KaiserJ on 2009-06-30
hi guys, thanks for the prompt and helpful responses!
 
to kyle... thanks for clearing up my confusion about the MBR ;) i had read some tutorials, but gotten the wrong end of the stick.
 
in either case, i re-installed ubuntu (for anyone who googles and finds this, i put my main ubuntu partition as root and wiped my swap disk) and it worked out fine; just as i had hoped it would.
 
now. as far as my "card" is concerned; it's an integrated radeon 2100 on an AMD board. for my first attempt, when i saw a scrambly screen, i had installed the drivers directly from the package manager. not willing to let well enough alone, i attempted it again, using a link directly from the AMD site. it gave me the same scrambly error, but i was able to boot in safe mode and use a text based package manager (the name escapes me) to remove the offending packets; and restored my desktop yet again (now that i know how to do it, im a little more brave about tinkering)
 
to laysan... i mentioned fixing things with a text-based package manager; before i did so, i may have navigated to that page you linked me, as i certainly remember entering
 
```
sudo dpkg-reconfigure xserver-xorg
```
 
it gave me a message like "conflicting criteria, -c conflicts with -f" or something to that effect; didn't actually do anything.
 
if i CANT get this integrated card to work, it's not the end of the world; i plan on installing a new graphics card either way... in fact, i have this sitting in a box on my desk:
 
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3747342&Sku=A271-3870](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3747342&Sku=A271-3870)
 
as far as i can see, there's an up to date linux driver available for it, so i doubt this card would give me any grief; however, as a new ubuntu user drifting over from vista, i wanted to see how well the OS would perform as a comparison without any extra hardware added it. would you guys recommend this card; or should i go with nvidia instead? its not a problem to return it and buy something else a little more expensive.
 
any opinions on the card situation are appreciated, just looking through other peoples discussions right now; thanks for being helpful guys, really takes a load off my mind knowing that people who know what they're talking about are willing to help me <3.
 
- KaiserJ

---

### Post by Laysan_A on 2009-06-30
Hi KaiserJ,

I'm glad you got it all sorted.

At this particular time, if what you want is just to have a properly working graphics card, I would have to say that if you have a choice go with nvidia. Nvidia is much better supported under linux than ati is at the moment.

However, if what you want is to tinker, and you don't mind waiting a while before everything's working really well, you might want to stick with your ati. I'm assuming your motherboard is crossfire capable; if so, you might eventually end up with a working crossfire set-up (eventually), if you stick with ati.

---

