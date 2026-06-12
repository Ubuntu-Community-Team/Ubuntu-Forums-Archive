---
title: "Samsung YP-K3 MP3 player"
date: 2010-07-27
forum: General Help
---

### Post by big-ted on 2010-07-27
Hey guys, my first post here after using at as a resource for so long, so be nice. I searched!

I am trying to use my Samsung YP-K3 player with Ubuntu 9.10. Many people report that Ubuntu fails to recognise similar players and some fiddling with Amorak is necessary. However, my system recognises the player fine, and I can copy files to it without any difficulties. However, the player itself fails to recognise the files that are copied to it via Ubuntu. It will play the files that were previously copied to it via Windows fine, and I can go back and copy edit the playlist in Windows and everything works accordingly, it just seems Ubuntu is copying the files over in a non-supported format or something, which is weird, because they're all just standard MP3 files, many of which were originally created under Windows...

Any help greatly appreciated!

---

### Post by Namesake on 2010-07-30
I have exactly the same problem; any responses would be really appreciated from me too!

---

### Post by big-ted on 2010-08-11
Bump.


I'm beginning to think it's something to with the Ext4 format used by Ubuntu 9.10. I'm currently using an Ext file reader under windows and copying the files across. A pain in the *** to say the least!

---

### Post by IcarusR on 2010-08-21
Copying files from an ext4 filesystem to your mp3 player will not change the file format.
Exactly what are you doing to the files in windows to get them playing on the player ??

Could possibly be an ownership issue.

---

### Post by big-ted on 2010-08-23
[QUOTE=IcarusR;9748211]Copying files from an ext4 filesystem to your mp3 player will not change the file format.
Exactly what are you doing to the files in windows to get them playing on the player ??

Could possibly be an ownership issue.[/QUOTE


The only solution I've found so far is to use Ext2Fsd (in Windows XP) to convert to NTFS format before copying them across from Windows, so what you're saying would agree with my theory. In order for the player to recognise the files, they must first be converted to NTFS file format using some other software. I think I'm going to see if I can convert the files to NTFS format in ubuntu before copying them over. That way I can test my theory...

---

### Post by big-ted on 2010-10-23
Ha! Solved!

installing the appropriate MTP packages:

mtp-tools
mtpfs
libmtp8

enabled me to transfer files from Rhythmbox. It was a little quirky in that the player must be connected after starting Rhythmbox for it to be recognised. More importantly, I was getting several error messages with the transfer of each file, despite transfer being executed successfully. Particularly annoying for batch transfers.

Switching to Banshee media player appears to have solved both the above issues, and allows the device status (free memory etc) to be reported also.

I also had one internet radio station (CBC Canadian songwriters) I could never get working in Rhythmbox but it seems fine in Banshee. Bonus!

Happy! :)

---

