---
title: "No sound from WMVs"
date: 2005-02-22
forum: General Help
---

### Post by NeoChaosX on 2005-02-22
I can't seemingly hear WMVs anymore. I can play QuickTime, Real, DivX, XviD and all sorts of videos and I can hear audio from them, but I can't hear the audio on Windows Media vids. Have w32codecs installed, and tried playing vids in gxine, and totem-xine. Anybody know what I could do?

---

### Post by NeoChaosX on 2005-02-25
ALso, I dunno if this has to do with the problem, but now I keep getting this error when I try to open a WMV in Nautilus:

[i]The filename "halo2_1440x1080_23.976_9m_k60_b10_q100_p100_440_48_16_6.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/i]

Does anyone else have either of these problem when playing WMV files?

---

### Post by lucan on 2005-02-26
hi,
i just install ubuntu into my laptop. and  i have the same problem. ubuntu just don't play file with *.wmv.

---

### Post by NeoChaosX on 2005-03-03
lucan: Check the WMV files and see if they're encoded in WMV7 (gxine can usually tell you this while it's playing the file). I've found anything encoded in WMV8 or 9 works, while WMV7-encoded stuff has the audio problems I was talking about.

As far as the opening it in Nautilus problems go, just open the file from the player instead of the file browser. GNOME has some serious problems identifying file types.

---

### Post by bigzak on 2005-03-03
[QUOTE=NeoChaosX]lucan: Check the WMV files and see if they're encoded in WMV7 (gxine can usually tell you this while it's playing the file). I've found anything encoded in WMV8 or 9 works, while WMV7-encoded stuff has the audio problems I was talking about.

As far as the opening it in Nautilus problems go, just open the file from the player instead of the file browser. GNOME has some serious problems identifying file types.[/QUOTE]
 I've noticed this too. On my system I do get sound, but it's only perhaps one 'blip' of noise every second or so, all broken up and unintelligible.

---

### Post by kaha on 2005-03-08
[QUOTE=bigzak]I've noticed this too. On my system I do get sound, but it's only perhaps one 'blip' of noise every second or so, all broken up and unintelligible.[/QUOTE]
Cool, thought I was the only one.   8-[

This is using Hoary, BTW.

---

### Post by bored2k on 2005-03-08
[QUOTE=kaha]Cool, thought I was the only one.   8-[

This is using Hoary, BTW.[/QUOTE]
 Have you  guys/gals/UFO's installed w32codecs?

If not, add this to ur /etc/apt/sources.list [repositories in synaptic]

# Marillat's Sources (MPlayer, w32 video codecs, etc.)
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

This should make everything work now .

If you're using Totem player, Clic Edit> Preferences> Add propietary plugins

and make a system link or just copy paste the codecs downloaded to the directory wich opened [/home/user/.gnome2/totem-addons].


Btw, the codecs are usually placed in /usr/lib/win32/ if downloaded thru marillat's .


As a complimentary option, download and try vlc .

---

### Post by dcstar on 2005-03-08
[QUOTE=NeoChaosX]ALso, I dunno if this has to do with the problem, but now I keep getting this error when I try to open a WMV in Nautilus:

[i]The filename "halo2_1440x1080_23.976_9m_k60_b10_q100_p100_440_48_16_6.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/i]

Does anyone else have either of these problem when playing WMV files?[/QUOTE]
Yes, I have seen this message.

Select the "Open with" option to view the file in your player, I use Xine myself.

And yes, the W32codecs are essential.....

---

