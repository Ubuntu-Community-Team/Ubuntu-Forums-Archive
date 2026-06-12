---
title: "High CPU usage while watching video"
date: 2006-01-27
forum: General Help
---

### Post by madtinkerer on 2006-01-27
Hi all,

I'm finding my cpu usage is rather high while watching dvds or other video files.  CPU usage sits about 30% while watching these files.  It also spikes every few minutes, to the point where it stops the video for a second or two.  When I used to run the same hardware in Gentoo, my cpu usage was about 10-15% with no spikes.  I've got dma set, but I can't think of any other issues that are important.  Here are my system specs:

AMD64 3200 (Kubuntu in x86 mode(
1gb ram
nvidia 6600gt vid card
ata133 hdd

Any suggestions on how to make it run more efficiently?

Thanks

---

### Post by ]Nbx*cmD[ on 2006-01-27
Which player do you use?

---

### Post by madtinkerer on 2006-01-27
Mplayer.  But I've tried other players with the same results.  I've tried tweaking my hdparm settings with no avail.

---

### Post by ]Nbx*cmD[ on 2006-01-27
[QUOTE=madtinkerer]Mplayer.  But I've tried other players with the same results.  I've tried tweaking my hdparm settings with no avail.[/QUOTE]

Wow it's so strange.
I use Mplayer on a AMD Athlon XP 2400+ with a poor Gforce2MX (32Mb) and 512 Mb RAM and it works perfectly :-k 
I was about to tell you to install Mplayer because I've had some speed problems with Xine but I see you use it already so... i'm sorry i don't have an idea of what the solution could be :(

---

### Post by dresnu on 2006-01-27
I think it might have something to do with what's called video overlay. Try searching the forum and try putting this line 
Option           "VideoOverlay"          "on"
in your xorg.conf under the device section.

---

### Post by bernardfrancois on 2006-01-27
For the best performance, use the xv video output plugin. Or vx, dunno...

Start gmplayer with: gmplayer -vo vx
or
gmplayer -vo xv

I can't test whether it's xv or vx right now,  I don't have mplayer installed for the moment...

---

### Post by johannes on 2006-01-29
I'm not sure if it helps, but have you installed the latest nvidia drivers?

---

### Post by bernardfrancois on 2006-01-29
The specs of his computer are high enough to watch it without those drivers (I have an older nvidia card and older processor and it works fine here without the drivers from nvidia).

There's al lot of information in the html manual of mplayer (dunno if that's installed when installing a package from synaptic... I know it's in the tarball...).

---

### Post by gamma on 2006-01-29
I was trying to get away from nvidia's driver and sticking with the opensource nv one, but I'm having the same issue. Xorg uses 20% CPU useage and  Kaffeine will use another 20%. On nvidia X uses 4% and Kaffeine uses 15%. The fan spins constantly on the laptop playing video with nv too.

---

### Post by Jojan on 2008-03-20
I have the same issue, and it's just started one or two weeks ago. This is on my stationary computer, specifics in the signature. It's pretty irritating since the fan goes all fast alos, wich makes the computer make more sounds. Sometimes I can just pause to get it quiet, and sometimes I need to pause and change desktop for a second.

---

