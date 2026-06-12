---
title: "Problems accesing internet and viewing files"
date: 2011-07-31
forum: General Help
---

### Post by shmalphy on 2011-07-31
I just downloaded wubi and I cannot connect to the internet. I use eay tether to connect to my Android phone on Vista, but I can't get it to work in Ubuntu

Also, I can't see any of my pictures, video, or music files in Ubuntu, how do I access these? 

I would like to eliminate Windows, but I want to make sure I know how to use Ubuntu first. 

Please keep in mind I am just getting started and know nothing about how to use Ubuntu at all, so keep it real simple, thanks!

---

### Post by spiky001 on 2011-07-31
Hi You could boot straight off the cd and run ubuntu from the cd instead of using wubi, you might find the internet connects easier, You can also see how it looks without any chamge to pc. If you like it you can then install as a dual boot setup which means Ubuntu runs alongside the windows install.

---

### Post by bcbc on 2011-07-31
Your windows files will be under the /host directory (under 'File System'). [http://ubuntuforums.org/showthread.php?t=914358](http://ubuntuforums.org/showthread.php?t=914358)

Can your android phone create a wireless network - that might work better.

---

### Post by shmalphy on 2011-07-31
OK, I will look into creating a wireless network on the android. When I plug it in, it seems to regognize the phone as a mobile broadband connection, I am not sure if that is the same as my mobile 3g connection, or if that may be the problem.

---

### Post by shmalphy on 2011-07-31
I found the files, but they cannot be played until I download an add-on, but I still can't connect to the internet. I downloaded and installed the Ubuntu version of the Easy Tether driver from Ubuntu, and switched to Ubuntu in the settings of Easy Tether on my phone. It seems to me that should work, but I am still unable to get on the web.

Should I maybe take this to the Easy Tether forums? Or does anyone know how to link the phone wirelessly? I found some info but it seems the phone needs to be rooted, is that true? If so how do I do that?

---

### Post by bcbc on 2011-07-31
Install ubuntu-restricted-extras to get access to mp3's etc.

I don't know how to setup a wireless hotspot on an android phone. I watched someone do it on an iphone4 and it was pretty much a one-click deal. Why would it need to be rooted? It's probably a good idea to try the easy tether forum.

---

### Post by shmalphy on 2011-07-31
I just had to open the terminal and type easy tether connect, and it worked. I am typing this from Ubuntu right now, I am going to mark this one solved. Thanks so much!

---

### Post by bcbc on 2011-07-31
> **shmalphy said:**
> I just had to open the terminal and type easy tether connect, and it worked. I am typing this from Ubuntu right now, I am going to mark this one solved. Thanks so much!
Great! 

> **shmalphy said:**
> I would like to eliminate Windows, but I want to make sure I know how to use Ubuntu first. 

PS Wubi is a great way to try out Ubuntu, but if you are planning to eliminate Windows then at some point you'll need to reinstall Ubuntu direct to partition, or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") your Wubi. It's something to keep in mind - as you customize your Wubi install - keep notes along the way if you're planning to reinstall. Also [avoid]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen") hard poweroffs if the wubi hangs as well.

---

### Post by shmalphy on 2011-08-02
Wow, that response solved another thread I made. That link is super helpful (when all else fails, read the directions) 

Thanks again, you are the best bcbc

---

### Post by bcbc on 2011-08-03
> **shmalphy said:**
> Wow, that response solved another thread I made. That link is super helpful (when all else fails, read the directions) 

Thanks again, you are the best bcbc

You're more than welcome :) Enjoy!

---

