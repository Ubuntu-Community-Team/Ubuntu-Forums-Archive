---
title: "Control Volume from terminal"
date: 2010-06-22
forum: General Help
---

### Post by hakermania on 2010-06-22
i don't want alsamixer. I want a command, e.g. setsound 98 (this will set sound to 98%) or something like this. Is there any?

---

### Post by WorMzy on 2010-06-22
I guess you're using OSS then? Try [ossmix]("http://manuals.opensound.com/usersguide/ossmix.html").

Oh wait, do you mean you're using ALSA, but don't want to use alsamixer? Try amixer. (man amixer)

---

### Post by kgas on 2010-06-22
try with amixer. Details man amixer or see [this](http://www.digipedia.pl/man/doc/view/amixer.1/).

---

### Post by justleen on 2010-06-22
if you just want a command to change setting, use amixer

```

#get list of controls
$ amixer scontrols   
Simple mixer control 'Master',**0**

$amixer controls
numid=17,iface=MIXER,name='**Master Playback Volume**'

#set items
$ amixer **-c 0** -- sset **Master Playback Volume** 60%

```
Note the text in bold,first commands give the info needed to set the values for.

---

### Post by hakermania on 2010-06-22
Cool thank you!

---

