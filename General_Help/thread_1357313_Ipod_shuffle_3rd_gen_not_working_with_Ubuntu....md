---
title: "Ipod shuffle 3rd gen not working with Ubuntu..."
date: 2009-12-17
forum: General Help
---

### Post by binare on 2009-12-17
Hi there

I recently got an ipod shuffle 2GB (3rd gen). I am only using Ubuntu (8.10 atm) and can thus not use iTunes.

To my disappointment, I cannot get my new shuffle to play back tunes :(. 

I am able to load songs and playlists onto the device with no sweat, but when I eject and try to listen, I am greeted with this message: "please use itunes to sync music to this ipod".

Like I mentioned, everything seems to work fine; the device mounts properly; I can upload tunes and playlists. BUT I CAN'T listen to any of the uploaded stuff...

I have tried several different applications, including Rhythmbox, gtkpod, songbird, amarok, etc. which SEEMS to work fine...

Does anyone know how to get past this prob??
Any help would be appreciated ;).

Thanks guys!

---

### Post by binare on 2009-12-17
Oh yea, I forgot to mention that the model no is A1271. It looks like a 4th gen ipod, but I think it's 3rd gen shuffle ;).

Thanks!

---

### Post by asqn34 on 2009-12-17
hi,
try this

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

---

### Post by binare on 2009-12-17
asqn34, the thread you pointed me is real old; I tried most of the stuff suggested tho...

I don't think there's support for this new iPod shuffle yet...

Anybody?

I really don't feel like setting up a VM or something, just to use my iPod!!

---

### Post by asqn34 on 2009-12-26
i am using amarok with my ipod nano. 
It work great as long as i plug the ipod first before switching the computer.
good luck

---

### Post by deadland on 2009-12-28
Hi I have exactly the same problem with a Ipod shuffel (Model A1271). Is there any solution?

---

### Post by moody_mark on 2009-12-29
Just to bump this thread, I have the same problem here. In fact if I load songs on via iTunes and then add something via rhythmbox it seems to screw up the whole iPod and I get the audio message "please use itunes..." blah

I can use an older iPod shuffle without a problem. I think we'll just have to wait a while for a update to come out to support this new gen of iPods... Unfortunately love it or hate it, I have to keep a windows PC kicking around to run some kind of app or another.

---

### Post by asqn34 on 2009-12-29
check this:

[http://amarok.kde.org/wiki/Media_Device:IPod#Devices_with_Firmware_2.x](http://amarok.kde.org/wiki/Media_Device:IPod#Devices_with_Firmware_2.x)

---

### Post by danopia on 2010-02-21
Jailbreaking a shuffle? Seems kinda unnecessary.

I'm going to try iTunes in WINE.

Oh darn old topic

---

### Post by Floola on 2010-03-14
Floola 5.5 now supports shuffle3G.

Visit [http://www.floola.com](http://www.floola.com)

---

### Post by beefcurry on 2010-04-09
I am using Floola 5.6, and it does not recognize my ipod shuffle 3rd gen, if only someone did not give me this as a gift my life will be so much less stressful.

---

### Post by Floola on 2010-04-12
You'll need to add at least one song with iTunes, then you'll need to properly mount the device in order to use it with Floola.

---

### Post by ethanmadden on 2010-04-19
I've got a 3rd gen shuffle here, with the same problem as the original poster. No matter what application I use to sync as soon as I start it up it says "please use iTunes to sync music to this iPod" and then shuts down.

I've tried rhythmbox, rebuild_db, and even tried using mediamonkey in windows, and I'm not getting any success.

Edit: After about 2 more hours of screwing around with it I seem to have found a method that works.

1) Download the following tools:
      a)A sample iPod shuffle [root directory]("http://shuffle-db.sourceforge.net/ipod_root.zip").
      b)[Floola]("http://www.floola.com/home/download_linux/") (links at the bottom)

2)Erase all visible files on the shuffle (you can delete the hidden ones, too, it doesn't really matter, either way you need to wipe the drive clean)

3)Unzip the root directory that you downloaded into the iPod root

4)Open Rhythmbox and sync all of the music to it that you want. (It may be wise to create a playlist for the iPod so that you can just sync that in the future). At this point running the iPod will still ask you to sync it using iTunes.

5)Unpack and run floola. On the first run it will ask you what kind of iPod you are using, be sure to select the shuffle 3g option, I believe it is the second option available.

This worked for me, but I have to start over at step 2 every time I want to add music to it. Also, the song title reading feature doesn't work. Better than nothing, though, in my opinion.

Your mileage may vary.

---

### Post by Jefferythewind on 2010-05-15
I just got my friend's ipod shuffle 3g working with foola, that software is awesome!!

  The ipod already had been used with itunes and had 100 or more songs on it.

