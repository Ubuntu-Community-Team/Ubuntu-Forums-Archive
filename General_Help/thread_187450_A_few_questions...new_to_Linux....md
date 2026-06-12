---
title: "A few questions...new to Linux..."
date: 2006-06-03
forum: General Help
---

### Post by Cable on 2006-06-03
Greetings.  I have never ever used Linux before, and I am thinking about setting up a dual boot on my Win XP box.  Really the only thing that keeps me on Windows is games.  I've got a few questions...

1)  I downloaded the desktop CD so that I could try out Ubuntu a little using the Live CD ability.  Ubuntu started booting perfectly, got through the initial loading process and everything.  Then, the screen just went black, and nothing happened, it just sits there.  Any advice on how to get that to work?

2)  I'm wondering if Ubuntu will properly detect my video, wireless, and sound cards.  I have an ATI Radeon 9800 XT, a Linksys WMP54G, and an Audigy 2 sound card.  Anything I should download and store away beforehand just in case so that I have whatever I'll need to get those working?

3)  Does Ubuntu work okay with SATA drives (NON RAID)?

Those are the only questions I can think of at the moment.  Any help for a complete Linux greenie would be greatly appreciated!

---

### Post by grsing on 2006-06-03
1. When the screen goes black, is there a little white rectangle in the far upper left corner?  If so, it's still just loading, give it time (it took my computer 5, maybe even 10 minutes, not sure why it took so long, but have faith).

2. They will probably be detected just fine, but you'll want to install the drivers for them.  ATI drivers are a mess, and I'm not an expert on that, so I'll defer it to someone else.  Wireless is fun, search around on the forums and in the wiki (link in the upper right corner of this page).  I have an Audigy 2, also, it works fine, though if you're using it for 5.1 or greater I think there's something you have to download (sorry, I did it a while ago, and haven't tried it since the upgrade, I'll look into it if it doesn't work out of the box for you).

3. Just plugged an SATA in today, works like a charm.

---

### Post by Third Thoughts on 2006-06-03
[QUOTE=Cable]Greetings.  I have never ever used Linux before, and I am thinking about setting up a dual boot on my Win XP box.  Really the only thing that keeps me on Windows is games.  I've got a few questions...

1)  I downloaded the desktop CD so that I could try out Ubuntu a little using the Live CD ability.  Ubuntu started booting perfectly, got through the initial loading process and everything.  Then, the screen just went black, and nothing happened, it just sits there.  Any advice on how to get that to work?

2)  I'm wondering if Ubuntu will properly detect my video, wireless, and sound cards.  I have an ATI Radeon 9800 XT, a Linksys WMP54G, and an Audigy 2 sound card.  Anything I should download and store away beforehand just in case so that I have whatever I'll need to get those working?
[/QUOTE]

1 and 2 may be related in that maybe Ubuntu isn't properly detecting your video card. Since you're working off the Live CD its very hard to detect the problem since you can't even get to the point where you could run dmesg. My only suggestion would be googling your video card. Where exactly in the boot process does it go funny though?

---

### Post by eqisow on 2006-06-03
1) It sounds like X didn't autoconfigure correctly. I'm afraid I'm not sure what to do about this on the Desktop CD. Maybe somebody else can help

2) I know for a fact that the WMP54G works flawlessly in Linux, the sound card should as well. Your video card will work, but if the Desktop CD is any indication, it may require a tweak or two.

3) Yes

P.S. - Welcome to the community! :)

Edit: Also, if you decide to install you will probably need to do it with the Alternate CD since the Desktop CD won't start. Fixing your display drivers once Ubuntu is on the hard disk should be easy, and we can help you through it.

---

### Post by hscottyh on 2006-06-03
1) When the screen goes blank, can CTR+ALT+F1 and get a terminal? Sounds like it may be your video. I don't have any experience with ATI, however.

---

### Post by Cable on 2006-06-03
[quote=Third Thoughts]Where exactly in the boot process does it go funny though?[/quote]

Ubuntu finishes doing the entire initial boot process.  It appears to me that it's about to show the desktop environment when the screen goes black.  And, as far as I know there is no white rectangle on screen when this happens.  I wish I could get it to work, I'd really like to give it a try before committing a decent amount of time to backing up a crapload of stuff and then installing Ubuntu.

---

### Post by Cable on 2006-06-03
[quote=hscottyh]1) When the screen goes blank, can CTR+ALT+F1 and get a terminal? Sounds like it may be your video. I don't have any experience with ATI, however.[/quote]

