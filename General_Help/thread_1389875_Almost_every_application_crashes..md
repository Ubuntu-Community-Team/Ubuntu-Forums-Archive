---
title: "Almost every application crashes."
date: 2010-01-24
forum: General Help
---

### Post by Robyr on 2010-01-24
Ok, I have been a linux user for over 10 years. I have been a Ubuntu fanatic since 6.04. On my new install of 9.10 on my Toshiba A135-S2247 I am having a very odd issue. Applications such as Firefox, Pidgin, even apt crash RANDOMLY! The dmesg outputs after crashes such as these look like this:
(pulse audio crashing? I wasnt even using the machine at this point)
[ 1154.689411] pulseaudio[1439]: segfault at 3c ip 001e9399 sp b764a130 error 4 in libpulse.so.0.12.0[1c8000+3e000]
(pidgin and synaptic)
Jan 24 16:42:07 phoebe kernel: [ 5741.950146] pidgin[4587]: segfault at 4 ip 00c15769 sp (null) error 6 in libpango-1.0.so.0.2600.0[bfb000+46000]
Jan 24 16:42:26 phoebe kernel: [ 5760.077586] pidgin[4641]: segfault at 4 ip 00535769 sp (null) error 6 in libpango-1.0.so.0.2600.0[51b000+46000]
Jan 24 16:43:23 phoebe kernel: [ 5817.066152] pidgin[4837]: segfault at 4 ip 00633769 sp (null) error 6 in libpango-1.0.so.0.2600.0[619000+46000]
Jan 24 16:46:16 phoebe kernel: [ 5990.226903] synaptic[4935]: segfault at 4 ip 007bd769 sp (null) error 6 in libpango-1.0.so.0.2600.0[7a3000+46000]
Jan 24 16:49:28 phoebe kernel: [ 6182.690509] nautilus[1594]: segfault at 4 ip 005f4769 sp (null) error 6 in libpango-1.0.so.0.2600.0[5da000+46000]
Jan 24 17:17:59 phoebe kernel: [  233.088150] pidgin[1753]: segfault at 4 ip 00284769 sp (null) error 6 in libpango-1.0.so.0.2600.0[26a000+46000]
Jan 24 17:23:33 phoebe kernel: [  566.672238] pidgin[1973]: segfault at 4 ip 00333769 sp (null) error 6 in libpango-1.0.so.0.2600.0[319000+46000]


I am a professional technician, so I have done the basic tests, RAM checks out, HDD should be good, it came out of my netbook that was operational before removal (also running 9.10). I have verified that the packages are installed correctly, and I have updated all packages, even going so far to use the Proposed and Unsupported updates. I am stuck guys.

Any ideas?

---

### Post by Barriehie on 2010-01-24
Try reinstalling the pango library.  I'm not running 9.1 so I can't supply a list of available packages to install via CLI.

Barrie

Edit: These are what I've got: libpango1.0-0  libpango1.0-common

---

### Post by Robyr on 2010-01-24
Thanks for the response! I guess I should have added, i have seen the same segfaults for libc, libapt (wtf?!) and pulse as witnessed above. Could I have just a really crappily downloaded ISO of 9.10? If it were only pango related segfaults I could understand, but this seems really pretty crazy. I thought it might be related to heat, but the cores are staying right at 40*C.... I am so at my wits end.

---

### Post by Robyr on 2010-01-25
Ok, that certainly did not work. Random friggin apps are still crashing. I am trying my hardest not to freak the fark out. Like the power manager? It failed with a libpango segfault. Firefox just ate it again. I don't know what else to check guys.

---

### Post by Saiko Berry on 2010-01-25
It looks like the evil hydra Pulseaudio is waterfalling errors through processes again.

---

### Post by Robyr on 2010-01-25
> **Saiko Berry said:**
> It looks like the evil hydra Pulseaudio is waterfalling errors through processes again.

You know, I wondered about that. pulse segfaulted out too, and i thought nothing of it. Then, just a second after i reinstalled pango and the like, it REALLY ate it. Dropped firefox, pidgin, and any widget or setting window i open drops immediately. Got any links to the pulse fixes (or attempts?)

---

