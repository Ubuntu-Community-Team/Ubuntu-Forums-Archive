---
title: "Audacity Install Problem"
date: 2009-12-18
forum: General Help
---

### Post by Coda_ on 2009-12-18
...I tried to download Audacity (Karmic Koala here)...I used the terminal and typed in 

> sudo apt-get install audacity...after asking me for my password, this came up...
> Package Audacity not available, but is refered to by another package. This may mean that a package is missing,has been obsoluted or is only available from another source. However the following packages to replace it: audacity-data
E: Package audacity has no installation canidate...what does that mean?...

---

### Post by audiomick on 2009-12-18
Have you tried installing via synaptic package manager or the software centre?

---

### Post by howefield on 2009-12-18
Assuming you mean you typed

```
sudo apt-get install Audacity
```

Try it again with lower case, audacity ie,

```
sudo apt-get install audacity
```

---

### Post by Coda_ on 2009-12-18
> **howefield said:**
> Assuming you mean you typed

```
sudo apt-get install Audacity
```Try it again with lower case, audacity ie,

```
sudo apt-get install audacity
```

...yea, I edited it...I ment to say audacity, I tried the package manager too, and it wasnt finding anything...

---

### Post by Leppie on 2009-12-18
i believe in karmic it's audacity2.
do a search with apt:
```
$apt-cache search audacity
```

this will show you which audacity versions are available for installation.

you may also have to [add the medibuntu repo]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by Leppie on 2009-12-18
Sorry, i found audacity in my cache...

---

### Post by howefield on 2009-12-18
Check your universe repository is enabled, (Synaptic > Settings > Repositories > Ubuntu Software tab. Then reload.


Or, the package in Karmic is available here,

[http://packages.ubuntu.com/karmic/audacity](http://packages.ubuntu.com/karmic/audacity)



Near the bottom of the page, select your download, whether 32 or 64 bit. You could try downloading and installing the package.

---

### Post by Coda_ on 2009-12-18
> **Leppie said:**
> i believe in karmic it's audacity2.
do a search with apt:
```
$apt-cache search audacity
```this will show you which audacity versions are available for installation.

you may also have to [add the medibuntu repo]("https://help.ubuntu.com/community/Medibuntu").

...I got this...
> No command '-cache' found 

---

### Post by howefield on 2009-12-18
> **Leppie said:**
> Sorry, just found out it's audacious now...

You sure, lol ?

> Audacious is a fork of beep-media-player which supports winamp skins
and many codecs.

In the default install, the following codecs are supported:

 * MP3
 * Ogg Vorbis
 * AAC and AAC+
 * FLAC
 * Windows Media (WMA)
 * Musepack
 * TTA
 * Many module formats and much more!

Additionally, Audacious is extendable through plugins, and contains
other useful features like LIRC support and support for last.fm.

This package contains the core player and its localization.

Canonical does not provide updates for audacious. Some updates may be provided by the Ubuntu community.

---

### Post by Coda_ on 2009-12-18
> **howefield said:**
> Check your universe repository is enabled, (Synaptic > Settings > Repositories > Ubuntu Software tab. Then reload.


Or, the package in Karmic is available here,

[http://packages.ubuntu.com/karmic/audacity](http://packages.ubuntu.com/karmic/audacity)



Near the bottom of the page, select your download, whether 32 or 64 bit. You could try downloading and installing the package.

...I downloaded that, and on the package installer, it says
> Error: wrong architecture 'amd64' 

---

### Post by Leppie on 2009-12-18
did you install 32bit ubuntu on your x64 machine?

---

### Post by howefield on 2009-12-18
> **Coda_ said:**
> ...I downloaded that, and on the package installer, it says... Error: wrong architecture 'amd64'

So,... you need the other one then :)

---

### Post by Leppie on 2009-12-18
> **howefield said:**
> You sure, lol ?

haha... nope, just sleepy... ;)

---

### Post by Coda_ on 2009-12-18
> **howefield said:**
> So,... you need the other one then :)

...I did that and got...
> Error: Dependency is not satisfiable :audacity-data (=1.3.9.6)

---

### Post by howefield on 2009-12-18
> **Leppie said:**
> haha... nope, just sleepy... ;)

Well have some then... you'll feel better when you wake up ;)

---

### Post by howefield on 2009-12-18
> **Coda_ said:**
> ...I did that and got...

[http://packages.ubuntu.com/karmic/audacity-data](http://packages.ubuntu.com/karmic/audacity-data)

---

### Post by Coda_ on 2009-12-18
> **howefield said:**
> [http://packages.ubuntu.com/karmic/audacity-data](http://packages.ubuntu.com/karmic/audacity-data)

...alright, that worked, but where did it install it to?...am I missing a step?...

---

### Post by howefield on 2009-12-18
> **Coda_ said:**
> ...alright, that worked, but where did it install it to?...am I missing a step?...

So you have done audacity-data and audacity ?

You should have a menu icon under Applications > Sound & Video > Audacity

---

### Post by Leppie on 2009-12-18
You may actually be interested in [this doc]("https://help.ubuntu.com/community/Repositories/Ubuntu"), it shows you how to enable/disable repos.

---

### Post by Coda_ on 2009-12-18
> **howefield said:**
> So you have done audacity-data and audacity ?

You should have a menu icon under Applications > Sound & Video > Audacity

...yea, It says everything was installed, but theres no menu Icon...

---

### Post by dcstar on 2009-12-19
> **Coda_ said:**
> ...yea, It says everything was installed, but theres no menu Icon...

Log out and log in again.

---

### Post by Coda_ on 2009-12-19
> **dcstar said:**
> Log out and log in again.

...still nothing...although, Ive been having shutdown problems, a screen comes up and says that is shutting down or whatever, and then an error comes up, and it freezes...I dont know if its related or not...

---

### Post by Leppie on 2009-12-19
> **Coda_ said:**
> ...still nothing...although, Ive been having shutdown problems, a screen comes up and says that is shutting down or whatever, and then an error comes up, and it freezes...I dont know if its related or not...

well, it doesn't seem normal...
what is the error? and when it freezes, what do you do?

---

### Post by Coda_ on 2009-12-19
> **Leppie said:**
> well, it doesn't seem normal...
what is the error? and when it freezes, what do you do?

> ubuntu login : [8875.470892] Buffer I/O error on device loop0, logical block 350075
[9975.471779] buffer on device loop0, logical block 2021381
[8875.472683] buffer on device loop0, logical block 3555362
[8875.473495] buffer on device loop0, logical block 3555327
[8880.000529] aborting journal on device loop0
[8880.000639] buffer on device loop0, logical block 2097666
[8905.860107] buffer on device loop0, logical block 2425994

...then it just sits there, freezes up, so I force shutdown...

---

