---
title: "Freezing computer"
date: 2012-09-11
forum: General Help
---

### Post by billcauley on 2012-09-11
My computer, an older Pentium 4 with 1GB RAM started freezing and requiring restarts.  It happened at random times, no matter what was being done.  I'm using Ubuntu 12.04 in classic mode, and keep it upgraded daily.  After days of troubleshooting everything imaginable, I decided to really read the code on the black screen when the computer freezes.

Two things got my attention. 1) the computer wasn't correctly identifying the server and was using a default number (so I added a correct MAC address); this wasn't a big deal, and **2) probably the main cause of the freezes, was that the swap number in the BIOS video setup was set too high.**  **While fiddling around a few weeks ago, I decided that changing the maximum possible amount of RAM to be used for integrated video from 512MB to 1024MB might be a good idea...WRONG MOVE.  What that did was to use a much too large portion of my memory for video, and in so doing caused a memory logjam and subsequent freeze.**

Now, since I switched it back to 512MB default, it's been more than two days without more freezing.  My computer is back to running great! Yeaaa! But hey, that's what Linux is for; people who like to fiddle with stuff.:)

I read the postings here daily, and have noted others with freezing problems. Hopefully this helps somebody.  Remembering that when things goes bad, it's often a simple reason, yet we think the exotic for a fix.

---

### Post by greatsirkain on 2012-09-11
mine kept freezing because of the amount of unwanted/unneeded startup programs (worked loads faster from a live disk) but when I clicked on the startup applications it just showed the make a sound at startup thing then someone said

 sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

to display hidden startup items, can't remember who posted it but it sorted my computer out so thnx :)

edit: it was [kgarbutt]("http://ubuntuforums.org/member.php?u=719803"), cheers!

---

### Post by Genkakuzai on 2012-09-12
I recently installed Ubuntu Studio 12.04 onto my new Toshiba laptop (Satellite P855-S5200) and experience freezing every once in a while. It completely locks up and I'm forced to do a hard shutdown (the clock stops counting seconds). Any reason why this could be happening?

I'm fairly comfortable with linux but I'm not as adept as I am with Windows.

Thanks in advance.

---

