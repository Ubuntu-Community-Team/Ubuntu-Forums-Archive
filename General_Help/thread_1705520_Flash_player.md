---
title: "Flash player"
date: 2011-03-12
forum: General Help
---

### Post by WlaadDyaab on 2011-03-12
Hi

How do you download an update or an upgrade (or whatever it's called) on a command line. For Chromium Internet Browser

Opened the computer and couldn't watch YouTube. I tried all the downloads available on Adobe's website and all of them are on my "Downloads" folder and when I click on any I just get stuff I don't understand and I simply find it easier to download through Terminal

Help please!

---

### Post by Frogs Hair on 2011-03-12
Sorry , I don't  have Chromium , so what I wrote may not apply.

---

### Post by WlaadDyaab on 2011-03-12
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


But I still can't play YouTube video :(

---

### Post by WlaadDyaab on 2011-03-12
I restarted/rebooted my Laptop but still no YouTube videos working :(

---

### Post by WlaadDyaab on 2011-03-12
Oh Ok thanks anyway :)

---

### Post by elliotbeken on 2011-03-12
what i did was i use firefox and install a pluging called flash-aid (search for in add-ons) restart firefox then use flash-aid and it will work fine.

this even allows me to play 1080p videos in full screen mode.

---

### Post by Frogs Hair on 2011-03-12
> **WlaadDyaab said:**
> Oh Ok thanks anyway :)

I found some instructions for flash in Chormium  , but they're outdated , maybe you Google skills will be better than mine today . Use the forum search also .

---

### Post by WlaadDyaab on 2011-03-12
The problem with Firefox is that I'm scared of it Lol. I've never opened Firfow since on the date of this thread - one of my threads: [http://ubuntuforums.org/showthread.php?t=1647731](http://ubuntuforums.org/showthread.php?t=1647731)

---

### Post by WlaadDyaab on 2011-03-12
I've never opened Firefox*

---

### Post by tekkidd on 2011-03-12
Do this in the terminal:
```
sudo apt-get install flashplugin-nonfree
```

That will install flash.

---

### Post by Frogs Hair on 2011-03-12
> **tekkidd said:**
> Do this in the terminal:
```
sudo apt-get install flashplugin-nonfree
```That will install flash.

The OP has flash installed , but it is not working with Chromium. If there is anything else required please post it.

---

### Post by ericrichards420 on 2011-03-12
```
 sudo apt-get install ubuntu-restricted-extras 
```

this will install flash player make your dvd work on non encryped dvds play mp3's and more.

---

### Post by WlaadDyaab on 2011-03-12
> **tekkidd said:**
> Do this in the terminal:
```
sudo apt-get install flashplugin-nonfree
```

That will install flash.

I'm still getting this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by WlaadDyaab on 2011-03-12
> **ericrichards420 said:**
> ```
 sudo apt-get install ubuntu-restricted-extras 
```

this will install flash player make your dvd work on non encryped dvds play mp3's and more.

Hey thanks! This command worked, but I'm still stuck with not being able to play YouTube videos :(

But thank God that I can still press "Run this time" and it works, but I think it's temporary not permanently

[ATTACH]185883[/ATTACH]

---

### Post by SavageWolf on 2011-03-12
If you just want to use YouTube, you could try this:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

Also, try updating your system from the update manager.

---

### Post by WlaadDyaab on 2011-03-12
I typed "chromium forum (linux)" in the search box.I'm hoping this link will solve the problem [http://ubuntuforums.org/showthread.php?t=1207863](http://ubuntuforums.org/showthread.php?t=1207863)

---

### Post by WlaadDyaab on 2011-03-12
I've already tried it:

> sudo apt-get update
sudo apt-get dist-upgrade

(from [http://ubuntuforums.org/showthread.php?t=11103](http://ubuntuforums.org/showthread.php?t=11103))

And thanks for the help, I'll try to deal with it somehow :)

---

### Post by Frogs Hair on 2011-03-12
Keyboard malfunction !

---

### Post by Frogs Hair on 2011-03-12
Type about;lugins into the address bar of the browser and this will display your plugins . Make sure flash is enabled.

---

