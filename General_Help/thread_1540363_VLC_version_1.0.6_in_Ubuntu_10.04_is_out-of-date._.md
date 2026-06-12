---
title: "VLC version 1.0.6 in Ubuntu 10.04 is out-of-date. We recommend you install VLC 1.1.x"
date: 2010-07-27
forum: General Help
---

### Post by finny388 on 2010-07-27
I was about to install VLC in Synaptic when I got curious about what the newest version is.

Then I found the message about VLC recommending against using the version in the Ubuntu repositories.

**[Note that there will be some bugs; you are on your own. (link)]("http://www.videolan.org/vlc/download-ubuntu.html")**

I'm not sure if this is common knowledge but there it is.

Aside from spreading the word, I have one question:

How do I install VLC 1.1.x manually? The site doesn't say as far as I can tell.

thanks

---

### Post by Vaphell on 2010-07-27
you can always add this to sources and then update stuff via synaptic
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

### Post by finny388 on 2010-07-27
Thanks Vaphell

The following did the trick:

*Add repository*
**sudo add-apt-repository ppa:c-korn/vlc**

*Update repositories*
**sudo apt-get update**

*Uninstall VLC (if necessary)*
**sudo apt-get purge vlc vlc-nox mozilla-plugin-vlc vlc-plugin-pulse**

*Install new VLC*
**sudo apt-get install vlc vlc-nox mozilla-plugin-vlc vlc-plugin-pulse**

---

### Post by mc4man on 2010-07-27
vlc always has bugs - sometimes of consequence, sometimes not so much..
1.1.0 has some bugs - that's why there is a 1.1.1

---

### Post by b_k_chu on 2010-07-28
i'm also trying to upgrade to the latest VLC....or anything 1.0.x or above.  but i'm still on Intrepid.....and so far, no luck at all in finding any clear indication of what repository i can use.

tried adding these to my Software Sources:
[FONT=monospace]deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main 

that only got me up to VLC 0.9.9.

tried following the solution above:
[/FONT]> **finny388 said:**
> The following did the trick:

*Add repository*
**sudo add-apt-repository ppa:c-korn/vlc**

that only got me an error:
sudo: add-apt-repository: command not found

...which i assume is because i'm not on Lucid like OP.

does anyone have any pointers?

---

### Post by NFblaze on 2010-07-28
The PPA only supports Intrepid up until 9.9

SO change your lines of:
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) intrepid main

To something that is supported, such as Lucid.

---

### Post by b_k_chu on 2010-07-28
i thought of trying that, but i can't help but wonder -- could it end up breaking something on my system, trying to install a package (w/ dependencies) that wasn't built for it?

---

### Post by finny388 on 2010-07-29
b_k_chu, I've removed SOLVED status of this thread to open it up to others to address your issue (at least visually)

Please post your results. If there's no response in a week or so I'll turn it back to solved.

thanks

p.s.
why are you still using intrepid?
I'm running lucid on a pretty weak system with no problems.

---

### Post by b_k_chu on 2010-08-03
sorry, haven't checked back for a few days.

but i did manage to get a 1.0 version of VLC running on my system.  

cutting and pasting my solution from another thread:

[QUOTE=b_k_chu]
-update-
 
 adding these repos got me up to 1.0.0-rc2:
 deb [http://ppa.launchpad.net/moviemaniac/ppa/ubuntu](http://ppa.launchpad.net/moviemaniac/ppa/ubuntu) intrepid main
 deb-src [http://ppa.launchpad.net/moviemaniac/ppa/ubuntu](http://ppa.launchpad.net/moviemaniac/ppa/ubuntu) intrepid main
 
 ....which at least gets me the one feature i was looking for: the ability to advance a vid frame by frame. :3
 
 edit: oops, forgot to note the key to be added for the above repos -- 
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1501599E
[/QUOTE]

p.s.
as to why i'm still on intrepid?

1) i'm lazy. :3

2) i don't have a backup of all my stuff in case something goes wrong and the system breaks.  though to me it seems simpler to just wipe the hdd and do a clean install of a newer distro.....but still, no backup.

---

### Post by finny388 on 2010-08-03
**Re: VLC**

Congrats on getting 1.0.0 running. I'll mark this solved.

**Re: Lucid/Intrepid**

If you have a separate partition or second hard drive you can tell Ubuntu to use that as the Home directory (during install :(  )

If you do that, your subsequent clean installs will preserve not only your documents but application settings.

I was so pleased to find this out. Firefox had all my bookmarks and settings etc. I was ready to restore them all but it was all there!

I initially set that up during a clean install. Doing it retroactively was a fail for me but some gurus out there may be able to tell you how to migrate it. (of course if you want to inquire about that start a new thread)

Cheers! :D

---

### Post by ThomasTheTan on 2010-08-28
Just as an update (in case anybody else finds this thread):

The repository suggested earlier no longer exists, and running the command
```

sudo add-apt-repository ppa:c-korn/vlc
```produces an error message.

The newest version of vlc can now be found at a different repository.

Replace the above command with the following:
```
sudo add-apt-repository ppa:ferramroberto/linuxfreedomlucid
```and that should do the trick!

[Here]("http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html") is where I got this information.

---

### Post by finny388 on 2010-08-29
Thank you Thomasthetan

I noticed that recently too but couldn't find where to go.

It's a wonder that VLC themselves don't host a repository.

---

### Post by andrew.46 on 2010-08-29
Hi finny,

> **finny388 said:**
> It's a wonder that VLC themselves don't host a repository.

Have a look at the various comments by Rémi Denis-Courmont [in this thread]("http://forum.videolan.org/viewtopic.php?f=13&t=81146&start=0&hilit=linux+windows"). He spells out the problems quite nicely I think...

Andrew

---

