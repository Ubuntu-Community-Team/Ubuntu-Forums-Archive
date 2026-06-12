---
title: "libdvdcss2 problems"
date: 2009-12-30
forum: General Help
---

### Post by the_webninja on 2009-12-30
All I wanted for Christmas was an Ubuntu that would play regular Dvds. :)
What I got was a Myriad of BS just trying to download and install libdvdcss2 so I could get my Mediaplayers to play the Dvds. 
The first thing my instructions said was to install everything related to Universe and Multi-verse. So I did, which took around 6 hours! then when the Synaptic Package Manager tried to install all of this BS it Crashed.  Never to Recover again.
I received and error code that said run "sudo dpkg --configure -a" to correct the problem, and when I did that, it just returned "no such command"
Looks to me like the left hand doesn't know what the right hand is doing some where down the line.
The related package that supposedly cause the Problem was something related to a Python-Twist program, whatever that is, when I tried to report the bug it could not report the Bug either. So I figured well I just upgrade to 9.10 maybe that will solve the problem cause I am running 9.04. But when I used the Update manager to try to install 9.10 IT CRASHED Too!

Can't you guys figure out a way to incorporate libdvdcss into Ubuntu already so we don't have to bang our heads against the wall just to try to play Dvds?
It should not be Rocket Science ya know?
Or at least make it appear on the List so we can download it with the Synaptic Package Manager! No one likes having to go through all this BS just to play dvds.

Now I am looking at having to re-install Ubuntu all over again just so things will work right again, reminds me of another Operating System I used to use. :)

---

### Post by thatguruguy on 2009-12-30
Did you follow this handy howto guide? [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Leppie on 2009-12-30
usually to watch dvd's you only have to add the medibuntu repo and install libdvdread4 (which comes with a script to install css) and libdvdcss2.
to install the medibuntu repo:
```
$sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

to install libdvdread4 and libdvdcss2:
```
$sudo apt-get install libdvdread4 libdvdcss2
```

also run:
```
$sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by fragos on 2009-12-30
You can also follow the instructions at the [http://medibuntu.org](http://medibuntu.org) site which will add the Medibuntu repository and allow you to install with Synaptic. There's a lot of good stuff on Medibuntu.

---

### Post by howefield on 2009-12-30
> **the_webninja said:**
> looks to me like the left hand doesn't know what the right hand is doing some where down the line.

Yep, and they are both yours.

> It should not be Rocket Science ya know?

It really isn't ya know.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

