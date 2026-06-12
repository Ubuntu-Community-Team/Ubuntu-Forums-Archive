---
title: "Negative coloured images in Firefox"
date: 2011-05-07
forum: General Help
---

### Post by ENatanael on 2011-05-07
Hi!
I wasn't sure where to post this so please move it if it would fit better somewhere else.

Since I upgraded to Natty, some images appear in negative colours in Firefox, but not all. For example, photos on Facebook have negative colours, but not the thumbnail versions of the profile pictures do not. I have tried reinstalling Firefox in Synaptic to no avail.
On another partition I have an installation of openSUSE 11.4 sharing the same /home (and therefore all Firefox settings etc), but no negative colours.

---

### Post by Paddy Landau on 2011-05-07
I wonder if there is some conflict in the settings between your two operating systems?

(Incidentally, reinstalling Firefox will make no difference. In Windows, that might reset its settings, but in Linux, settings are stored in a folder in your home directory.)

To reset your settings, you need to delete your Firefox directory. Do this:


[LIST=1]
[*]Close all open Firefox windows.
[*]Firefox stores its settings in a directory in your home called [FONT=Courier New].mozilla[/FONT]. Rename it to, say, [FONT=Courier New]backup.mozilla[/FONT] (open Nautilus, press Ctrl-H to see hidden folders, and rename the directory).
[*]Run Firefox and check whether the problem recurs.
[/LIST]

(To restore your settings, delete the newly-created [FONT=Courier New].mozilla[/FONT] and rename [FONT=Courier New]backup.mozilla[/FONT] back to [FONT=Courier New].mozilla[/FONT].)

---

### Post by ENatanael on 2011-05-07
I tried "resetting" the settings as you described, but the problem remained. The reason I reinstalled the firfox package was because those files are specific to Ubuntu, not shared with openSUSE so I thought there might've been some kind of problem with the upgrading (I don't really know the inner workings of the OS).

The problem started before I installed openSUSE. I used to have Fedora 13 (or was it 12?) on that partition (it's for trying different distros), but I had not started it since before the upgrade of Ubuntu.

---

### Post by Paddy Landau on 2011-05-07
Sorry, I'm struggling to understand what could cause such a problem. It's not much of a solution, but you could try Chromium instead?

---

### Post by ENatanael on 2011-05-07
I already have Opera installed. No negative colours there.

I really appreciate that you're trying!

---

### Post by Paddy Landau on 2011-05-08
Well, sorry I couldn't help. Let's bump this thread and hope someone with a better idea sees it.

---

### Post by no2498 on 2011-05-08
is your adobe flash up to date
if you did not use flash aid to install flash
try installing grease monkey
i had to do it to get flash to work on 10.04

---

