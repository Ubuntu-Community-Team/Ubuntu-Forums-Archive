---
title: "How do I disable screen blanking?"
date: 2009-11-03
forum: General Help
---

### Post by johnklos on 2009-11-03
Hi,

It seems that nobody's posted a viable way to disable screen blanking. setvesablank doesn't do it (also, the web-based manual page is out of date), BLANK_TIME=0 in /etc/kbd/config doesn't do it, and "setterm -blank 0" isn't a solution because the login prompt would still get blanked even if this did work.

Does anyone know how to simply turn off screen blanking? More importantly, could you tell me HOW I might've found the information myself? "apropos blank" just gives setvesablank, and Google gives a hundred posts about screen blanking in KDE / Gnome / whatever, but nothing about the text console.

Thanks,
John Klos

---

### Post by alphaniner on 2009-11-03
There's also the -powersave and -powerdown options to **setterm**, have you played with them?

---

### Post by johnklos on 2009-11-04
setterm gets run AFTER someone logs in. I'd like to know how to stop screen blanking altogether, since all of my Ubuntu instances are running as virtual machines.

But more importantly, I want to learn about how Ubuntu documentation works. I want to know where I'd find the information so I don't have to ask in the future. It would seem somewhat silly if someone decided that screen blanking should be enabled on all Ubuntu installations, but that there was no need to document it in any meaningful way.

Perhaps I'm just not looking in the right places... I have to believe that it's documented SOMEWHERE, or that the discussion about adding screen blanking as the default in ALL installations exists SOMEWHERE.

Thanks!

---

### Post by Baka no Kami on 2009-11-17
I'm having a problem disabling screen blanking on an old laptop I converted into a digital picture frame.  It has xorg installed on it, but no window manager and it boots to a text login.  I put the the commands to start the slide show in /etc/rc.local and it runs without the need for someone to log in.  

I tried putting setterm in the script I use to start the slide show and restart if new pictures are added, and it didn't work.

I haven't tried putting the setterm command directly in rc.local, but it's my next thing to try.

If anyone else has a better idea how to disable blanking I'm all ears.

---

### Post by Baka no Kami on 2009-11-18
Putting the setterm command in rc.local didn't work for me, but I find something that did.

I created a xorg.conf file in /etc/X11 and put the following section in it.

Section "ServerFlags"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

So far the screen hasn't gone off.  We'll see if it stays like that.  This system starts up and runs X for the sole purpose of running feh to display images, so I'm nto sure if it'll work the same for you.

---

### Post by thewolfman on 2009-11-23
> **Baka no Kami said:**
> Putting the setterm command in rc.local didn't work for me, but I find something that did.

I created a xorg.conf file in /etc/X11 and put the following section in it.

Section "ServerFlags"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

So far the screen hasn't gone off.  We'll see if it stays like that.  This system starts up and runs X for the sole purpose of running feh to display images, so I'm nto sure if it'll work the same for you.

Hi Baka,

can you explain the steps you used to create your new file, did you overwrite the original?.

Thanks in advance thewolfman.:D

---

### Post by ronocdh on 2009-12-01
> **Baka no Kami said:**
> Putting the setterm command in rc.local didn't work for me, but I find something that did.

I created a xorg.conf file in /etc/X11 and put the following section in it.

Section "ServerFlags"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

So far the screen hasn't gone off.  We'll see if it stays like that.  This system starts up and runs X for the sole purpose of running feh to display images, so I'm nto sure if it'll work the same for you.
This was immensely helpful, thank you. Worked like a charm for me. Server install of Ubuntu with X and fluxbox added.

---

### Post by Baka no Kami on 2009-12-01
> **thewolfman said:**
> Hi Baka,

can you explain the steps you used to create your new file, did you overwrite the original?.

Thanks in advance thewolfman.:D

Pretty much just "sudo vi /etx/X11/xorg.conf"  and put the part I listed above in it.  There wasn't an existing file to overwrite.  I remember reading that they've done away with xorg.conf for the newer versions.

---

### Post by sureshms on 2011-06-17
Im having the same problem. Im running ubuntu 11.04. Even after entering the code given above into a xorg.conf file when i executed the "xset q" command in the terminal to check the status it still showed that screen blanking was enabled. Has anyone come up with any soultion?

---

