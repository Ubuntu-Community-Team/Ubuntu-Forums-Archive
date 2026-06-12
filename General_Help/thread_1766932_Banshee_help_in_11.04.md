---
title: "Banshee help in 11.04"
date: 2011-05-25
forum: General Help
---

### Post by I got worms. on 2011-05-25
I WAS so excited to see after installing 11.04 that Banshee recognized and seemingly was able to communicate with my iPhone4 however, something is missing and I am unsure of what it is. 
](*,)
Banshee says that it's syncing the audio files that I'm trying to transfer and the iPhone says it too is in the syncing process.  Unfortunately, nothing transfers over to the iPhone.  Banshee thinks it has, and the iPhone acts as if it has received the information but the result is unsuccessful.  This goes for both the addition and the deletion of files.

Is any one else having these issues or has a better idea of how I can use my ubuntu and my iPhone4 in harmony?  
I've tried the dual boot thing with windows for iTunes and for reasons and details I'd rather not get into it simply does not work for me. 

Thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-25
This works great for syncing

[http://www.gtkpod.org/wiki/Home](http://www.gtkpod.org/wiki/Home)

---

### Post by I got worms. on 2011-05-25
> **linuxinstalledfromhdd said:**
> This works great for syncing

[http://www.gtkpod.org/wiki/Home](http://www.gtkpod.org/wiki/Home)

Thanks but no dice.  However, I was surprised that it recognized the iPhone4.  I have had some bad luck in the past with gtkpod and an iTouch I used to have.  

Anyways, I tried to transfer a few music files over and upon saving the changes gtkpod gave me a warning message; "Unsupported checksum type."  I'm unsure of what this means so I'll have to look into it.
If anyone has any thoughts or input I would appreciate it.
:confused:

---

### Post by DinoT1985 on 2011-05-25
Try this [http://guayadeque.org/forums/index.php?p=/wiki/page/home](http://guayadeque.org/forums/index.php?p=/wiki/page/home)

Its called Guayadeque, pronounced Gua-ya-de-key.

---

### Post by I got worms. on 2011-05-27
> **DinoT1985 said:**
> Try this [http://guayadeque.org/forums/index.php?p=/wiki/page/home](http://guayadeque.org/forums/index.php?p=/wiki/page/home)

Its called Guayadeque, pronounced Gua-ya-de-key.


Thanks for the suggestion but unfortunately this didn't work either.  Guayadeque couldn't load my iPhone...

(sigh)

I find this whole thing so annoying!  I can't understand why Apple forces one to use iTunes.

---

### Post by LordNeo on 2011-05-27
> **I got worms. said:**
> Thanks for the suggestion but unfortunately this didn't work either.  Guayadeque couldn't load my iPhone...

(sigh)

I find this whole thing so annoying!  I can't understand why Apple forces one to use iTunes.
Because it his way to check DRM before letting you copy stuff.

check and update (if posible) libimobiledevice

Reading this ([http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/](http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/)) it appearently the "new hash" checksum for the iDevices is not supported yet.
In the link you can find a way to "force" using the old hash

---

### Post by mdhollis on 2011-05-27
This sounds similar.  Although at least some of the tracks show up.

[https://bugzilla.gnome.org/show_bug.cgi?id=643559]("https://bugzilla.gnome.org/show_bug.cgi?id=643559")

---

### Post by I got worms. on 2011-05-29
> **LordNeo said:**
> Because it his way to check DRM before letting you copy stuff.

check and update (if posible) libimobiledevice

Reading this ([http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/](http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/)) it appearently the "new hash" checksum for the iDevices is not supported yet.
In the link you can find a way to "force" using the old hash

Yeah, it seems that as of now I'm forced to wait until the new hash is supported.  
I don't want to try and force the issue by jailbreaking my iPhone. I did it with an old iTouch and it seemed to cause me more headache than it was worth.  :-k

---

### Post by I got worms. on 2011-05-29
> **mdhollis said:**
> This sounds similar.  Although at least some of the tracks show up.

[https://bugzilla.gnome.org/show_bug.cgi?id=643559]("https://bugzilla.gnome.org/show_bug.cgi?id=643559")


I agree, it does sound similar.  However, I think that person was running a different gen. iPod. 
Thanks.

---

### Post by ratant on 2011-05-31
i have the exact same problem. the worst part is my iphone still displays all the music I tried to delete from it, only the album art is mixed up beyond belief, and the songs don't play when you select them, they just look like they are about to. so i guess it did delete them technically. the songs I try to transfer to my iphone 4 don't show up at all, but the album art actually does transfer over..it just randomly shows up as a cover for the wrong albums. this is super frustrating. i've been thinking about jailbreaking it, but I never have before, and none of the jailbreak websites look legit.

---

### Post by wbm on 2011-05-31
How is the iPhone formatted?
If it is Mac formatted it shows up but you can't copy to it. If it is WIndows formatted it shows up AND you (hopefully) can write to it.

---

### Post by I got worms. on 2011-06-04
Same thing here.  I managed to corrupt all the existing music I had on my iPhone while I was messing with it.  Luckily I had it all backed up but it's very annoying to not be able to play any music now.  :(

I had some issues in the past with an iTouch that I jailbroke in the past like I had mentioned and I didn't feel that it was worth it.  In the end I had some trouble with gtkpod and an update that said something to the effect that they will never support my iPod...ever.  I don't want to risk something like that on my phone for obvious reasons.  

I think I'm going to have to go back to running windows (solely for iTunes) as well as Ubuntu and just choosing between the two at start-up.  That's the only solution I can see until Banshee figures out how to bridge the gap.

---

### Post by I got worms. on 2011-06-04
> **wbm said:**
> How is the iPhone formatted?
If it is Mac formatted it shows up but you can't copy to it. If it is WIndows formatted it shows up AND you (hopefully) can write to it.

I assume it's Mac/Apple formatted...  I only assume this because of all the trouble it's causing and I've never seen any indication of Windows anywhere.  Is there a way to tell for sure that I might have overlooked?

---

