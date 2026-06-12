---
title: "gtkpod is the devil"
date: 2006-03-21
forum: General Help
---

### Post by ironuckles on 2006-03-21
I would like to take this moment to vent my undying hatred for the program called gtkpod. I've been using Linux for 5 years, and I've never had a problem. Ok, a few bugs now and then, a few kinks to work out, but nothing disastrous.
I went on the Ubuntu chat and asked around about if there was a Linux prog to use my iPod. They recommended gtkpod.
I opened this program, ran it, and tried to use it to upload some music from my laptop onto my iPod. The result? I now have NO music on my iPod.
Yes, that's right. gtkpod erased my iPod.
Perhaps you can't understand my anger unless you've owned an iPod for some time. I had things on there that I will *never* replace. It was my sole source of music, and I am very, _very_ pissed off. 

Not only did this f***ing program erase all my music. It didn't even upload the new music I was trying to put on there. It seems to have corrupted the poor little iPod, which will not even mount in Ubuntu anymore. 
Can someone please help me? Is there any way to salvage my music? My only hope is that when I check the stats under the About menu on the iPod, it tells me that I am using about 9 GB out of 18. Does that mean the data is still intact?

---

### Post by kaffelars on 2006-03-21
First of all, I am sorry for your loss. I can't really imagine what it's like, because I have all my music on one PC and one USB disk in addition to my iPod (as well as the physical CD's).

What I would try, if it won't mount in Ubuntu, is to boot your computer with a live CD and see if it mounts there if you plug it in (I guess it should be mountable as a regular external disk). You could also try to plug it into another computer, both Windows and Linux should recognize it as an external disk.

However, i do **not** promise **anything**!

Good luck :)

---

### Post by Brynster on 2006-03-21
Sounds to me like the file system on the Ipod has become corrupted.

Its not a major issue. But into windows and run ipod updater service(free download for apple.com) Allow it to reformat in into fat32. From there you should be able to remount the Ipod  within Ubuntu and GTKpod (Or in my opinion a better choice is Amaork) tunes back to you Ipod.

This happened to me also and this is how i had to fix it.

---

### Post by ironuckles on 2006-03-21
Okay, here are some updates.
First of all, I was right to suspect that the music files themselves weren't actually lost. I opened iTunes in Windows to see what would happen. Not much; iTunes showed that I was using 0 out of 9 GBs on the iPod. 
I ran chkdsk on the iPod drive, and it said what I had feared: the iTunesDB file was corrupted. I then tried running the iPod updater software, but it crashed with an error message. 
I rebooted Ubuntu and tried mounting the drive again. This time is worked. The files were still all there, under the /media/ipod/iPod_Control/Music directory. Rather than try to fix the DB files, I decided to just make a backup of all my music and load it back onto the iPod through Windows. 
I wrote a simple perl script to automate this.

```
for($i=0;$i<10;$i++)
{
	system("cp /media/ipod/iPod_Control/Music/F0$i/* ~/Music/Backup/");
}

for($i=11;$i<50;$i++)
{
	system("cp /media/ipod/iPod_Control/Music/F$i/* ~/Music/Backup/");
}

```

After this ran, I just reformatted the iPod. The updater didn't work, so I just did a quick format to clear the drive. Opening iTunes then seems to have created a new iTunesDB file.

I've started to slowly copy all the rescued music back to Windows and onto the iPod. So far it works! It's probably not the best solution, but as long as I keep my music, I don't care.

---

