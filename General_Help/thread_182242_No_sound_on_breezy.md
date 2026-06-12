---
title: "No sound on breezy"
date: 2006-05-25
forum: General Help
---

### Post by core on 2006-05-25
Hi all.
I'm on this desktop trying to get sound to work but no success.
I've tried the gnome sound fix from automatix, but nothing changed.
I've changed /etc/esound/esd.conf to look like

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Also, lsof /dev/snd/* and lsof /dev/dsp displays nothing.

Beep media player seems to play fine, it's just I don't hear anything.
Speakers are connected, as I hear fine from them on windows.

Alsa mixer is ok i guess, master, mm and pcm are not muted and in the maximum volume.

I've checked a dozen of posts but the problem remains.

Any help? Suggestions? Thanks.

---

### Post by johnc4510 on 2006-05-25
You might try this web site:
[http://linux-sound.org/](http://linux-sound.org/)
Click on Hardware + Linux, you can then enter your sound card to see if it is supported

---

### Post by core on 2006-05-25
Mine is SiS 740 and is listed there. I don't get it. I got some instructions on the site involving recompiling the kernel. That's something i've never done and i'm affraid of what could happen.
Any advice? Why doesn't this soundcard work by default? Have I done anything wrong?

---

### Post by core on 2006-05-25
I've found, in /usr/src, a file named alsa-driver.tar.gz. I've followed more or less the commands here: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+745.&chip=SI7012&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+745.&chip=SI7012&module=intel8x0)

but i got an error on ./configure:

(...)
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

does this have anything to do with the fact that I upgraded my kernel? but everything freezes on starting ubuntu with the new kernel, so i'm using the old one.

I'm sorry for being so not-specific, i'm yet kinda noob about linux :p

Thanks in advance for all you help.

---

### Post by chakkid on 2006-05-26
Yo, guys.:p My first new image is on, no more freezes, i'm using it right now.

But there's a strange thing on turn off the computer and reboot, it gives OK, but it's a thing about aumix and mixer.

It says like this:

(...)
aumix will not touch mixer

There is another thing too, that gives FAIL, but my brother says that it haves no problem.

It says like this:

(...)
Stopping PostgreSQL database server:main
Error: cluster is not running

                                                                                                                                                                               [[COLOR="Red"]Fail[/COLOR]]


PS: my nickname changed because it has my brother that post the other posts.

---

### Post by chakkid on 2006-05-26
MAN, my problem is solved. I buyed a new desk and then, i iniciated Ubuntu and i heard the beginning of the sound of logon. I think that the problem has the connection of one and another column.

I can take away this topic?

PS: :) :p :cool: :) :p :cool: :KS ;)

---

