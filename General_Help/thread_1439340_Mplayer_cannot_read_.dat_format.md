---
title: "Mplayer cannot read .dat format"
date: 2010-03-26
forum: General Help
---

### Post by sportspool7 on 2010-03-26
Why format .dat is not read in MPlayer? What if I want to convert the format. dat to. avi using Winff?

Can anyone help me? I use Ubuntu now 9.10 and I was the new user in Ubuntu.
To obtain a statement about my problem more clearly, please see the pictures that I have attach it.

---

### Post by slakkie on 2010-03-26
Looks like vista to me mate. Perhaps join a Windows forum.

If it is an Ubuntu box, do the following:

file /path/to/file.dat and tell us what that tells you.

---

### Post by sportspool7 on 2010-03-27
> **slakkie said:**
> Looks like vista to me mate. Perhaps join a Windows forum.

If it is an Ubuntu box, do the following:

file /path/to/file.dat and tell us what that tells you.

My answers can be found on the pictures that I attach the question before this. I have to try it in a way that you taught me.

---

### Post by Helkaluin on 2010-03-27
> **slakkie said:**
> Looks like vista to me mate. Perhaps join a Windows forum.
It could well be Linux. Remember the wonders of Emerald and blurring done in Compiz.

As for the problem, it clearly suggests a permission problem, so the obvious thing to do will be:
```
ls -l
```
Or just right click and do 'properties' in your graphical file manager and check the permissions tab.

Then we can go from there.

---

### Post by sportspool7 on 2010-03-29
Its really working and how does I convert my video using Winff application?

---

### Post by Helkaluin on 2010-03-30
Advice: try asking this irrelevant question in another thread and mark the current as [SOLVED].

---

### Post by sportspool7 on 2010-03-30
I do not understand how you taught me. Can you taught me the easy way because I recognize the new Ubuntu,

---

### Post by amit.neo2000 on 2010-03-30
why dont u try vlc media player.
it plays _almost_ all the media files which u want.
i hardly get any error like this in it...

---

### Post by sportspool7 on 2010-04-04
On how want play file .dat the, already finished but present problem, how I want convert .dat to .avi?

---

### Post by jrz on 2010-06-03
I use ffmpeg, you might have to go to synaptic and install it.
Bring up a terminal screen, and cd to the directory containing the .dat file(s) you wish to convert, and use the following command, replacing {filename} with the actual filename.

ffmpeg -i {filename}.dat -target vcd {filename}.avi

---

