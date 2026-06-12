---
title: "Buoh Comic Strip Reader"
date: 2009-08-01
forum: General Help
---

### Post by iheartubuntu on 2009-08-01
I just wanted to thank Mike who posted about the "Buoh" comic strip reader in a thread here: [http://ubuntuforums.org/showthread.php?t=312714](http://ubuntuforums.org/showthread.php?t=312714)

Unfortunately, a mod closed down the thread, but luckily Mike was able to respond with this great program beforehand. Ive tried out all the other programs, without much luck. There just isnt any good simple, nice looking readers out there. Comix is great for zipped up comic books, but I was looking specifically for a comic strip reader, the kind of comics found in newspapers like Ziggy, Family Circus, Garfield, Dick Tracy, etc.

Buoh was the easiest to get going (they have a DEB file), but even better yet, they have a newer version in the Synaptic Package Manager. Just search for it by typing in "buoh", then installing.

Nice simple program. Select the comic strips you want and bingo. Easy as pie. Plus its gnome, so the program itself is easy on the eyes (unlike some of the older programs for linux out there).

Buoh Comic Strip Reader...

[http://buoh.steve-o.org/index.html](http://buoh.steve-o.org/index.html)

If anyone knows of a better oen than this, please post. Thanks!

---

### Post by dsfitzpat on 2009-11-02
I've also enjoyed this program for the last couple of years.  Unfortunately, it's been removed from the repositories in 9.10!  Probably this is because it doesn't appear to have been maintained since 2006, and chances are it depends on out-of-date libraries.

---

### Post by theonlyandy on 2009-11-28
It's unfortunately not in the repos anymore, but still you can install the .deb on 9.10.

---

### Post by outerspacerace on 2009-12-08
It's a shame no one is working regularly on this project, I can't find any better alternatives.

That and the .deb installs but the program won't open in karmic for me.

Com on coders! Just a few tweaks could bring it back to life and improve it no end.

---

### Post by littlepeon on 2010-03-23
its part of launchpad now

[https://launchpad.net/ubuntu/karmic/+source/buoh](https://launchpad.net/ubuntu/karmic/+source/buoh)


edit: nevermind.....

could have sworn i got it from launchpad............
i have it on one of my karmic machines..but i dont know where it came from........
perhaps i compiled it....
odd....its on one of my older machines...and i dont compile much on that 'puter will check around

---

### Post by littlepeon on 2010-03-27
k figured out how my one karmic system has buoh installed...

it came packaged with its two dependencies....

libgnutls13_2.0.4-1ubuntu2.6 and it's dependency libopencdk10_0.6.6-1ubuntu1

install script installs buoh by installing libopencdk, then libgnutls then buoh......

don't know why these aren't included in karmic...

what reprocussions might i encouter by having these two outdated (they were in intreped and jaunty) libraries????!!?????

---

### Post by inzaneg on 2010-04-10
I didn't have any problems installing Buoh on Karmic, I used this package [http://ubuntu.uib.no/archive/pool/universe/b/buoh/buoh_0.8.2-0ubuntu2_i386.deb](http://ubuntu.uib.no/archive/pool/universe/b/buoh/buoh_0.8.2-0ubuntu2_i386.deb).

Just installed the same package on Lucid and it asked for this also.[http://se.archive.ubuntu.com/ubuntu/pool/universe/libs/libsoup/libsoup2.2-8_2.2.105-4ubuntu1_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/universe/libs/libsoup/libsoup2.2-8_2.2.105-4ubuntu1_i386.deb) 

Works great :)

I've edited in my own localized cartoons to the Buoh list by editing this:
sudo gedit /usr/share/buoh/comics/comics.xml
I looked on one of the other cartoons in the .xml, and found out that way how to add my own.

---

### Post by dsfitzpat on 2010-04-11
OK, thanks for the tip.  The 32-bit version won't run on my machine but I'll see if there's a 64-bit version in the same location.
I suppose I could get it off of one of the Debian repositories too - but it would be nice to have something that was (a) still supported (b) in the repos.

---

### Post by inzaneg on 2010-04-12
Yeah, I agree. I was annoyed when I couldn't apt-get Buoh anymore.
But it's still the best for viewing web comics, and after I added to the .xml it's even better.

I'm willing to go the extra mile for Buoh.

---

### Post by Phil Hansen on 2010-05-12
I have upgraded to 10:04 and missed Buoh.
Thanks for the tips.
It is now working again.
Phil

---

