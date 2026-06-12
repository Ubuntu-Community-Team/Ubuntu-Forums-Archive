---
title: "Gnome hangs on login"
date: 2006-04-11
forum: General Help
---

### Post by AaronWyatt on 2006-04-11
Hi all,

I newly installed Breezy Badger a few days ago, and all worked fine until I updated all the packages.  The next time I turned on my system and tried to log on, gnome hung.  I get the brown gradient background with a mouse cursor that moves.  Ctrl-alt-backspace brings me back to a login screen, and the failsafe gnome does the same thing.

I'll post some info from the error logs tomorrow (I had forgotten where to look, though now I know to browse /var/log. I'm at work right now.)  In the meantime, does anyone have an idea or three what may be causing this?  Is anyone having a similar issue?  Also, is there anything I should check out besides the logs?

Thanks for all your help.

P.S.
apt-get can't find package 'lynx'.  What's an easy way for me to find and install it from the command line?

---

### Post by earobinson on 2006-04-11
It could be an error about how gnome cant write to a file, if thats it log on to just the terminal (ctrl alt f1) at the log on screen and chmod (man chmod for more info) the file so that you can write to it again

---

### Post by nolihc on 2006-04-11
I've had the same problem. In my case it was the network name...

---

### Post by AaronWyatt on 2006-04-11
Wow!  That's the fastest reply I've ever gotten on any support forum anywhere.  And with such little to go on, I'm impressed.  Thanks, earobinson.

---

### Post by AaronWyatt on 2006-04-11
[QUOTE=nolihc]I've had the same problem. In my case it was the network name...[/QUOTE]

Can you elaborate, nolihc?  What did you do to fix it?

One thing I had to do after installing (to make sudo work) was append /etc/hosts with my machine's name, although everything seemed to work fine afterwards...

---

### Post by plumcreek on 2006-04-11
lynx is in the main repository, so if apt-get can't find it, I would guess there are networking issues in play.

Have you had trouble installing anything else vi apt-get?

---

### Post by nolihc on 2006-04-11
i've also corrected some hosts files

---

### Post by earobinson on 2006-04-11
[QUOTE=AaronWyatt]Wow!  That's the fastest reply I've ever gotten on any support forum anywhere.  And with such little to go on, I'm impressed.  Thanks, earobinson.[/QUOTE]

Only to happy to help, however it could be something else (I see talk of a netowrk name below) Its just a guess cuz it is a problem I had after updating once!

---

### Post by AaronWyatt on 2006-04-11
[QUOTE=plumcreek]lynx is in the main repository, so if apt-get can't find it, I would guess there are networking issues in play.

Have you had trouble installing anything else vi apt-get?[/QUOTE]

I used apt-get update and apt-get upgrade to update the whole system...  I followed the directions here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories),
and afterwards I got a message something like (from memory, mind you): 

```

could not connect to
http://ubuntu-backports.mirrormax.net/hoary-backports/main/universe/multiverse/restricted
http://ubuntu-backports.mirrormax.net/hoary-extras/main/universe/multiverse/restricted
```

I didn't worry too much about it because I know those are optional repositories.

---

### Post by earobinson on 2006-04-11
that just means exactly what it says, it cant connect to the repo

---

### Post by psychicdragon on 2006-04-11
[QUOTE=AaronWyatt]I used apt-get update and apt-get upgrade to update the whole system...  I followed the directions here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories),
and afterwards I got a message something like (from memory, mind you): 

```

could not connect to
http://ubuntu-backports.mirrormax.net/hoary-backports/main/universe/multiverse/restricted
http://ubuntu-backports.mirrormax.net/hoary-extras/main/universe/multiverse/restricted
```

I didn't worry too much about it because I know those are optional repositories.[/QUOTE]
The information on the ubuntuguide.org site is really out of date now. It hasn't been modified since before Breezy was released. The guy who was maintaining the site just dissappeared one day. 

The backports repositories have been made official now, the new urls are as follows:

```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

