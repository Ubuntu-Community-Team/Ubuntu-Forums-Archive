---
title: "Help! Ubuntu can &quot;see&quot; music files from my windows partition"
date: 2009-09-23
forum: General Help
---

### Post by ladavis89 on 2009-09-23
Hi everyone, 

I have been searching forums and google and can't seem to find my issue anywhere.  I recently installed ubuntu on a hard drive where i also have XP installed.  Its working perfectly except now i cant access the music i have saved on my ntfs partition.  When i first started using ubunt i had amarok find the local collection from the windows partition and it worked fine. When i booted up my machine one day, my local collection dissapeared and when i went to look for the files in the file browser, i could not see them.  It said the folders were empty.  I can access the containing folders of my music, but not the files themselves.  I can access all other files from that partition, just not my music.  Its frustrating me because i need my music!!! Why would it all of a sudden do this?

Thanks for the help in advance! 

Landon

---

### Post by tgeer43 on 2009-09-23
Well, since you didn't mention it I guess someone's gotta ask.
Are the files still actually there? Can you see them from Windows?

tgeer

---

### Post by A_Fiachra on 2009-09-23
You probably unmounted your NTFS partition when you rebooted.

What do you see when you type:

```

df -h

cat /etc/fstab

cat /etc/mtab

```

??

---

### Post by fuzzyk.k on 2009-09-23
if the files are really there the second answer is the most likely true

---

### Post by blackened on 2009-09-23
A dirty shutdown of XP could also be keeping the partition from mounting properly. To fix it, boot into XP and do a clean reboot into Ubuntu.

---

### Post by tgeer43 on 2009-09-23
From the OP's original message:
> I can access all other files from that partition, just not my music.So apparently it's mounted.

tgeer

---

### Post by fuzzyk.k on 2009-09-23
ok , am thinking crazy here , don't know bout amarok but some music managers have to option to move your music files , did you by any chance tick that ?

---

### Post by tgeer43 on 2009-09-23
You may be on to something there, fuzzyk.
If the OP would just answer my first question to him it would sure eliminate a lot of guessing on our part.

Being a new Ubuntu user, he's probably used to waiting days for a reply to his Windows problems. Wait until he sees 7+ replies in the first 2 hours! :wink:

tgeer

---

### Post by ladavis89 on 2009-09-23
Wow that was quick! Yes the files are actually there.  They just don't show up when I navigate to them in the file browser.  My windows partition is mounted also.  Im about to boot into XP and reboot into ubunto to see if that works.  

Thanks for the quick replies!

---

### Post by ladavis89 on 2009-09-23
ok now im freaking out! I booted into my windows partition and just to be sure i went to check to see if my music files were still there but they are missing!!  It's just the music files though.  The album artwork is still there along with its containing folder.  In windows i searched for any music that is on the hard drive and none of it is showing up anywhere!  I had over 30 GB of music! Would amarok have moved them somewhere or erased them?!  I have no idea what could have happend to it!

---

### Post by rodh on 2009-09-24
JUST A THOUGHT HERE. When you look for the music in XP did you look for ALL file types.  *.*

---

### Post by tgeer43 on 2009-09-24
Amarok shouldn't have moved or deleted them unless you instructed it to do so. My guess is that they *have* been moved, probably to a location on your Ubuntu partition and that's why Windows is not finding them.
Try doing a file search from within Ubuntu on all partitions and see if they show up.

I too have over 25GB of 128K MP3s (~7,000 files) which took me many years to amass and it would sure suck if I lost them. I keep a backup on a second drive and have burned them to DVD as well so I don't worry about it anymore. If and when you find them you should consider backing them up.

Good luck.

tgeer

---

### Post by unmole on 2009-09-24
Any chance you moved your library or perhaps accidentally deleted your collection from amarok?

---

### Post by sedawk on 2009-09-24
Boot into Ubuntu and run this (I assume you are missing files
ending in .mp3).

```

sudo find / -type f -name \*mp3 -print

```

Good luck!

---

### Post by ladavis89 on 2009-09-25
nope nothing...i dont know what in the world could have happened to them....i was really happy with ubuntu up until now.

---

### Post by blackened on 2009-09-25
You didn't happen to batch-edit the meta data on your files did you?

---

### Post by tgeer43 on 2009-09-26
> **ladavis89 said:**
> nope nothing...i dont know what in the world could have happened to them....i was really happy with ubuntu up until now.
Don't be unhappy with Ubuntu if your mp3s are missing.
The operating system had *nothing* to do with it.

Let's recap:

[LIST]
[*]After installing Ubuntu, you ran Amarok and it found your mp3 collection on your NTFS partition.
[*]Then one day you booted up and the files (but not their folders) appeared to be missing.
[*]Then you stated that the files are actually there but just don't show up in the file manager. How did you know that they were there?
[*]Next you said that the files are _*not*_ there (but the album art is still there).
[/LIST]
You need to tell us what you have done with Amarok other than just playing your music files. I'm not familiar with Amarok itself but like most media players it has many functions for manipulating your audio collection. As stated previously this includes the ability to move or even delete your collection but it will not perform these functions unless specifically instructed to do so.

Tell us which of Amarok's functions you experimented with and maybe we can narrow down the possibilities of what has happened.

But whatever the outcome, please don't hold it against Ubuntu. It's just an operating system and doesn't inexplicably delete audio collections for no reason. You had to have done something whether intentional or not, to cause your mp3s to go missing.

tgeer

---

### Post by ladavis89 on 2009-09-28
Amarok was working perfectly for about a week.  The only functions of amarok that I used was to scan my windows partition for music.  All 6000+ of my songs appeared in the local collection and everything was fine.  I made a few playlists and i was really happy with amarok.  Then one day I booted up my machine and opened up amarok and there was nothing in my local collection.  I rescanned it and still nothing.  Also I hadn't even booted into windows since I started using ubuntu because I was so happy with ubuntu.  

I assumed the files were still there. I had no reason to think that my files were deleted since I hadn't even touched them other than scanning them in amarok.  I booted up windows just to make sure they were still there and they were not.  Again, the only thing i have done with amarok is adjust the settings to scan the My Music folder of my windows partition.  I dont know how amarok could have mistaken that for DELETE ALL MUSIC FILES....Im backing all my **** up like crazy now because Im afraid all the rest of my files might mysteriously disappear one day.

---

### Post by wilee-nilee on 2009-09-28
Have you looked in Xp to see if they are still there, and if they are you should probably save them off the computer to a ntfs formatted external HD you can get a terrabyte HD for aroud 120$ on the web. If you do this then you can use the HD to run in either Xp or Ubuntu.

---

