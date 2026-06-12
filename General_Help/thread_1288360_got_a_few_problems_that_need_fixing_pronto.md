---
title: "got a few problems that need fixing pronto"
date: 2009-10-11
forum: General Help
---

### Post by starcraftmaster on 2009-10-11
[FONT=Arial][SIZE=2]hey guys
OS:ubuntu 9.04
i got two questions

first one is
i had 3.1 gb left of harddisk space and then all a sudden i only got 1.7 gb left
so how can i clean useless crap off ubuntu ?
i was going to use computer janitor but i heard that causes lots of problems
plus its seems it has things i need

also how can i test my firewall(firestarter)
i tried using norton online security check
[/SIZE][/FONT][U][B][FONT=Arial][SIZE=2]but it says it only works on windows/mac
firestarter says it has blocked nothing
but when it windows ZA blocks a lot of things(1 thing a day)
[/SIZE][/FONT]
a other problem is that i cant play WMA files(music files)
i tried install win32codecs but it wont work with banshee music player or movieplayer


last problem is that i can get hibernate to work at all
once its finishes showing the screen saver it goes to a black screen and never tuns off

i hope  you can think this guys
thanks for looking
[/B][/U]

---

### Post by mac9416 on 2009-10-11
> i had 3.1 gb left of harddisk space and then all a sudden i only got 1.7 gb left
so how can i clean useless crap off ubuntu ?

This command will clear out your software installer cache, freeing a little space. There are plenty of other ways to free space, but this is one of the easiest:

```
$ sudo apt-get clean
```

> a other problem is that i cant play WMA files(music files)
i tried install win32codecs but it wont work with banshee music player or movieplayer

ubuntu-restricted-extras should be the key ([https://help.ubuntu.com/community/RestrictedFormats):](https://help.ubuntu.com/community/RestrictedFormats):)

```
$ sudo apt-get install ubuntu-restricted-extras
```

I'm afraid I can't help with your other troubles. Hopefully someone who can will be along soon. :)

Good luck!

---

### Post by starcraftmaster on 2009-10-13
well mac9416
i tried sudo apt-get install ubuntu-restricted-extras
says i ready got the newest version of that

i notice that it plays enter sandman.wma
but eagles peaceful easy feeling.wma it can't play (banshee nor can movieplayer)

also i tried sudo apt-get clean
seems it did nothing olol:confused:

---

### Post by 3rdalbum on 2009-10-13
Reboot and the contents of the /tmp directory will be cleared. This may be using some disk space.

Computer Janitor gives you advice about what packages you might be able to remove. If it lists a package that you want to keep, then just uncheck the package from its list. It's as simple as that. It doesn't cause problems unless you give it the go-ahead to remove something that you want.

If you have an ADSL/cable router, then it already contains a firewall and so no incoming connections will reach your computer. If you do have one of these routers, then you don't need Firestarter or any firewall configuration utility. If you want to test your firewall, you can use the Shields Up online port scanner (check Google).

Note also that Ubuntu doesn't come with any software that listens to incoming connections, so you might not have any use for a firewall at all.

If your WMAs use DRM encryption (i.e. they were bought from an online music store a while back) then they will not play outside Windows Media Player.

---

### Post by starcraftmaster on 2009-10-14
> **3rdalbum said:**
> Reboot and the contents of the /tmp directory will be cleared. This may be using some disk space.

Computer Janitor gives you advice about what packages you might be able to remove. If it lists a package that you want to keep, then just uncheck the package from its list. It's as simple as that. It doesn't cause problems unless you give it the go-ahead to remove something that you want.

If you have an ADSL/cable router, then it already contains a firewall and so no incoming connections will reach your computer. If you do have one of these routers, then you don't need Firestarter or any firewall configuration utility. If you want to test your firewall, you can use the Shields Up online port scanner (check Google).

Note also that Ubuntu doesn't come with any software that listens to incoming connections, so you might not have any use for a firewall at all.

If your WMAs use DRM encryption (i.e. they were bought from an online music store a while back) then they will not play outside Windows Media Player.

are you saying theirs no possible way to play my wma files ?

also i did the test
passed em all:)
(i got no router)

a problem with that janitor program is that i dont know what  some packages are and some of them may be taking a lot of room. it does not say how much room it takes(i can google search but theirs so many packages)

---

### Post by lastoneleft07 on 2009-10-14
> **starcraftmaster said:**
> are you saying theirs no possible way to play my wma files ?

also i did the test
passed em all:)
(i got no router)

a problem with that janitor program is that i dont know what  some packages are and some of them may be taking a lot of room. it does not say how much room it takes(i can google search but theirs so many packages)

Install windows media player using Play on Linux

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by 3rdalbum on 2009-10-14
> **starcraftmaster said:**
> are you saying theirs no possible way to play my wma files ?

If your WMA files were bought off an online music store and they are encrypted with DRM, then they won't play natively on Linux. They won't play on anything except a copy of Windows Media Player that is "authorised" to your music store account. Now that I think about it, I remember hearing that an old version of WMP used to apply DRM encryption to music that you rip off CDs.

If your files are not DRM-encrypted, then they can be played with the "w32codecs" or "w64codecs" packages.

> also i did the test
passed em all:)
(i got no router)

Ubuntu doesn't listen to incoming ports by default. So you don't need a firewall.

> a problem with that janitor program is that i dont know what  some packages are and some of them may be taking a lot of room. it does not say how much room it takes(i can google search but theirs so many packages)

Fair enough; but remember we're a good resource for telling you what you can and can't delete. Do you want to type in the names of the packages and we can advise on what to delete?

---

### Post by t0p on 2009-10-14
A good way to see what's taking up space on your disk(s) is to use the **Disk Usage Analyzer**: you'll find it at **Applications > Accessories > Disk Usage Analyzer**.  It gives you a nice graphical representation of what's on your disk(s) and how much space each item takes up. Click on the button "Scan Filesystem" and it draws a pie-chart of your disk use.  Then use your mouse pointer to get details.

---

### Post by macabrem on 2009-10-14
> **starcraftmaster said:**
> are you saying theirs no possible way to play my wma files ?

also i did the test
passed em all:)
(i got no router)

a problem with that janitor program is that i dont know what  some packages are and some of them may be taking a lot of room. it does not say how much room it takes(i can google search but theirs so many packages)

You might want to download VLC and mplayer.  Those two with the restricted extras seem to be able to play anything and everything I have tried - although I haven't tried any files with DRM.  I'm not sure if VLC and Mplayer install extra codecs besides what the restricted extras install, but it is worth a try.

---

