---
title: "Kubuntu Dapper not quite ready yet?"
date: 2006-04-02
forum: General Help
---

### Post by rverrips on 2006-04-02
Hi

Been happy with Breezy and Gnome but decided to try a fresh install of Kubuntu Dapper Flight 6 on my [Laptop ]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1642WLMi")

KDE came up ok, however like in Ubuntu Breezy X.org needed 915resolution to get the correct 1280x800 displaymode ... no worries installed it, but now everytime when I goto KControl and Display properties I get a crash message ... 

Then (and this is really weird) - I have two nic's (Wireless eth0 and Wired eth1) - I used eth0 during install and everying went great, but after installing eth1 just won't come up - I searched the forums and everyone always seems to have trouble with the wireless port, never the wired one?  Weird hey?

Also related to the 915resolution thing, in Breezy with Gnome when I hibernate (ACPI 4) the laptop, she goes down fine, but fails during startup and simply creates a new session, but with the incorrect resolution of 1024x768 (probably why she crashed at startup?) - However, sleep/suspend (ACPI 3) worked fine and not too much of a drain on the battery:  Suspended her for 9 hours once and only used up 5% battery power, and she starts up with in 3 seconds right where I left off.  

However, with KLaptop/Kubuntu Dapper Flight 6 Hibernate does nothing, and suspend brings up the screen-saver???

And yes, why isn't the Matrixgl screensaver available in Kubuntu!? (The nice one where you "float" through the Matrix 'gliphs, not the one on KDE-look that only has pictures of the characters made up out of Matrix 'gliphs?

Anyway, I understand that Kubuntu Dapper Flight 6 is still in testing and I shouldn't complain - With a bit of work all the above issues could be resolved, and it's all because of my hardware, etc. etc. and that's why it's still in the testing phase ...

But what was really worrying is this: I installed Ubuntu Dapper Flight 6 and all "Simply worked" 100% - I still needed 915resolution, but after that X and Gnome had no prob's (and no crashes) - Both NIC's worked fine, the ACPI suspend 3 worked and although gnome-screensaver has replaced xscreensaver the Matrixgl screensaver is still there ... 

So now here's the funny bit, in Ubuntu I did an "apt-get install kubuntu-desktop" and hey, both nic's now work ok with KDE, and the KControl issues seem to be KDM's fault - KDE under GDM is fine.  Suspend still works, and with KDE I can turn off the KDE Screensaver and use xscreensaver (probalby even try gnome-screensave if I want to)

**Displaimer: Please realise I'm not comparing KDE to Gnome, but rather the installation and "out-of-the-box" hardware support of Ubuntu Dapper Flight 6 vs. Kubuntu Dapper Flight 6... **

Now here's my question (thank you for being patient): Is it normal for Ubuntu and Kubuntu to give such different results after installation and will it be that way when 6.06 goes live?  My personal experience is that Ubuntu Dapper is fairly stable on my hardware, where-as Kubuntu is the total opposite and still needs some work - Is it just me and my hardware or is this a general perception?

---

### Post by njf on 2006-04-03
Ready? No.

Kubuntu needs your bug reports.
[https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

---

### Post by nickle on 2006-04-03
Grant it these are not final releases, but it does not bode well for the Ubuntu/Kubuntu distro overall. The Gnome bias in Ubuntu is indeed a case of being simply blind in one eye. If the Unbutu/Kubuntu distro does not address this, it will mean many KDE folk will simply move on to better supported distros....

Howeverl lets await the final release before jumping to such conclusions...

---

### Post by rverrips on 2006-06-09
Hiyee

Follow-up to this posting:  I upgraded the HDD on my laptop, and decided to try an install Kubuntu 6.06 now that it's finally released, and ....

[LIST=1]
[/LIST]
[*]Wired and Wireless worked great, in unison with KNetworkManager
[*]915resolution is still needed (as with GNOME/ubuntu), but hibernates/suspends perfectly now
[*]Sadly, I still can't find the matrixgl screensaver for KDE/kubuntu yet though :-(

Cool stuff!

---

