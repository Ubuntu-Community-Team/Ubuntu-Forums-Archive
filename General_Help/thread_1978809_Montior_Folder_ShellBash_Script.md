---
title: "Montior Folder Shell/Bash Script"
date: 2012-05-12
forum: General Help
---

### Post by rhss6-2011 on 2012-05-12
Hello there everyone,
I've used linux since Ubuntu 9.04 and just recently started to try to learn how to use shell/bash scripting, using core utilities that ALL linux systems can use, such as unrar, tar, and others...
Well, I made a script for myself not too long ago to manage archives, videos, and other files that used to take me a long time to deal with -- With my script (which I am still tweaking every now and again) it has made things easier, but I finally ran into an issue that is a little too big for me to swallow...

I am trying to _**create a script**_, that will  _**monitor a folder and ****move**_ any _**new folders and/or files of various sorts**_ to another location.
[I][U][B]
FOR EXAMPLE:[/B][/U][/I]
_**monitor folder**_ /home/user/downloads/NEW\ Downloads/
_**Move new files**_ to /home/user/downloads/Completed-Downloads

I heard that inotify could do the trick, but using *man inotify* only confused me even more and while looking at scripts from other people, nobody really explains how it works... Scripts that I create, are supposed to be able to work on all platforms without having to install anything - if you install a linux version from a live cd, you should be able to run any script that I create right from the beginning...

The problem I'm having is that (for convenience) people tell me to use one program or another, while I try to create scripts that run from a terminal (verbosely at times) so I can learn what it is I am doing...

The _**script**_ I am trying to create **_can be executed_** _**by**_ a _**program on Download Completion**_, so I figured that might make things a little easier, because the script _**would check/monitor folder**_ and then _**move any new folders and/or files to**_ a _**different location**_ and also _**notify me**_ when the _**files have be moved**_.

Is this even possible using strictly shell/bash or is it just really complicated and difficult..?

---

### Post by Bonster on 2012-05-12
you might want look into in *incron* if u need to monitor your files changes

---

### Post by rhss6-2011 on 2012-05-14
-__-

That is exactly what I meant. I am trying to create a script that will monitor the folder _**using components of Linux that are standard**_, and _**not something **_that I have to additionally install.

---

### Post by roelforg on 2012-05-14
> **rhss6-2011 said:**
> -__-

That is exactly what I meant. I am trying to create a script that will monitor the folder _**using components of Linux that are standard**_, and _**not something **_that I have to additionally install.


On linux, there's no such thing as stuff you don't add. install.
Heck, a default ubuntu install just unpacks the packages from the cd's offline repo.
(ever did an ubuntu server install / textmode install / used debootstrap? cause they, unlike the gui one, DO show you what packages they're installing)
And there's no way to know if a dl finished w/o some program tying into events of other progs that says if they're done.

---

