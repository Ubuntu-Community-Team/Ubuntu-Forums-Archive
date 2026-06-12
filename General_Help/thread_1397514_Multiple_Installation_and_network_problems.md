---
title: "Multiple Installation and network problems"
date: 2010-02-03
forum: General Help
---

### Post by ShadowMosesGreen on 2010-02-03
[FONT=Times New Roman][SIZE=2][SIZE=3]I'm trying to install wine and as always I follow someone's instructions step by step and I can't get past step one. I'm trying to install Wine. I go to applications>terminal and type in "sudo apt-get install wine." Then it ask for [sudo] password for caleb. Right here is the problem.  I type in the password and it says that it can't find "package wine." I have wine-1.1.33.tar.bz2, but I have no idea how to run it. I use the mounting application and nothing changes. It'll just open up a folder as if nothing was mounted unlike daemon tools where it recognizes it as a cd in the drive and does an auto run. I can't do auto run on the bz2 file. All seven of the tutorials on youtube that I tried yielded no results. Even though they have 9.10 (as do I) they have things that they claim are stock, and yet mine doesn't have them. How on earth do I install Wine?

Also, when I go into the Software Center, NO software can be installed from there. It says the following for every program:

"Wine Microsoft Windows Compatibility Layer

Not available for your hardware architecture.

Lecence: Open Source

Price: Free

Canonical does not provide updates for Wine Microsoft Windows Compatibility Layer. Some updates may be provided by the Ubuntu community."
Also, I am unable to go online in Ubuntu, so no suggestions about downloading something. All of this that I am doing is just so I can have Ubuntu recognize my wireless card so I can go online with it.

Again... how do I install Wine?

Now the network problem.
I am unable to access the internet because I am stuck at step one. I need to enable the drivers, but when I do the driver search, a window pops up saying "No proprietary drivers are in use on the system."  It doesn't recognize anything.  It is the same wireless card I am using to access the internet on this computer. How can I go about making it realize there is at least a piece of hardware installed?[/SIZE]
[/SIZE][/FONT]

---

### Post by gmargo on 2010-02-03
> [FONT=Times New Roman][SIZE=2][SIZE=3]All of this that I am doing is just so I can have Ubuntu recognize my wireless card so I can go online with it.
[/SIZE][/SIZE][/FONT]If I'm reading you correctly, this an XY problem - you're asking about Wine but you're really trying to solve an unrelated problem with your wireless card.

You might find better help over in the Networking & Wireless forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Unless I'm totally misreading and you really do care about Wine, in which case there is a Wine forum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by ShadowMosesGreen on 2010-02-03
> **gmargo said:**
> If I'm reading you correctly, this an XY problem - you're asking about Wine but you're really trying to solve an unrelated problem with your wireless card.
 
You might find better help over in the Networking & Wireless forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
 
Unless I'm totally misreading and you really do care about Wine, in which case there is a Wine forum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
 
I can see why you're confused. I was unclear about it. I'm trying to install Wine because I want to be able to install my wireless card driver because the autorun is an exe and I need Wine in order to do that. And once I get the wirless card driver to install, maybe Ubuntu will recognize it and not say that there are no drivers to enable. I forget exactly what it says, but when I do a driver search, it says something along the lines of "No priority drivers found" I forget exactly what that "p" word is, but it's a word starting with "p." "No 'p------' drivers found." You might know what I mean. I'd check, but I'm in classes right now. I'll check out those two links you posted.

---

### Post by gmargo on 2010-02-03
[QUOTE=]autorun is an exe [/QUOTE]

There's an off chance that "cabextract" can get what you need from the .exe file.

---

### Post by ShadowMosesGreen on 2010-02-03
> **gmargo said:**
> There's an off chance that "cabextract" can get what you need from the .exe file.
Alrighty. How will I go about retrieving it and installing? If you have a link to answer the question, that'll be fine.

---

