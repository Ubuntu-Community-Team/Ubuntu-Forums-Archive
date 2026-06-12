---
title: "64bit or 32bit ubuntu 10.04?"
date: 2010-04-29
forum: General Help
---

### Post by StormRoBoT2 on 2010-04-29
hi, im using core i7 processor on my laptop with nvidia GeForce GTX 260M,

should i use 64bit or 32bit? will all 32bit application work on 64bit without problem? 

like wine?

---

### Post by howefield on 2010-04-29
> **StormRoBoT2 said:**
> should i use 64bit or 32bit? will all 32bit application work on 64bit without problem? 

like wine?

There are very few applications not supported with 64 bit versions, and 32 bit versions can generally be installed in a 64 bit system.

Wine will work fine.

---

### Post by arrrghhh on 2010-04-29
There was a conversation just a few threads back about this...

Essentially yes, go 64-bit.  Everything is going in that direction, and I don't think the app compatibility is so atrocious now.  Flash used to be a big headache, but it's gotten a lot better as I understand it.

Plus, if you have more than 4GB of RAM, 32-bit is just going to ignore anything over I think 3.5GB.

---

### Post by StormRoBoT2 on 2010-04-29
how about my graphic card driver? will there be any problem?

---

### Post by arrrghhh on 2010-04-29
Shouldn't be.  Run the LiveCD if you're unsure.

---

### Post by ttshivers on 2010-04-29
> **StormRoBoT2 said:**
> hi, im using core i7 processor on my laptop with nvidia GeForce GTX 260M,
 
should i use 64bit or 32bit? will all 32bit application work on 64bit without problem? 
 
like wine?
 
Definately use 64 bit.  Thats what I use.

---

### Post by howefield on 2010-04-29
> **StormRoBoT2 said:**
> how about my graphic card driver? will there be any problem?

Shouldn't be an issue. Anything I've seen on this card says it's fine with Ubuntu.

If it runs in 32 bit, it'll run 64 bit.

---

### Post by jesuisbenjamin on 2010-04-29
There are already interesting threads on the matter:
[http://ubuntuforums.org/showthread.php?t=502754](http://ubuntuforums.org/showthread.php?t=502754)
and
[http://ubuntuforums.org/showthread.php?t=403064](http://ubuntuforums.org/showthread.php?t=403064)

Good luck.
B.

---

### Post by StormRoBoT2 on 2010-04-29
any one can give me a guild on how to install java on ubuntu 64bit? ubuntu 10.04 64bit

---

### Post by itachisxeyes on 2010-04-29
> **StormRoBoT2 said:**
> hi, im using core i7 processor on my laptop with nvidia GeForce GTX 260M,

should i use 64bit or 32bit? will all 32bit application work on 64bit without problem? 

like wine?

i'm running the amd64 version right now. and its wonderful. i had some issues with amd64 back with 9.10 and ended up just using 80x86 but they really worked all the kinks out with 10.04 (^_^) go for it!

---

### Post by itachisxeyes on 2010-04-29
> **StormRoBoT2 said:**
> any one can give me a guild on how to install java on ubuntu 64bit? ubuntu 10.04 64bit

try:
```
sudo apt-get install ubuntu-restricted-extras
```if you look here: [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)
it has icedtea which will run java applets as well as java and other goodes XD

---

### Post by StormRoBoT2 on 2010-04-29
is that all? 

do i need to install any other thing? is this full java?

---

### Post by itachisxeyes on 2010-04-29
> **StormRoBoT2 said:**
> is that all? 

do i need to install any other thing? is this full java?
when you say "java" do you mean the run time that lets you interact with stuff on the internet? because this has you covered, at least i'ts covered me.
if you mean "java" like net beans or something then that is separate. 
but if it doesn't workout for you then have a look here: [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)

---

### Post by StormRoBoT2 on 2010-04-29
ok, yeah, the java for uploading picture in facebook are all working now.. thanks to you..

but if i would like to install netbean and all, do you have any link where i can follow the guild?

---

### Post by itachisxeyes on 2010-04-29
> **StormRoBoT2 said:**
> ok, yeah, the java for uploading picture in facebook are all working now.. thanks to you..

but if i would like to install netbean and all, do you have any link where i can follow the guild?

i believe that is in the "ubuntu software center" if you look under developer tools.

---

### Post by Cardale on 2010-04-30
It would depend on how much memory you have.

---

### Post by interzoneuk on 2010-08-18
Hi.


sorry to revive an old thread, but regarding the query on Java...

apt-get install ubuntu-restricted-extras will install openjdk - not sun-jdk - I know that some java apps (i.e [www.jmeeting.com](www.jmeeting.com))  do not work unless you use the sun version.

In 10.04 (32 + 64 bit versions) Sun Java has moved to the partner repo.

Just add/uncomment the partner repo in /etc/apt/sources.list 

-------------
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
-------------

Then 

sudo apt-get update
sudo apt-get (one of the following)

sun-java6-bin
sun-java6-jdk
sun-java6-jre
sun-java6-plugin

Its in the release notes also :-

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository)

----------------------
For Ubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the Ubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
----------------------

---

