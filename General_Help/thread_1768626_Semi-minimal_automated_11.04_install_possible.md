---
title: "Semi-minimal automated 11.04 install possible?"
date: 2011-05-27
forum: General Help
---

### Post by .psd on 2011-05-27
Suggestions on ways for a complete n00b to install 11.04 semi-minimally but still as automated as possible. Looking to install without the following programs, or anything that relies on them, or anything they rely on.

unity (newest stable gnome instead)
libreoffice
tomboy notes
transmission
games
ubuntu one
empathy
onboard
banshee
printing
gwibbler
orca magnifier
movie player
[ no banshee or movie player assumes VLC can handle both, otherwise rhythmbox and keep movie player ]
simple scan
sound recorder
evolution
pitivi

Not looking for other distros or non-answers, just ways to minimize a somewhat automated fresh install. Also if there's anything you would consider bloat that could be eliminated from install, that would be neat. I mean automated as in it finds drivers and updates and installs everything automatically as opposed to me doing it one piece at a time at the command line a la [minimal install]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

---

### Post by linuxinstalledfromhdd on 2011-05-27
Open Ubuntu Software Center and search for each of those titles.

For any that you can not find use:

sudo apt-get --purge remove <nameofapplication> 

That's it.

---

### Post by LowSky on 2011-05-27
Do a normal install... then remove the apps then install an app Ubuntu Customization Kit. It will create a live CD of the current environment.

---

### Post by .psd on 2011-05-27
Alright I got that.

Are there any ways to customize an install on that level? To prevent those things and their dependencies and whatnot from ever installing in the first place?

I don't have a problem reinstalling, in fact I'm about to do it as soon as I can get someone in the community to actually answer one of my questions lol instead of offering alternatives. You guys are really strongly opinionated. It would be even cooler to customize my own install CD and see how light I can make ubuntu and the install, but not too light to make it no longer ubuntu, or too much to make it unnecessarily complicated.

@linuxfromhdd I don't exactly know all the bloat that's installed which is why part of my question was to gather what other people thought was bloat which was also removable.

---

### Post by .psd on 2011-05-27
Also, I just learned there's a distinction between desktop environments, windows managers, and file managers. Can I have several of each installed and switch among them?

---

