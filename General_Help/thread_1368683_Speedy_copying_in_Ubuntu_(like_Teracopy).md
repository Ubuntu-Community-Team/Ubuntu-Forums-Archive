---
title: "Speedy copying in Ubuntu (like Teracopy)?"
date: 2009-12-30
forum: General Help
---

### Post by astrobeaver on 2009-12-30
Hi all

Is there any application for Ubuntu/Linux that speeds up copying of files? Teracopy is one but it is only meant for Windows.

[http://www.codesector.com/teracopy.php](http://www.codesector.com/teracopy.php)

I tried installing Teracopy through Wine but that didn't work.

---

### Post by jbrown96 on 2009-12-30
Preload will cache commonly used files in ram; however, it's history-based, so it takes a few days to learn what you use. In a terminal (apps-->accessories-->terminal) ```
sudo apt-get install preload
```

I believe that when you are transferring files in Gnome (Ubuntu) there are options to pause file transfers. I know in KDE (Kubuntu) you can pause transfers. 

Besides being able to pause file transfers, which is possible in Ubuntu, this software sounds useless. 
Low-level stuff like this will not work in Wine.

---

### Post by Dino_ on 2010-01-02
I'm afraid you are mistaken, jbrown96 :-)
Preload won't change your transfer rates (say, copying files from one HDD to another), but will decrease startup time of frequently used programs.
Maybe if you would copy those cached programs/libs, it'll show an increase in transferspeed... but when would you do something like that? :-s

Second, there is no pause button in gnome. There are however many ideas spinning at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) to implement it :-)

I'm sorry to say astrobeaver, but I am not aware of any program like terracopy for linux.
I've been looking like mad too. :-(

---

### Post by jbrown96 on 2010-01-02
> **Dino_ said:**
> I'm afraid you are mistaken, jbrown96 :-)
Preload won't change your transfer rates (say, copying files from one HDD to another), but will decrease startup time of frequently used programs.
Maybe if you would copy those cached programs/libs, it'll show an increase in transferspeed... but when would you do something like that? :-s

Second, there is no pause button in gnome. There are however many ideas spinning at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) to implement it :-)

I'm sorry to say astrobeaver, but I am not aware of any program like terracopy for linux.
I've been looking like mad too. :-(

Preload will speed up frequent file transfers. because the files will already be cached in memory, so there's no read from the hard drive, just write. Obviously, it will only work on files that preload caches. Preload will cache more than programs/libs; any file that is regularly used will be cached, so there is a potential for improvement.

You can look into tmpfs, but it won't be automatic like that Windows program. Tmpfs is insanely fast, but you need to know what you are doing.

I stopped using Gnome a year ago, but there definitely used to be a pause button in Gnome. If you do need to be able to pause transfer, then look at KDE, which has excellent support for this.

---

### Post by warfacegod on 2010-01-02
I think simply moving the file with the terminal as opposed to drag and drop would be faster.

---

### Post by jbrown96 on 2010-01-02
> **warfacegod said:**
> I think simply moving the file with the terminal as opposed to drag and drop would be faster.

Unfortunately, no. GUI and CLI utilities use the same kernel apis, so they will be the same speed. cp also has the disadvantage that it doesn't have a status bar, which can be frustrating when copying a large file.

---

### Post by Dino_ on 2010-01-03
> **jbrown96 said:**
> Preload will speed up frequent file transfers. because the files will already be cached in memory, so there's no read from the hard drive, just write. Obviously, it will only work on files that preload caches. Preload will cache more than programs/libs; any file that is regularly used will be cached, so there is a potential for improvement.

You can look into tmpfs, but it won't be automatic like that Windows program. Tmpfs is insanely fast, but you need to know what you are doing.

I stopped using Gnome a year ago, but there definitely used to be a pause button in Gnome. If you do need to be able to pause transfer, then look at KDE, which has excellent support for this.

Maybe there was a pause button in gnome 1.0, but I haven't come across it in the past two years. :P

Could you point me at some info about preload caching "casual" files? I'm very interested.
Preload tracks processes, so it'll be very unlikely to cache your bigdocument.odt. :confused:

...sorry getting off-topic a bit :-)

---

### Post by abhijithnilama on 2011-02-27
ULTRACOPIER can serve.......

---

