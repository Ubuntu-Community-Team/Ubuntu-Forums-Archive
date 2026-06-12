---
title: "[Ubuntu/elementaryOS] Can't create a makefile :("
date: 2011-06-18
forum: General Help
---

### Post by redbullcat/ctdp on 2011-06-18
Hi guys,

I'm new here, please don't shout at me :)

Basically, I'm using elementary OS (based on 10.10 Maverick). I'm trying to install rhythm-e but everytime I type either ./autogen.sh or ./configure after following some instructions, it comes with an error:

> make: *** No targets specified and no makefile found. Stop.

I've already followed 3 different threads here to try and find the answer, but nothing is working. I've attached the outputs from ./autogen.sh and ./configure below. I've run both commands as sudo too, same output. I'm really stumped by this problem, a lot of the time I can quite easily install things from source :(

The instructions I used are here:

> Remove rhythmbox completely from your system

sudo apt-get remove rhythmbox rhythmbox-dbg rhythmbox-dev rhythmbox-plugin-cdrecorder rhythmbox-plugin-coherence rhythmbox-plugins

And then use these commands. :D

sudo apt-get build-dep rhythmbox

bzr branch lp:rhythm-e

cd rhythm-e

./autogen.sh

make

sudo make install

These look correct enough to me, but I've followed them to the letter twice and it doesn't work. So could somebody shed some light on where I'm going wrong?

Here are the output files: [Clicky!]("http://www.mediafire.com/?ld0ca7d0574za3a") For some reason it wouldn't let me attach them here, so I put them on mediafire for you :)

Thanks very much for your help

Phil :)

I would have put this in the Installation and Upgrades forum, but I think my post count most be too low :(

---

### Post by redbullcat/ctdp on 2011-06-18
No one?

---

