---
title: "For the DEVS - MSI 890FXA-GD65"
date: 2011-06-21
forum: General Help
---

### Post by stephen730 on 2011-06-21
Okay, I am new to this forum and would like to post (as was recommended) some information about my setup. I am currently using a MSI 890FXA-GD65 board, 6Core AMD 2.8GHz phenomII (true 6 core not unlocked) 8GB Ram (currently set to 667MHz) a MSI Twin Frozr II 460 nvidia GTX (fermi) and a standard SATA 6GBs hard disk.

For the installation, I had to choose the ACPI workaround option otherwise I get a blinking cursor and no boot. Then I had to manually edit the grub file to turn off acpi (using the command line to update it within the grub file, it tells you what command to press when you edit the grub conf file.) So now it boots. So with my current board, we have to turn off ACPI because it won't boot. It won't even friggen boot to that LINUX Live cd that comes with the board!!! Same thing, blinking cursor which means out of sync. 

Whew, what an ordeal to find all this out but hey, thats half the fun to me... 

Now, i have a problem with my audio which is a Realtek HD audio onboard. It was crackling. I found the fix that was recommended by reverting the ALSA driver (google it, you will find it all over here) because my sound was crackling and popping and hissing and all that stuff.

All I did to fix it was click the sound icon, click sound preferences, and when it opened up, it was automatically on the APPLICATIONS tab. Once that window popped up it worked perfectly while I was in the middle of a song with last.fm and it seems to be working. So thats fixed, i didn't touch any sliders or mess with that dialog at all.

So now, I'm listening to Soulwax - Compute and just like the song says, "EVERYTHING SEEMS TO WORK FINE"! Its not popping or hissing. 

The popping and hissing seems to be too much voltage or feedback from something. I've also disabled my HDMI port to my monitor for sound because I am an ANALOG sound guy, i dislike digital sound and perhaps that is also a fix.

Running 11.04 ubuntu 64 bit. Email me, DEVs, if you need any input on this issue and I would be happy to help you out as much as I can. Regular users, sorry but I have no idea other than what I stated to fix it so I can't trouble shoot you. 

Hope this helps

---

### Post by stephen730 on 2011-06-21
Okay... Just after I wrote this, I close out my sound preferences box and guess what, 5 - 7 seconds later, the crackling is back. So I open sound preferences back up, it goes away. Close out sound preferences its back.

So thats what's up. I leave sound pref open and the crackling hissing popping is gone. So now I listen to everything with that box open. CRACKERS AND CHEESE!!!!!!!!!!! hahaha, help me someone! I'm close!

---

