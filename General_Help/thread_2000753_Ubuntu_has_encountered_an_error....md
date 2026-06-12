---
title: "Ubuntu has encountered an error..."
date: 2012-06-10
forum: General Help
---

### Post by NaturistGirl on 2012-06-10
After since I've been using Ubuntu 12.04. I get a lot of "Ubuntu has encountered an error" messages. I get one of two soon after I boot in. I some of the them are x.org and the weather applet (which I have now deleted).

A couple months ago, I had to take my computer in to get a new hard drive. They had to install Ubuntu again. When I got it back, it seemed to work fine, but soon after, I get a message of an upgrade. That's when that all started. My computer seems to work fine, despite getting these messages. The only thing it did effect, if the weather applet. As soon as I got an error from it, it would disappear until I restart my computer.

Should I take my computer back to the store?

---

### Post by MG&amp;TL on 2012-06-10
> **NaturistGirl said:**
> After since I've been using Ubuntu 12.04. I get a lot of "Ubuntu has encountered an error" messages. I get one of two soon after I boot in. I some of the them are x.org and the weather applet (which I have now deleted).

A couple months ago, I had to take my computer in to get a new hard drive. They had to install Ubuntu again. When I got it back, it seemed to work fine, but soon after, I get a message of an upgrade. That's when that all started. My computer seems to work fine, despite getting these messages. The only thing it did effect, if the weather applet. As soon as I got an error from it, it would disappear until I restart my computer.

Should I take my computer back to the store?

Nope, not a hardware problem. As free software, unfortunately, Ubuntu isn't perfect, so we have to put up with the occasional crashes (but faster pace of development). Have you sent the problems to the developers?

Most likely, the weather applet was a fatal crash, so it got killed until the panel was restarted (if you logout, then in again).

---

### Post by zombifier25 on 2012-06-10
That's a rather annoying behavior of Ubuntu. Clean everything inside the /var/crash directory (probably as root) and see if the problem disappears.

---

### Post by NaturistGirl on 2012-06-10
> **MG&TL said:**
> Nope, not a hardware problem. As free software, unfortunately, Ubuntu isn't perfect, so we have to put up with the occasional crashes (but faster pace of development). Have you sent the problems to the developers?

Most likely, the weather applet was a fatal crash, so it got killed until the panel was restarted (if you logout, then in again).

Yes, I report click the send button when I get them.

---

### Post by MG&amp;TL on 2012-06-10
> **NaturistGirl said:**
> Yes, I report click the send button when I get them.


Good for you! Does it not open a webpage with some further details? You should get email updates about how the bug is progressing. :)

---

### Post by NaturistGirl on 2012-06-10
> **MG&TL said:**
> Good for you! Does it not open a webpage with some further details? You should get email updates about how the bug is progressing. :)

Nope. Sometimes when I do, it disappears. If it is a program, it says that the project is finished for this version, and asks what else I would like to do. ANy option I choose dosen't really do anything. None take me a too a web page, but I think one suggests a page like AskUbuntu to get answers. It's been a while since I got that one.

---

### Post by MG&amp;TL on 2012-06-10
That's odd. Are you on a fully updated system?

---

### Post by NaturistGirl on 2012-06-10
> **MG&TL said:**
> That's odd. Are you on a fully updated system?

Yes.

---

### Post by MG&amp;TL on 2012-06-10
Obviously, it's not meant to do that. So I don't know what to suggest. Anybody?

---

### Post by GreggC on 2012-06-10
> **NaturistGirl said:**
> Nope. Sometimes when I do, it disappears. If it is a program, it says that the project is finished for this version, and asks what else I would like to do. ANy option I choose dosen't really do anything. None take me a too a web page, but I think one suggests a page like AskUbuntu to get answers. It's been a while since I got that one.

I have the same issues with error messages & I work on a fully updated system. I also have the weather app installed and a couple "less than stable" programs that crash quite a bit when I run them.
I always make a point to send a crash report except when I know what the cause is or it's a reoccurring issue.

It's a minor inconvenience when compared to waiting 15-20 minutes for my windows work machine to boot & then having office crash in the middle of your work.

---

### Post by deadflowr on 2012-06-10
The reality of the situation is that the errors you are getting have probably been in your system forever. The difference now is that the debugging tool apport has been enabled in precise by default, were as, even though, it has been installed in previous distros, it had always been disabled.
 Reporting the bugs is good and helpful, but having a system which seems to be running without any real set backs, reporting errors left and right is annoying. My simple solution to this is to disable apport.

 Open a terminal

```
sudo nano /etc/default/apport
```

Change the line enable=1 to enable=0
ctrl+x, then answer y to save.

I have done this and haven't gotten an error since, and my system is running just as it always has.

---

