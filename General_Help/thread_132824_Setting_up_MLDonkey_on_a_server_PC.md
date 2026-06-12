---
title: "Setting up MLDonkey on a server PC?"
date: 2006-02-19
forum: General Help
---

### Post by LxP on 2006-02-19
Hi all,

I like to download from BitTorrent and eDonkey networks. I have a Ubuntu computer that's always on and always connected to the internet. I am therefore led to believe that I'd like to set up **MLDonkey** on that computer.

If no one can think of better software for this task, would anyone be kind enough to lend a helping hand? So far I've managed to install **mldonkey-server** through Synaptic and start it as a daemon, but from there I'm lost.

[One thread asking for similar advice](http://ubuntuforums.org/showthread.php?t=91396) points to [an external page discussing configuration](http://talk.trekweb.com/~jasonb/articles/mldonkey_linux.shtml), however it doesn't seem to apply to the version of mldonkey-server that I have because a few of the options there (such as *http_login* and *http_password*) don't exist in my configuration files.

Another post from that thread gives a brief tutorial which involves running mlnet while logged in, but that doesn't seem to be what I want (I don't want to have to be logged into the server PC all the time to have MLDonkey working). **aMule** is also discussed, but as aMule's site is currently down I can't determine whether it offers the same functionality.

Thanks very much for any help that you can give. (Please let me know if I haven't chosen the correct forum to post this!)

**Edit:** Typo.

---

### Post by LxP on 2006-02-21
Surely the idea of a 24/7 connection to P2P networks regardless of who's currently logged in (to that computer) must appeal to others?

Think about the long time that it can take to find sources, reach the front of queues and ultimately download those less common downloads -- particularly when you log in and out which would take you out of any queues. By being connected all of the time, that's no longer a problem. Think about how much more you could download! ;)

Any takers at all?

---

### Post by slazh on 2006-02-21
[QUOTE=LxP]
Another post from that thread gives a brief tutorial which involves running mlnet while logged in, but that doesn't seem to be what I want (I don't want to have to be logged into the server PC all the time to have MLDonkey working). 
[/QUOTE]
One solution to this, is logging in, start a screen session and in that screensession you could run mlnet. The nice thing about screen is that you can detach this session. Your program keeps running, but you can logout!

For a nice introduction to screen;
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

Screen kan be installed trough Synaptic / Apt.

---

### Post by LxP on 2006-03-04
> **slazh]One solution to this, is logging in, start a screen session and in that screensession you could run mlnet. The nice thing about screen is that you can detach this session. Your program keeps running, but you can logout!

For a nice introduction to screen said:**
> http://www.kuro5hin.org/story/2004/3/9/16838/14935[/url]

Screen kan be installed trough Synaptic / Apt.
Thanks slazh! This was exactly the info I needed to get up and running.

One extra advantage to this approach is that I can run mlnet under my own username, so configuration files and downloads are only accessible to me.

---

### Post by bugmenot on 2006-03-08
The alternative is of course to have it running as an init.d system daemon.

Just activate it by configuring with "sudo dpkg-reconfigure -plow mldonkey-server"

(-plow is "ask all kinds of low priority questions")

I recommend using mldonkey as the user and either 0022 as the file mask. The files (config, temp and incoming) will be stored in /var/lib/mldonkey. Only the user and group members "mldonkey" will have access.

Is there an advantage? It will be restarted in case of crashes (rare?) and autostarted on system boot. It's safer to chroot everything and run as the non-porivileged user "mldonkey".

You can of course move/change the incoming if the storage space is somwhere else ...


[Edit:] Take note that your current config in your home directory will not be used when run from /var/lib/mldonkey though

---

### Post by MJSOnline on 2006-03-09
Hi.  Just a question.  Can the above be applied to the use of Azureus?  So I can make a server to download files to and still control it from a laptop?  What do I need on the server and laptop?  Thanks. M

---

