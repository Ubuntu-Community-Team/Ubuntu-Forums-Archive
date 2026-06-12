---
title: "Commands ending in %d etc."
date: 2006-01-27
forum: General Help
---

### Post by Farthing-or-less on 2006-01-27
What does the %d at the end of many run commands mean, and how do you know whether to put %d, %h or whatever for each application you're trying to run?


Dumb queestion, i guess, but I've never figured it out.

---

### Post by Ocxic on 2006-01-27
what command are you trying to run? I've never had to type such a thing while giving any commands.

---

### Post by Farthing-or-less on 2006-01-27
Hmmm... I should have mentioned that. I was referring to run commands for applications. For example, the command for Sound Juicer is listed as sound-juicer -d %d in the Removable Drive and Media Preferences. That for Totem is totem %d, and then that for digital camera connections is gnome-volume-manager-gthumb %h.  If I check the Preferences for the Firefox panel launcher, the command is given as firefox %u. That's what I mean.

Are those % bits necessary? If I run Sound Juicer from the terminal with the %d, there seems to be no difference from when I run it without %d.

---

### Post by public_void on 2006-01-27
%d is a format string for a decimal in C, others are listed [here]("http://www.its.strath.ac.uk/courses/c/section3_18.html#SECTION00018000000000000000").  I'm also curious by what you mean, what sort of commands does that happen with?

EDIT: You just posted before me. Oh, I see what you mean.

---

### Post by Farthing-or-less on 2006-01-27
Hmmm... that seems to be different from what I mean, but I  could just be misunderstanding what those % at the end of the run commands are. As i said, I can't see any difference when i run the apps by typing the commands with or without the %*. But if there is no difference, why are they preset that way in the launchers and such? 

Other examples are the commands listed for the various launchers in the Menu Editor. OpenOffice Writer, for example is ooffice2 -writer %U, The GIMP is also listed as gimp-remote-2.2 %U, while Sane is simply listed as xsane.

I am a bit bewildered by these mysterious %s.

---

### Post by tukuyomi on 2006-01-27
[QUOTE=Farthing-or-less]If I check the Preferences for the Firefox panel launcher, the command is given as firefox %u.[/QUOTE]
Maybe if you drop an 'http://address.org' URL/link on it, it will launch firefox with 'http://address.org' as an argument.

[QUOTE=Farthing-or-less]For example, the command for Sound Juicer is listed as sound-juicer -d %d in the Removable Drive and Media Preferences.[/QUOTE]
The same for sound-Juicer; you connect a removable media (*/dev/hdd*, for example), gnome loads it in *%d* and launches the command *sound-Juicer -d /dev/hdd* (*sound-juicer --help* for the command-line options) ;)

---

### Post by Farthing-or-less on 2006-01-28
Ah... So there's the question? You said, Gnome loads it in %d.  What is %d?  What would %h be, and so on. I guess that is the heart of my misunderstanding... or rather lack of understanding.:-D

---

### Post by tukuyomi on 2006-01-28
I guess *%d*, *%h* etc are temp variables just needed to launch the command (%d for device, %h for...?, %U for URL and so on).
' *%variables* ' syntax is used in various programming languages to create variables used by your program.
There is probably a daemon who listens when you connect a removable media (say */dev/hdd*).
The daemon reads */dev/hdd* (the characters string actually, not the content of it) then stores it in the variable *%d*.
Then gnome launches the command *sound-juicer -d %d*, replacing *%d* with */dev/hdd* --> sound-juicer -d /dev/hdd.
But I'm not an expert, if someone can correct me ;)

---

