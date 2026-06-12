---
title: "rhythmbox not obtaining album art"
date: 2009-10-23
forum: General Help
---

### Post by vavoem on 2009-10-23
Well basically the title says it all

---

### Post by P4man on 2009-10-23
I believe its an issue with Amazon no longer allowing  fetching of cover art unless you have a login there.
You can try Exaile which can fetch covers from LastFM

---

### Post by howefield on 2009-10-23
> **vavoem said:**
> Well basically the title says it all

Well, in that case, are you making a statement or asking a question ?

---

### Post by P4man on 2009-10-23
Actually, I just tried Rhythmbox 0.12.5 here (on Karmic) and it does fetch cover art again

---

### Post by vavoem on 2009-10-23
not a statement more like a finding.
I was wandering if anyone experiences the same issue and might have a solution for it.
I'm quite happy with rhythmbox so i do not want to switch over to any other player.
In the meanwhile I read something about amazon having updated their stuff and therefore the album covers are not properly retrieved any longer.
I also found an apparent solution but haven't a clue on how to install it.
[https://bugzilla.gnome.org/attachment.cgi?id=108913&action=edit](https://bugzilla.gnome.org/attachment.cgi?id=108913&action=edit)

Anyone an idea?

---

### Post by howefield on 2009-10-23
> **vavoem said:**
> not a statement more like a finding.
I was wandering if anyone experiences the same issue and might have a solution for it.

ok,

---

### Post by P4man on 2009-10-23
> **vavoem said:**
> 
I also found an apparent solution but haven't a clue on how to install it.
[https://bugzilla.gnome.org/attachment.cgi?id=108913&action=edit](https://bugzilla.gnome.org/attachment.cgi?id=108913&action=edit)

Anyone an idea?

Yeah. ignore that. Its an old patch already incorporated in the current version. I think Amazon changed their stuff again since then.
Anyway since it seems to work with mine, id say upgrade your rhythmbox manually to the latest release, or switch to karmic next week.

---

### Post by vavoem on 2009-10-23
well the latest version has some libsoup2.4 dependency issues
I'm busy building 0.12.1 now hope it is solved in that version.
I'm a bit reluctant on installing karmic right away.
I installed it on my lappie for testing purposed that all went well but this pc is used by my wife and if it doesn work she'll nag me.

And you're right 0.12.5 on karmic indeed fetches the covers again.

---

### Post by vinutux on 2009-10-23
Album art fetcher based on amazon is very bad idea......coz they changed it frequently ..based on google images search or lastfm are better options.................

---

### Post by vavoem on 2009-10-23
shame to say it is not and i cannot compile newer versions because it has issues with the libsoup2.4 stuff
here is the relevant output of ./configure
libsoup is installed so i'm kinda stuck.
anyone any ideas?

```

checking for RHYTHMBOX... configure: error: Package requirements (		  gtk+-2.0 >= 2.12.0					  glib-2.0 >= 2.16.0	  gio-2.0 >= 2.16.0					  gio-unix-2.0 >= 2.16.0  gnome-media-profiles >= 2.8 		  libsoup-2.4 >= 2.26.0			  libsoup-gnome-2.4 >= 2.26.0			  ) were not met:

No package 'libsoup-gnome-2.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by blur xc on 2009-10-23
I switched to Banshee...  that did the trick and was only two typed words away-

```
install banshee
```

(I have aliases- install="sudo apt-get install")

BM

---

### Post by vinutux on 2009-10-23
> **blur xc said:**
> I switched to Banshee...  that did the trick and was only two typed words away-

```
install banshee
```

(I have aliases- install="sudo apt-get install")

BM

+ 1 for banshee ```
sudo apt-get install banshee
```

---

### Post by vavoem on 2009-10-25
Although banshee might work fine it is not a solution but a workaround.
I have over 15000 music files and have been busy rating them and all.
I don see how switching over to another player is going to solve that.

If rather hope someone has the knowledge to explain to me how i can overcome the libsoup issues so i can compile the 0.12.5 version.

---

### Post by P4man on 2009-10-25
rather than compiling, just fetch the .deb here:
[http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox)

---

### Post by vavoem on 2009-10-25
thanx p4man that helped.

---

### Post by Deverell on 2009-11-03
> **vinutux said:**
> Album art fetcher based on amazon is very bad idea......coz they changed it frequently ..based on google images search or lastfm are better options.................

How do you change it to use LastFM or Google Image Search?

---

