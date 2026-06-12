---
title: "what is 'localhost:53886'"
date: 2010-05-08
forum: General Help
---

### Post by whitefort on 2010-05-08
Hi,

When using Firefox, I've started getting a popup window with the following message:

'A user name and password are being requested by [http://localhost:53886](http://localhost:53886). The site says: "administrator"'

Then there are spaces for the name and password.

I've no idea what this is all about - could it mean someone is trying to hack me, or something?  A Googlesearch didn't find anything, so I'm guessing it's not something common.

I just click cancel and the box goes away, but then it comes back after a while.

Any idea what's going on?

---

### Post by SPr on 2010-05-08
Enter
```

sudo netstat -nlp

```
when the prompt appears. You'll have to look for the port number.

Read man netstat to see if you can refine the results.

---

### Post by dino99 on 2010-05-08
you may need some "security" installed: gufw (activate it) and look at "secured ip" below

into firefox: install adblocks and noscript

---

### Post by SPr on 2010-05-08
I'm not disputing that those security packages aren't needed but they wont help in this case because this is caused by a program running on the computer hence the localhost:xxxxx address:port combo.

I thought this sounded familiar. Read [http://ubuntuforums.org/showthread.php?t=1299896](http://ubuntuforums.org/showthread.php?t=1299896) and see if it applies to your set up.

---

### Post by whitefort on 2010-05-08
> **SPr said:**
> I thought this sounded familiar. Read [http://ubuntuforums.org/showthread.php?t=1299896](http://ubuntuforums.org/showthread.php?t=1299896) and see if it applies to your set up.

SPr - thank you so much!  I haven't checked yet, but I think you've solved the puzzle.

Just today I installed the Firefox add-on that's supposed to sync my bookmarks with UbuntuOne (Bindwood) It uses something called CouchDB, and in the thread that you mentioned, I found this:

"A synaptic search shows it has something to do with CouchDB"

I'm going to get rid of Bindwood, and see if that fixes things.  Presumably it's asking for my UbuntuOne password, but I've decided that I prefer Xmarks anyway.

Thanks - I'll mark this thread as solved if it fixes the problem (and come back here crying if it doesn't!)

PS Thanks to everyone else who tried to help!

---

