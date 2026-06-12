---
title: "Unexpected inconsistency"
date: 2011-09-18
forum: General Help
---

### Post by leviathan8 on 2011-09-18
Hello. 

I have experienced a rather strange problem today after some file management. Here is the story:
Just an ordinary day, browsing and listening to music. I was thinking about adding some new songs to my playlist, so I mounted an NTFS partition with music on it. I copied approximately 150 MB worth of music to my /home partition. I then cleaned up some unused files from my downloads directory. After that I copied my new music files to my phone and flash drive. So far so good. Having noticed that there is a game left unplayed for a while, I decided to uninstall it, using the shell script it provided. The game was named Heroes Of Newerth. At the end of deletion, the script reported that there was a problem with uninstallation, but provided no other information. The directory of the game was located in my home folder so I deleted the left content manually.  Later, while I was playing some flash games, I noticed that my music player suddenly stopped after changing a song. I thought there wasn't anything wrong, probably a database error.
But then it happened again. There was a particular song whose content resources were unreadable, as reported by Rhythmbox. I thought the song was just corrupted so I deleted it permanently. 

Short after that, everything on my root partition became unreadable. I opened Thunar (having it cached), and every folder and file had an X below it, representing that it can't be read. It was also impossible to open any other applications.
After that I rebooted my computer, and I've been thrown into a console. There were a lot of verbose messages regarding to problems with blocks, inodes and such. Below are some pictures I managed to take on the fly. Please have a look at them so you can understand the problem better:

[http://i.imgur.com/BgiXS.jpg](http://i.imgur.com/BgiXS.jpg)

[http://i.imgur.com/Bm1k1.jpg](http://i.imgur.com/Bm1k1.jpg)

[http://i.imgur.com/aXwEg.jpg](http://i.imgur.com/aXwEg.jpg)

[http://i.imgur.com/sBiAD.jpg](http://i.imgur.com/sBiAD.jpg)

[http://i.imgur.com/Ux97V.jpg](http://i.imgur.com/Ux97V.jpg)

Note: I have the AHCI option enabled. It is also possible that the hard disk is starting to fail, because I had some boot failures recently and the Raw Read Error Rate as mentioned in SMART tests is at a pre-fail value.
Here are the SMART test's result: [http://pastebin.com/raw.php?i=y8acFVja](http://pastebin.com/raw.php?i=y8acFVja)
Also, a few weeks old surface test results, using HDScan: [http://i.imgur.com/VM2zD.png](http://i.imgur.com/VM2zD.png)

I'm sorry for having the pictures flipped, but it is late and I have school tomorrow. I will provide you tomorrow with more information and search for log files. Any help is truly appreciated.

---

### Post by leviathan8 on 2011-09-19
Bump.
While I was listening today to the new music I copied on my phone, I noticed that a few songs have missing bits (skipping for a few seconds) and others contain, at a particular time, a totally different song embedded into them, that last 30 seconds, but after that the original song plays again. :confused:

---

### Post by diagram30 on 2011-09-19
No help can be given anymore, just by looking at that smart test which is a few weeks old it was already obvious that your disk drive was already good to throw in the trash bin. 
Sorry for your data!

---