I just tried booting from the CD again.  When the screen goes blank, it actually sounds like my monitor is turning off.  It doesn't go into standby mode (when the power light blinks), rather, I can hear the display turn itself off, but the power light remains on.  Also, Ctrl + Alt + F1 yields no results whatsoever.

---

### Post by bionnaki on 2006-06-03
I have a similiar setup: audigy 2, wmp54g, and ati 9600.

sound works out of box.
ati takes about 10 mins of work to install the driver.
this works for me:

> open up synaptic
search for fglrx
mark xorg-driver-fglrx for installation
mark fglrx-control for installation
apply changes

once the packages are installed, open a terminal

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf

in the gedit window, find the section "devices"
in this section you will see:
driver "ati"
change the "ati" to "fglrx"
save

at this point you will want to restart x so either save all your open work and press CTRL ALT BACKSPACE or restart your computer.

when you log back in open a console and type

fglrxinfo

you should see information about your ATI video card. If you see something about MESA then you did something wrong.

If for some reason you can not start xorg after this then log in via command prompt and type sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf to restore you old xorg settings.

and for the wmp54g, follow what I wrote and you'll have WPA: [http://www.ubuntuforums.org/showthread.php?t=161376](http://www.ubuntuforums.org/showthread.php?t=161376)

no need to create the script that the original poster wrote...
just follow my instructions.

just open a terminal and enter:
> sudo gedit /etc/network/interfaces

and copy/paste my interfaces and save.

enjoy!

---

### Post by Cable on 2006-06-03
Well, I just went downstairs and tried booting from the CD on my dad's computer (nVidia video card) and it worked flawlessly.  I must say, Ubuntu is a great looking OS!  Now I'm even more excited to try it out.  Currently downloading the alternate CD ISO via bittorrent.  So, I'm assuming the desktop cd has an issue with my video card, as stated above.  Does that mean I'll have problems once I actually get Ubuntu installed on my system?  Also...how do I install using the alternate cd?  Or is it still pretty straightforward?  Sorry for so many questions, just trying to figure things out so I have some idea of what I'm doing whenever I get around to this.  I'm most definitely not new to computers, but I've never touched Linux and haven't the first clue about commands and whatnot.  Thanks for the help.

---

### Post by Cable on 2006-06-03
[quote=bionnaki]
and for the wmp54g, follow what I wrote and you'll have WPA: [http://www.ubuntuforums.org/showthread.php?t=161376]("http://www.ubuntuforums.org/showthread.php?t=161376")
[/quote]

You say if I do this I'll have WPA...do I need to do anything else to have WEP?  I do all the network administration at my home (parents/siblings know nothing about it) and due to a couple of wireless devices we need that don't have WPA capabilities, I can't use WPA on the router...

---

### Post by eqisow on 2006-06-03
WEP will work by default. :)

---

### Post by Cable on 2006-06-03
So how do I use the alternate install CD?  Is there a guide somewhere, or can anybody here give me a step-by-step?  I haven't looked at it yet, so I don't really know what to expect from it (difficult to understand, or easy to use but just text-based).

---

### Post by bionnaki on 2006-06-03
whats an "alternate" install cd?

---

### Post by grsing on 2006-06-03
You'll probably just have to install the drivers for your video card to make it work right, a pretty minor issue (probably).  If the alternate CD is like the old installer (which I think it is), it's pretty much the same as the normal one, just in an ugly, DOS looking interface without mouse support.  Not hard, just not pretty looking.

Once you do get it up and running, you may want to run Automatix ([http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)) to install all the codecs and non-free (free as in beer but not as in speech) programs and such that Ubuntu can't include for legal reasons and because it tries to keep the install size down.  For reference, this forum, the wiki ([https://wiki.ubuntu.com/)](https://wiki.ubuntu.com/)), the guide ([http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)), and a list of linux commands (I use [http://www.ss64.com/bash/](http://www.ss64.com/bash/)) is very useful (though of course, feel free to ask any questions).

---

### Post by Cable on 2006-06-03
Just thought of something...if I can't run Ubuntu from the live cd (since my monitor goes black), does that mean that when I get Ubuntu installed, it will do the same thing when I boot into it?  If so, what do I do about that?

---

### Post by Melvil on 2006-06-03
Maybe, but not necesarrily. If the screen goes blank on your local installation, you can examine the errors by 
a) booting a live-cd (knoppix i.e.) 
b) using an ext3 driver in windows
and then examine the contents of /var/log/Xorg.0.log and /var/log/messages

Have you tried the safe mode of the live cd? You might also try to boot the live cd with the parameters "noacpi" or "acpi=off", I'm not sure which one is correct

---

### Post by Cable on 2006-06-03
Well I guess whenever I install, I'll cross my fingers and hope for the best.

---

