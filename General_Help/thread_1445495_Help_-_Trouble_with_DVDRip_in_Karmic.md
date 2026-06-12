---
title: "Help - Trouble with DVD::Rip in Karmic"
date: 2010-04-02
forum: General Help
---

### Post by MrCloudHands on 2010-04-02
Hi,

I looked over the tutorial for how to properly install dvd::rip, but I'm having trouble getting version 2.71 of 'rar' to install. 

I referenced this thread ( [http://www.ubuntuforums.org/showthread.php?t=519758]("http://www.ubuntuforums.org/showthread.php?t=519758") ) but I still can't get it installed.

When I enter the fist command in terminal, the output reads:

christian@christian-laptop:~$ chmod +x rarlnx271.sfx.bin
chmod: cannot access `rarlnx271.sfx.bin': No such file or directory

If I could just get this version of rar installed, I think I'd be good. If you happen to know of a better/easier DVD ripping program for 9.10 please let me know.

Thanks.

---

### Post by coffeecat on 2010-04-02
> **MrCloudHands said:**
> If you happen to know of a better/easier DVD ripping program for 9.10 please let me know.

I'm glad you asked that! Yes - use k9copy. It's in the repository and easy to use.

It's a KDE app, so will bring in a load of KDE libraries and will look slightly out of place on a gnome desktop, but it 'just works'. Or rather to get it to 'just work' with commercial DVDs, you need to install libdvdcss2 from Medibuntu. Post if you need more details.

---

### Post by MrCloudHands on 2010-04-02
Thanks for the reply.

If you could elaborate on installing libdvdcss2 that'd be great.

I may have installed it in the process of installing DVD::rip but I'm not sure... 

Thanks

---

### Post by coffeecat on 2010-04-02
> **MrCloudHands said:**
> If you could elaborate on installing libdvdcss2 that'd be great.

Instead of typing it all again, here's one I posted earlier: :)

[http://ubuntuforums.org/showpost.php?p=9065595&postcount=5](http://ubuntuforums.org/showpost.php?p=9065595&postcount=5)

It might be worth installing ubuntu-restricted-extras if you haven't done so already, and check you have libdvdread4 installed, although this will probably get installed as a dependency of k9copy if not already installed.

---

### Post by tobemem on 2010-04-28
> If you happen to know of a better/easier DVD ripping program for 9.10 please let me know.Give ANDREW a chance  ([http://tobemem.memebot.com]("http://tobemem.memebot.com/")): easy to install (all its dependencies are in Ubuntu repositories) and to use (in my own opinion, since I wrote it by myself).

---

### Post by cdavid13 on 2010-04-28
Does anyone know if it is possible to get the files that k9copy makes while backing up your DVD to play on a windows plat form straight from the same external?

---

### Post by tobemem on 2010-04-29
Are yours DVD-Video .iso files? If so, [VLC]("http://www.videolan.org/vlc/") should be able to play them.

---

