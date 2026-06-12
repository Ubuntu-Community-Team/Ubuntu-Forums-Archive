---
title: "Apt-get connections to local ip?!"
date: 2006-03-08
forum: General Help
---

### Post by Toxicity999 on 2006-03-08
For example when running a source list update:
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

Of course this many fold for all other of the many attempts to other sources.

This of course also conflicts with apt-get entirely (whatever happened that is.) As packages allready in the local package view cannot be installed...

For probably uneeded reference this seemingly occured all by itself, as of 2 days ago all was well. Also, Dialup as if that held any matter.

---

### Post by Mustard on 2006-03-08
Have you installed any software recently that may have affected your installation?

---

### Post by Toxicity999 on 2006-03-08
Well, naturally this was my first thought but honestly, I don't believe so... If I knew what *could* presumably cause this then I could probably trace it back somehow. This is of course a temporary issue anyway but I thought I'd throw it out there for my convenience and help to others later. (Temporary as I'm going to be playing with dapper probably tomorrow.)

---

### Post by Toxicity999 on 2006-03-09
Anyone? Though I am upgrading to flight 4 as my prodominant OS I would like to fix this until that time.

---

### Post by Mustard on 2006-03-09
[QUOTE=Toxicity999]Anyone? Though I am upgrading to flight 4 as my prodominant OS I would like to fix this until that time.[/QUOTE]

Unfortunately I have no idea what is causing it.

---

### Post by lamego on 2006-03-09
You have  a proxy defined (localhost) or your sources.list is broken...

---

### Post by muzaki on 2006-03-11
hey i have the same problem...> [http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

dunno what 2 do ,,, yeah i think about proxy thing too, but i have uninstalled this proxy , but still getting the same error:( 
is that possible if the config file from my-already-uninstalled proxy cause this?

---

### Post by Toxicity999 on 2006-03-11
For any reference this was due to my own stupidity... late night as always tweaking my installation installed a proxy("anonymous surfer")... I forget the name of this... from the repos. I'm sure it was only because I didnt configure it correctly, or maybe at all. Just to anyones reference, if this is happening to you and your sources.list isnt physically pointing to a local host for the repos (by that I mean local ip no a file type listing obviously.) You have a proxy program installed or you misconfigured the like yourself.

---

### Post by muzaki on 2006-03-11
apparently the same problem... i installed tor and privoxy from this 
[http://www.ubuntuforums.org/showthread.php?t=95527&highlight=proxy](http://www.ubuntuforums.org/showthread.php?t=95527&highlight=proxy)
General - HOW TO surf anonymous
configure it...
but i cant make myself anonymous....thats why i uninstalled them

after that i got this problem.... so what do you think?,,, what did u do to solve ur prob?

**EDIT** : now its working ... ithink this only because ubuntu need more time than i think to refresh the changed state

---

### Post by Toxicity999 on 2006-03-12
It could just be some kind of residual config... in synaptic check out anything the package alters, or if you didn't already do a complete removal rather than just an uninstall. Of course for me I reinstalled already in an attempt to manually upgrade to dapper using a broken cd *cough* Dialup makes us do crazy things...

---

