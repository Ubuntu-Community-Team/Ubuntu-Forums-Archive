---
title: "How I can free my disk space and move packages to another drive that'll work well"
date: 2010-08-31
forum: General Help
---

### Post by shock_the_rock on 2010-08-31
hi, 
I have installed Ubuntu 10.04 Lucid on my pc a month ago and using only ubuntu, I am not so familiar with ubuntu and linux distribution. I have set up many packages on my ubuntu, last of all it shows low disk space, and available disk space only 152MB, I understood with my novice brain that i have to free some disk space, but i dont know how to :( again i want to install more packages on my ubuntu, so i need more disk spaces,  I want to bypass some applications to my external hard drive storage space that will work well on my ubuntu and also tried to backup all my packages with Apton CD software, but it couldn't possible to do so, as there is no enough space on /temp... At first I want to backup all my packages that i have downloaded with investing many times in a .iso format that i can write on disk and later use it, I want to bypass my some Application in my another drive from file system drive that'll work well on Ubuntu and also want to install packages that'll be stored on that drive and want to free my file system drive space to work well on ubuntu.. I dont want to go back to windows any more. 

plz help me. As I am a novice user so plz say step by step or i cant grab anythin.

---

### Post by lombaardcj on 2010-09-06
Hi,

I've had the exact same situation. 

Found the solution at [COLOR=Blue][https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)[/COLOR]
[B]
NOTE:[/B] Understand what they do before attempting to do your own thing.

My setup as follows:

I've copied all my .deb files from ```
/var/cache/apt/archives
``` to my USB portable HDD ```
/media/USBHDD/debarchive10
```I created a script file on my home directory containing:
```
#! /bin/bash
 cd /media/USBHDD/debarchive10
 dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

```The APT line I added to Synaptic looks like this:

```
deb file:/media/USBHDD/debarchive10 ./
```Now from time to time I move all the deb files out to my USB HDD, Run the script and update Synaptic.

This solution helps me to stay in control of the debs I downloaded at a price (Live in South Africa where internet usage is not free)

I can also share with by friends who don't have internet connection.

Hope you get yours sorted.

---

