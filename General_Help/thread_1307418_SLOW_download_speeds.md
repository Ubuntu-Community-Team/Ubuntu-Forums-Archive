---
title: "SLOW download speeds"
date: 2009-10-31
forum: General Help
---

### Post by dbyjazz on 2009-10-31
Right now I'm downloading something through Terminal and it's downloading at only at 16-24 kB/s. It should be downloading at about 90-100 kB/s. 

Any ideas?

And no, I'm not using a BitTorrent in the background

---

### Post by misfitpierce on 2009-10-31
Change the server in sources 
System-Admin-Software Sources
Then hit Download From... dropdown... hit other... then hit select best server...

It will find the best server for you by speed and they are all just as updated like they are cloned. So dont worry about anything like that... Less ppl using some of those and closer servers to your connection server will get you better speeds!

---

### Post by dbyjazz on 2009-10-31
that helped a ton! thanks!

---

### Post by misfitpierce on 2009-10-31
No prob

---

### Post by shaon3343 on 2009-10-31
hey , do you know about my maximum download speed ?? its 10 KBps!!!!! lolz :D :D!! I'm using a nokia3230 mobile phone as my modem and my ISP is Grameen Phone and I'm in Bangladesh. Do you know any tweak to increase it?

---

### Post by rockstarrem on 2009-10-31
Your using a mobile phone as a modem?

---

### Post by misfitpierce on 2009-10-31
Sounds like that would be controlled by your phone and carrier not ubuntu or anything... Make sure you got good signal is best way to ensure full speed!

Also this thread is solved and that really has nothing to do with this thread lol.

---

### Post by earthpigg on 2009-10-31
> **shaon3343 said:**
> hey , do you know about my maximum download speed ?? its 10 KBps!!!!! lolz :D :D!! I'm using a nokia3230 mobile phone as my modem and my ISP is Grameen Phone and I'm in Bangladesh. Do you know any tweak to increase it?

do you have access (even temporary) to a faster Internet connection?

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Alex1200GS on 2009-11-02
> **misfitpierce said:**
> Change the server in sources 
System-Admin-Software Sources
Then hit Download From... dropdown... hit other... then hit select best server...

That would work on a Desktop; any clues how to do that using shell commands? I need to change this setting on my Ubuntu Server.

---

### Post by earthpigg on 2009-11-02
> **Alex1200GS said:**
> That would work on a Desktop; any clues how to do that using shell commands? I need to change this setting on my Ubuntu Server.

edit /etc/apt/sources.list in your fav text editor.

replace the default URL's with any of these:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

try a few, see which ones are fast enough for you.

if you want the fast***_est_***:

if you wish, you could take that html page, grep it into a plain text file list, pipe that into a shell script that pings them all and tells you which is the quickest.

but that may be more work than it's worth for you. you could use the method mentioned above on your desktop machine, and use whichever one is found to be the fastest on your server machine. for best results there, perhaps bring your ubuntu laptop/netbook to wherever your server is located and plug it into the same internet connection and then test.

---

### Post by Alex1200GS on 2009-11-03
Thanks earthpigg! It worked like a charm.

Although the geek/nerd/weirdo inside me insisted that grepping the page and pinging all hosts would be the proper way to go along, I quickly pinged all hosts using my Karmic laptop and then nano'ed the fastest host into the sources.list file.

Then tried updating/upgrading and the download speed is greatly improved.

Thank you!

---

### Post by Alex1200GS on 2009-11-03
Uhmmm...

How can I add beans or reputation, or whatever to a helpful answer?

---

