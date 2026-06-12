---
title: "What program can i use to stream TV off the internet?"
date: 2009-10-09
forum: General Help
---

### Post by Jedi_Knight on 2009-10-09
What program can i use to stream TV off the internet? I would love to be able to watch the Cricket on my computer, is there a Ubuntu program that will let me do this? Thanks for any help

---

### Post by MelDJ on 2009-10-09
sopcast. get it at the sopcast website. i am having a server problem with it. might be only me though

---

### Post by akakingess on 2009-10-09
I don't know if you mean like broadcast channels or what, but at least hulu (of hulu.com fame) has released hulu desktop for Ubuntu, now!

---

### Post by t0p on 2009-10-09
> **akakingess said:**
> I don't know if you mean like broadcast channels or what, but at least hulu (of hulu.com fame) has released hulu desktop for Ubuntu, now!

The fact that the OP wants to watch cricket suggests to me that he doesn't live in the USA.  And hulu.com doesn't work outside the USA.  Plus, hulu.com doesn't show live sport broadcasts, I believe.

OP: what TV channel is the cricket on?  You should have a look if that channel streams its programming on its website.  Many channels do this nowadays.

---

### Post by Jedi_Knight on 2009-10-09
> **t0p said:**
> The fact that the OP wants to watch cricket suggests to me that he doesn't live in the USA.  And hulu.com doesn't work outside the USA.  Plus, hulu.com doesn't show live sport broadcasts, I believe.

OP: what TV channel is the cricket on?  You should have a look if that channel streams its programming on its website.  Many channels do this nowadays.

ESPN. I tried installing sopcast, man that was a pain in the ***, im a ubuntu noob and it didnt work. Ill check on espn's website now

---

### Post by MelDJ on 2009-10-09
do you know about this website: [http://www.myp2p.eu/](http://www.myp2p.eu/) ?

---

### Post by Jedi_Knight on 2009-10-09
> **MelDJ said:**
> do you know about this website: [http://www.myp2p.eu/](http://www.myp2p.eu/) ?


Yeah, when i try to watch a channel, it says 'an error occured'

---

### Post by TwinStinger on 2009-10-09
Jedi_Knight

Go to this address:

[http://www.myp2pforum.eu/live-tv/41045-british-tv.html](http://www.myp2pforum.eu/live-tv/41045-british-tv.html)

Download the 32-bit or 64-bit version for linux.

Unpack it and run it from command line.

44 British channels. 

Works fabulous except for a few channels.

Think that you must have vlc-player installed. 

/ Twinned

---

### Post by Jedi_Knight on 2009-10-09
> **TwinStinger said:**
> Jedi_Knight

Go to this address:

[http://www.myp2pforum.eu/live-tv/41045-british-tv.html](http://www.myp2pforum.eu/live-tv/41045-british-tv.html)

Download the 32-bit or 64-bit version for linux.

Unpack it and run it from command line.

44 British channels. 

Works fabulous except for a few channels.

Think that you must have vlc-player installed. 

/ Twinned


Thankyou, worked perfectly. I appreciate it

---

### Post by spursncowboys on 2009-10-11
Justin.tv and Veetle
I'm watching the Cowboys game on Veetle right now and watched the Longhorns last night on Justin.tv

---

### Post by snakedocter on 2009-10-11
Try hobofilm It's a great open source app, works quite nicely. :guitar::popcorn:

---

### Post by polki@mac.com on 2009-10-14
> **TwinStinger said:**
> Jedi_Knight

Go to this address:

[http://www.myp2pforum.eu/live-tv/41045-british-tv.html](http://www.myp2pforum.eu/live-tv/41045-british-tv.html)

Download the 32-bit or 64-bit version for linux.

Unpack it and run it from command line.

44 British channels. 

Works fabulous except for a few channels.

Think that you must have vlc-player installed. 

/ Twinned

Unfortunately it hasn't worked on any of the 9.10 machines I've tested so far. I get this:

```
Compress::Raw::Zlib object version 2.008 does not match bootstrap parameter 2.015 at /usr/lib/perl5/Compress/Raw/Zlib.pm line 97.
Compilation failed in require at /usr/share/perl5/Compress/Zlib.pm line 12.
BEGIN failed--compilation aborted at /usr/share/perl5/Compress/Zlib.pm line 12.
Compilation failed in require at /usr/share/perl5/Archive/Zip.pm line 24.
BEGIN failed--compilation aborted at /usr/share/perl5/Archive/Zip.pm line 24.
Compilation failed in require at -e line 359.
```

Works on 9.04 and OS X Leopard though.

Edit: I should have said they were all 64-bit machines, I tried using the 32-bit programme and it worked! Would like to have it 64-bit, but you can't have everything you want, can you...

---

### Post by e45cream on 2009-11-24
> **polki@mac.com said:**
> Unfortunately it hasn't worked on any of the 9.10 machines I've tested so far. I get this:

```
Compress::Raw::Zlib object version 2.008 does not match bootstrap parameter 2.015 at /usr/lib/perl5/Compress/Raw/Zlib.pm line 97.
Compilation failed in require at /usr/share/perl5/Compress/Zlib.pm line 12.
BEGIN failed--compilation aborted at /usr/share/perl5/Compress/Zlib.pm line 12.
Compilation failed in require at /usr/share/perl5/Archive/Zip.pm line 24.
BEGIN failed--compilation aborted at /usr/share/perl5/Archive/Zip.pm line 24.
Compilation failed in require at -e line 359.
```

Works on 9.04 and OS X Leopard though.

Edit: I should have said they were all 64-bit machines, I tried using the 32-bit programme and it worked! Would like to have it 64-bit, but you can't have everything you want, can you...

I managed to get the 64-bit version working on Karmic by installing the Jaunty version (2.015) of libcompress-raw-zlib-perl from [here]("http://packages.ubuntu.com/jaunty/amd64/libcompress-raw-zlib-perl/download"). Then using Synaptic, force the package version to 2.015 to prevent it being updated to the new 2.020 package.

---

### Post by flyguy97 on 2009-12-07
> **Jedi_Knight said:**
> ESPN. I tried installing sopcast, man that was a pain in the ***, im a ubuntu noob and it didnt work. Ill check on espn's website now

I'm sorry your first impression with Sopcast was a negative one. I created a PPA that will ease the installation of Sopcast and a GUI program that I created called SopCast Player. Go to [http://code.google.com/p/sopcast-player/wiki/Installation]("http://code.google.com/p/sopcast-player/wiki/Installation") for instructions on how to get everything working.

Cheers,
Jason

---

