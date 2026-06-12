---
title: "Firefox freezes everytime..."
date: 2009-07-14
forum: General Help
---

### Post by J03y on 2009-07-14
Ok so theres a site a go to a lot called [GaiaOnline]("http://www.gaiaonline.com") but every time I go to the forums for example [[this one]]("http://www.gaiaonline.com/forum/gaia-aquarium/b-boutique-short-paged-library-3xcontest-alert/t.49297849/?sequence=76")  Firefox freezes and doesn't let me scroll down or anything, but in Windows I go to the forums with Firefox and it doesn't freeze at all and it runs smoothly. So is there anyway I can make Firefox handle more flash or something?

Edit: I forgot that you have to be logged in to access that thread. I replaced the link so click it again.

---

### Post by J03y on 2009-07-14
Bump

---

### Post by margni on 2009-07-14
I got to your site:

[http://www.gaiaonline.com/forum/from_feed/booty-grab-read-first-post/t.46900015_recent/?_gaia_t_=626](http://www.gaiaonline.com/forum/from_feed/booty-grab-read-first-post/t.46900015_recent/?_gaia_t_=626)

but the page there says it no longer exists... ??

---

### Post by lovinglinux on 2009-07-14
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by J03y on 2009-07-15
Wow thanks. I certainly noticed an improvement when i made some tweaks to those files, but it still freezes even when I turn off the visual effects.

---

### Post by lovinglinux on 2009-07-15
> **J03y said:**
> Wow thanks. I certainly noticed an improvement when i made some tweaks to those files, but it still freezes even when I turn off the visual effects.

You should try Firefox 3.5

---

### Post by J03y on 2009-07-15
> **lovinglinux said:**
> You should try Firefox 3.5I was thinking about doing it, but what's pgo? Does Firefox 3.5 come with it?

---

### Post by lovinglinux on 2009-07-15
> **J03y said:**
> I was thinking about doing it, but what's pgo? Does Firefox 3.5 come with it?

From: [http://en.wikipedia.org/wiki/Profile...d_optimization](http://en.wikipedia.org/wiki/Profile...d_optimization)

> Profile-guided optimization (PGO) is a compiler optimization technique in computer programming to improve program runtime performance. In contrast to traditional optimization techniques that solely use the source code, PGO uses the results of test runs of the instrumented program to optimize the final generated code.[1] The compiler is used to access data from a sample run of the program across a representative input set. The data indicates which areas of the program are executed more frequently, and which areas are executed less frequently. All optimizations benefit from profile-guided feedback because they are less reliant on heuristics when making compilation decisions.

I don't know if they compile Firefox with PGO enabled or if they included this feature to allow PGO during compilation. Anyways, I'm using my own compiled version and PGO didn't improved performance that much. Nevertheless, I had a significant performance improvement (30% boost) by compiling with optimization flags for my processor.

If you want to try the benefits of PGO and processor optimization, you could install Swiftweasel, which is basically an optimized Firefox. 

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by J03y on 2009-07-18
Thanks. I installed Swiftfox and Swiftweasel but still I couldn't find any difference between the performance of Firefox, Swiftweasel and Swiftfox, :confused: .

---

### Post by lovinglinux on 2009-07-18
> **J03y said:**
> Thanks. I installed Swiftfox and Swiftweasel but still I couldn't find any difference between the performance of Firefox, Swiftweasel and Swiftfox, :confused: .

[Peacekeeper](http://service.futuremark.com/peacekeeper/index.action)

---

### Post by RJARRRPCGP on 2009-07-18
It didn't freeze at that page, but the scrolling was slow!

---

### Post by arizonalarry2 on 2009-07-18
I'll start my computer, start up FireFox and it freezes about one minute later regardless of what website I'm on. This happens at every single bootup without exception. I just sit there and watch it go black and white, sometimes it comes back after a few seconds and sometimes I have to force quit and start it up again. Once I get through the first freeze it works fine until the next time I bootup. 

FireFox 3.0.11 on Ubuntu 9.04

---

### Post by J03y on 2009-07-19
> **lovinglinux said:**
> [peacekeeper](http://service.futuremark.com/peacekeeper/index.action)
[attach]121707[/attach] [attach]121708[/attach]

Hehe, 1st one's from Swiftweasel and 2nd's from Firefox.

---

### Post by lovinglinux on 2009-07-19
> **J03y said:**
> [attach]121707[/attach] [attach]121708[/attach]

Hehe, 1st one's from Swiftweasel and 2nd's from Firefox.

Not much. Why did you installed swiftweasel 3.0.11 instead of 3.5?

Also make sure you download the correct version for your processor.

---

### Post by J03y on 2009-07-20
> **lovinglinux said:**
> Not much. Why did you installed swiftweasel 3.0.11 instead of 3.5?

Also make sure you download the correct version for your processor.
Cause for some reason I cant start 3.5 but I can start 3.0.11. I "installed" Swiftweasel 3.5 with this [guide]("http://swiftweasel.wiki.sourceforge.net/Installation") but when I type Swiftweasel on a terminal this is the output:

```
cp: cannot stat `/home/joey/.sw3/*': No such file or directory
/usr/local/swiftweasel/swiftweasel-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

```

---

### Post by lovinglinux on 2009-07-21
> **J03y said:**
> Cause for some reason I cant start 3.5 but I can start 3.0.11. I "installed" Swiftweasel 3.5 with this [guide]("http://swiftweasel.wiki.sourceforge.net/Installation") but when I type Swiftweasel on a terminal this is the output:

```
cp: cannot stat `/home/joey/.sw3/*': No such file or directory
/usr/local/swiftweasel/swiftweasel-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

```

Try method **4.2** from the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by J03y on 2009-07-21
Ok I installed Swiftfox but the problem is that it doesn't have any plugins...

---

### Post by lovinglinux on 2009-07-21
> **J03y said:**
> Ok I installed Swiftfox but the problem is that it doesn't have any plugins...

Swiftfox uses the same profile folder as Firefox 3.0, which is ~/.mozilla/firefox. If you were using Shiretoko recently, then your stuff might be under  ~/.mozilla/firefox-3.5.

If you are referring to extension incompatibility, then you can turn version checking off. See [COLOR="DarkRed"]**Extension Compatibility**[/COLOR] section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by J03y on 2009-07-21
All of the addons are there. 

[ATTACH]121866[/ATTACH] [ATTACH]121867[/ATTACH]

---

### Post by lovinglinux on 2009-07-21
> **J03y said:**
> All of the addons are there. 

BTW, when you install Swiftfox, it creates a symlink to **/usr/lib/mozilla/plugins** inside **/usr/lib/swiftfox**, so you plugins shouldn't be missing.

---

### Post by J03y on 2009-07-21
Earlier I came across a thread about the same problem and it said that i had to: 
```
$ cd /opt/swiftfox
$ sudo mv plugins plugins.old
$ sudo ln -s /usr/lib/firefox/plugins /opt/swiftfox/plugins
```

But theres isnt anything in the opt folder.

---

### Post by lovinglinux on 2009-07-21
Try this:

```

sudo mv /usr/lib/swiftfox/plugins /usr/lib/swiftfox/plugins.old
sudo ln -s /usr/lib/firefox/plugins /usr/lib/swiftfox/plugins
```

---

### Post by J03y on 2009-07-23
> **lovinglinux said:**
> Try this:

```

sudo mv /usr/lib/swiftfox/plugins /usr/lib/swiftfox/plugins.old
sudo ln -s /usr/lib/firefox/plugins /usr/lib/swiftfox/plugins
```
Well never mind. I guess im stuck using Firefox 3.5. Thanks for your help and your optimization thread, :D .

---

### Post by MountainX on 2009-12-19
> **J03y said:**
> when I type Swiftweasel on a terminal this is the output:

```
/usr/local/swiftweasel/swiftweasel-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

```

I ran into this exact error today.
```
/opt/swiftweasel/swiftweasel-3.5.5/swiftweasel-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
```

I'm sure it's because libxul.so was located in /usr/lib/xulrunner-1.9.1.5 and now, after today's update, it is in /usr/lib/xulrunner-1.9.1.6

What's the right way to fix this? The firefox thread ([http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)) didn't help me... (but it is a great thread for general info).

---

### Post by linux_junky on 2010-02-18
> **MountainX said:**
> I'm sure it's because libxul.so was located in /usr/lib/xulrunner-1.9.1.5 and now, after today's update, it is in /usr/lib/xulrunner-1.9.1.6
What's the right way to fix this?

After I updated [SIZE=3]**SWIFTWEASEL**[/SIZE] this morning...
My libxul.so got relocated to /usr/lib/xulrunner-1.9.1.8/ so I had to replace a few symbolic links.
I would guess that if you change my 1.9.1.8 to your 1.9.1.6 that you MIGHT have the same success that I have had.
[COLOR=Red]FOR ANYONE NEW TO THIS... USE GREAT CAUTION WHEN WORKING WITH "RM" ESPECIALLY "SUDO RM" !!!! MAKE SURE YOU KNOW WHAT YOU ARE REMOVING!!![/COLOR]
```
locate libxul.so
sudo rm /usr/local/swiftweasel/libxul.so
sudo ln -s /usr/lib/xulrunner-1.9.1.8/libxul.so /usr/local/swiftweasel/libxul.so
locate libxpcom.so
sudo rm /usr/local/swiftweasel/libxpcom.so
sudo ln -s /usr/lib/xulrunner-1.9.1.8/libxpcom.so /usr/local/swiftweasel/libxpcom.so
swiftweasel 
```

---

