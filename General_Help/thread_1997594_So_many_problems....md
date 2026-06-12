---
title: "So many problems..."
date: 2012-06-05
forum: General Help
---

### Post by nicknefarious on 2012-06-05
Hi All,

I have a fresh install of Ubuntu 12.04 64-bit (6 weeks or so old). I have experienced many issues with it and would like to get some help finding answers to a number of problems. The issues I am experiencing regularly are:-

1. something chewing up RAM – though haven't noticed it using too much SWAP. Usage grows until it reaches around 3615MB of the 3953MB available (4GB RAM) – this information from htop
2. CPU has regular spells where the CPU usage increases towards 100% for no apparent reason, it never gets all the way to 100% unless I am running many apps at once - but runs quite hot sometimes when lots of apps open sometimes when few are.
3. experience random slowdowns of the whole system for extended periods of 5 minutes or more. During these periods it is virtually impossible to do anything – even moving the mouse about the screen is generally not possible.
4. compiz and lightdm regularly use 30-50% CPU or more each – even when the system has been sitting doing nothing - is this normal behaviour or a problem?
5. Temperature increases in line with increased CPU/RAM use – information from htop
6. I ran a number of different audio player apps – Rhythmbox, Amarok, Banshee – all of which either froze or crashed totally while trying to import my large (30,000 songs) music library – (it is on an external USB) – I have started using Clementine which seems much happier and smoother though I haven't pressed it to scan my whole library yet.
7. I also have tried running Calibre as an ebook tool – it also struggles when importing a large amount of books. This could be a bug/deficiency with the app itself?
8. I tried using easytag to re-tag my audio library it also crashes somewhere around the 60-70% of library imported/processed mark. Segfault.
9. A number of apps I have installed have issues with overlay scrollbars meaning that they are rendered either difficult to use or useless – b-folders and x-mind are two apps that have scrollbar problems there are others that I haven't recorded.
10. When operating in Twinview using my nVidia 8600M GT and Ubuntu X-Swat PPA with Current Driver 295.53 installed/enabled – opening Movie Player to the second display or trying to move it there kills the launcher on both displays, freezes the second display and requires a restart or log out log back in to get the launcher and other things to work again. VLC Player has no such problems opening or being swapped to the 2nd display. Some times when activating Twinview in the nvidia-settings, compiz crashes, sometimes it restarts but most of the time after crashing I need to restart/reboot laptop to get things back to normal. On some occasions I have had to do a hard reset as nothing else would rectify the situation, waiting on some occasions for 15 minutes did nothing to resolve the problem. I couldn't even escape to another tty terminal – nothing.
11. When running in Twinview – if I enable “Place Windows” in CCSM (Config Settings) Window Management apps/dialogue windows open on the 2nd display when they should open on the main display even when an app is running on the main display it opens dialogue boxes on the second display. If I disable “Place Windows” in CCSM, many apps open in the extreme top left of the screen with the Title Bars, Menus etc. obscured so it becomes extremely fiddle to catch a small corner of the title bar to drag the appp out from under the top panel (Ubuntu's main top panel).
12. Random display issues in Chrome that see an image from one page displaying in the background or foreground of many other pages at the same time. This image can also display itself the background window of other apps.
13. I close apps and their window closes and they disappear from the launcher as if they are closed but then later I receive notifications or pop-up windows from the app, so obviously they did not close properly.

I am dual-booting with Windows 7 and I experience none of these problems. No CPU?RAM problems, no over heating. No problems with libraries, media or ebooks – no display issues. In fact most days I feel like just booting into Win 7 rather than Ubuntu. 

I have numbered my issues above so if you are able to reply or offer further information please reply with a number next to it. If you would like further info on any of the specific problems please just ask what it is you would like to look at and I'll do my best to provide it.

---

### Post by dino99 on 2012-06-05
have you installed third party apps ? ppa ?

htop ( and/or system monitor) will show you which process is eating ram

sudo dpkg-reconfigure -phigh -a
(wait for self ending, can take a while)

---

### Post by nicknefarious on 2012-06-05
Is there a simple way to print a list of installed apps and PPA's?

Can you explain what the command you have offered will do?

Which of the problems does this solution specifically address?

Thanks for getting in and posting so quickly.

Appreciated,

N

---

### Post by dino99 on 2012-06-05
> **nicknefarious said:**
> Is there a simple way to print a list of installed apps and PPA's? (sudo apt-get install synaptic && sudo synaptic )

Can you explain what the command you have offered will do? (reconfigure)

Which of the problems does this solution specifically address? (too lazy to read that all :()

Thanks for getting in and posting so quickly.

Appreciated,

N

comment inside

htop and/or system-monitor let you know which process is eating memory

---

### Post by nicknefarious on 2012-06-06
Hey Dino,

Thanks for getting back...

Any chance you could step into the Hurt Locker with me for a minute, that painful place where people might ask you to utter more than just one word answers, and expand on your > Can you explain what the command you have offered will do? (reconfigure)

Being that I am not so bright could you shed a little light for me onto what it will reconfigure and how?

If that's too much for you I guess I'll just have to say thanks for your time...


Cheers,

NN

---