### Post by Robyr on 2010-01-25
[23627.592666] gnome-power-sta[9619]: segfault at 4 ip 001d6769 sp (null) error 6 in libpango-1.0.so.0.2600.0[1bc000+46000]
[23770.104462] pidgin[7047]: segfault at 4 ip 0021d769 sp (null) error 6 in libpango-1.0.so.0.2600.0 (deleted)[203000+46000]
[23779.615362] pidgin[9664]: segfault at 4 ip 00324769 sp (null) error 6 in libpango-1.0.so.0.2600.0[30a000+46000]
[23904.174924] gnome-system-lo[9840]: segfault at 4 ip 00b73769 sp (null) error 6 in libpango-1.0.so.0.2600.0[b59000+46000]
[24559.727669] python[1544]: segfault at 2991a6e4 ip 00266fd1 sp bfb9be50 error 4 in libdbus-1.so.3.4.0[259000+37000]
[25391.522687] pidgin[9765]: segfault at 0 ip (null) sp b5d00560 error 4
[25571.663321] gnome-terminal[9908]: segfault at 10900 ip 004bfcf9 sp bfe02d0c error 4 in libX11.so.6.2.0[4b6000+12a000]

^^^ These just happened, literally minutes ago. If id open one, it would drop, then the terminal went. WTF is going on here guys? If PulseAudio has this many problems, it REALLY needs to be removed from the distro until further notice. This is unacceptable.

---

### Post by chewearn on 2010-01-25
> **Robyr said:**
> ^^^ These just happened, literally minutes ago. If id open one, it would drop, then the terminal went. WTF is going on here guys? If PulseAudio has this many problems, it REALLY needs to be removed from the distro until further notice. This is unacceptable.

I'm sure you are frustrated, but jumping to conclusion based on one liner from one person would not help you any quicker.  It might even lead you down the wrong path.

---

### Post by Robyr on 2010-01-25
> **chewearn said:**
> I'm sure you are frustrated, but jumping to conclusion based on one liner from one person would not help you any quicker.  It might even lead you down the wrong path.

Any ideas? I am out of them. PulseAudio sure is coming up in the error logs a lot, and I just got through reading an entire thread about crashes and lockups that pointed the finger directly at Pulse. What else am I to do man? It's 1AM on a monday, and this machine needs to be operational this morning. I didn't have these issues on my 9.10-powered Acer Aspire One, yet this Toshiba, which is beautifully supported out of the box (minus sound) cant seem to keep Pidgin open for more than 3-4 minutes. Firefox crashes at RANDOM. I dont even have to do anything but click on it. I have turned compiz off which was my only other idea, and it has not helped one bit.

---

### Post by D3V11 on 2010-01-25
did you install it from the live cd or update manager?

---

### Post by Robyr on 2010-01-25
Live CD. Desktop-x86. I have the Alternate ISO downloading now, just in case I have a corrupt ISO or some dumb crap, but I some how doubt this.

---

### Post by D3V11 on 2010-01-25
You said you're computer savvy, so i'm sure you know whether you need the 32 or 64 bit. Check the live disk for errors before you install it. There's an option for this when you boot the cd on alternate or desktop versions. The best disk to use is the cheap cd-r.

---

### Post by Robyr on 2010-01-25
Thats the one thing so far I haven't tried... I feel dumb now. Lemmie go slap that sucker in and see if she checks out. What if it does?

---

### Post by D3V11 on 2010-01-25
If it's jacked up then burn a new one. best to use a new cd-r. Or make a usb version to boot from.

---

### Post by Robyr on 2010-01-25
Well, I meant what if the disc gets the green light? Am I just hosed?

---

### Post by D3V11 on 2010-01-25
I'd try doing a reinstall if the disk checks out. It may have installed incorrectly. If that doesn't work try doing a hard reset. If neither of those help, it's either a hardware issue or software/hardware incompatibility. Maybe drivers?

---

### Post by Robyr on 2010-01-25
D3vil:

Disc had errors. I am currently burning the alternate ISO for a reinstall. I wish the integrity check was more verbose, however. It makes me wonder what was wrong with the other disc. Thanks a ton man, you must know how those 1AM Sundays are. Have to have this machine ready to go for work in the morning, got a few onsite visits to make, so I was getting pretty annoyed.

EDIT: Also, I had done a full reinstall, that's why I was like "WTF?" with all these errors. Again, thanks a ton for opening my eyes a little more to the tools I had in front of me.

---

### Post by D3V11 on 2010-01-25
anytime bro ;)

---

### Post by Robyr on 2010-01-25
Ok, reloaded with a confirmed good disc last night, thought the issue was solved. However, today I experienced the crashes and other issues again. What in the world is wrong with libpango/libglib? It happens whether or not compiz is enabled. I am at my wits end.

---