---

### Post by pat.techouvot on 2010-06-13
I have tested this solution and it's run very well with iPod A1271 :

My configuration :
Ubuntu 10.04 AMD 64

1- Download and install Virtual box ORACLE 3.2.4 (PUEL)

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Do not use the version of Virtual box (OSE) 3.1.6 whith synaptics

2- Install Windows XP SP3 (or SP2, but no older version) on Virtual box.

3- Download iTunes for version 9.0.2.25

[http://www.9down.com/iTunes-9-0-2-25-261406/](http://www.9down.com/iTunes-9-0-2-25-261406/)

Install this version on your emulated Windows XP with Virtual box.

Very important : do not accept the apple automatic upgrade program
and DO NOT UPGRADE your iTunes 9.0.2.25 !

4- When your are using iTunes with your iPod A1271, open the USB acces.


Excuse my english because I'am French and I'do not speak this language very well...

Friendly.

Pat.

---

### Post by pip182 on 2010-06-15
You guys are awesome, I won this same ipod in a drawing at work (it's actually a 4th generation) I never could get it working. But with your tips I finally got it to work. Here is what I did thanks to ethanmadden.

1: Delete all files on my ipod (hidden and trash as well)
2: Extracted the example Ipod directory structure posted above
3: Added 1 song with rhythmbox, hit eject. 
4: Opened gtkpod and created Ipod directories in the music menu (this may or may not have done anything at all) 
5: Opened floola went to tools, renamed my ipod, and searched for lost files. 
6: Opened up my ipod folder and deleted the floola lost files folder, showed hidden files and deleted the trash folder on my ipod as well (all the files go in there unless you manually delete it).
7: Went back to floola, went to item and add. Now I can drag and drop all my music from rhythmbox into there and IT WORKS! I can add and delete songs on my ipod shuffle and have them play! Thanks to floola and you guys.  

I just barely did this and I'm sure this method could be cleaned up a bit ;) But whatever I did got it working. Hope it helps someone. 

The Virtualbox method did not work for me, my Ipod would not even show up in iTunes, yes I enabled the USB support for my device.

---

### Post by Sobooban on 2010-07-24
hmm do i realy have to downgrade to 32bit to get my ipod shuffle 4th gen to work in Ubuntu? kinda sucks!
floola uses i386 stuff=(

---

### Post by peterVG on 2010-08-10
FYI: Experienced similar problems as those reported above. The fix for me was (unfortunately) to dock iPod Shuffle 3G to a Windows machine running iTunes. Then reformatting it and following Floola download, iPod config requirements and Floola install instructions **step-by-step** here: [http://www.floola.com/home/docs_install/](http://www.floola.com/home/docs_install/)

It works great now. I run Floola directly from the iPod Shuffle 3G now from any one of my Ubuntu 10.04 machines.

---

### Post by SimonJones on 2010-09-01
I still can't help in Linux but Foobar2000 works with my Shuffle. [http://www.foobar2000.org/](http://www.foobar2000.org/) 

All I do is right click the song/playlist and send to ipod, then it does all the transfer and gapless for me. I remove the ipod and it plays. 

How I wish this was available for Linux! :-(

---

### Post by scouser73 on 2010-09-01
For an iPod to be recognised in Ubuntu, you firstly have to initialise it with iTunes on Windows. Then unplug the iPod and go back to your Ubuntu PC & it will work with Rhythmbox, I think Banshee Music Player will also allow you to synchronise your iPod.

---

### Post by TheNerdAL on 2010-10-09
> **pip182 said:**
> You guys are awesome, I won this same ipod in a drawing at work (it's actually a 4th generation) I never could get it working. But with your tips I finally got it to work. Here is what I did thanks to ethanmadden.

1: Delete all files on my ipod (hidden and trash as well)
2: Extracted the example Ipod directory structure posted above
3: Added 1 song with rhythmbox, hit eject. 
4: Opened gtkpod and created Ipod directories in the music menu (this may or may not have done anything at all) 
5: Opened floola went to tools, renamed my ipod, and searched for lost files. 
6: Opened up my ipod folder and deleted the floola lost files folder, showed hidden files and deleted the trash folder on my ipod as well (all the files go in there unless you manually delete it).
7: Went back to floola, went to item and add. Now I can drag and drop all my music from rhythmbox into there and IT WORKS! I can add and delete songs on my ipod shuffle and have them play! Thanks to floola and you guys.  

I just barely did this and I'm sure this method could be cleaned up a bit ;) But whatever I did got it working. Hope it helps someone. 

The Virtualbox method did not work for me, my Ipod would not even show up in iTunes, yes I enabled the USB support for my device.

Floola gives me this. :( 
[IMG]http://i.imgur.com/7nP7p.png[/IMG]

---

