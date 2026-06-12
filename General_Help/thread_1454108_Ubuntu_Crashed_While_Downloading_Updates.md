---
title: "Ubuntu Crashed While Downloading Updates"
date: 2010-04-14
forum: General Help
---

### Post by Joe Bloe on 2010-04-14
I Installed Ubuntu 9.10 on April 12th
   
  On April 14th I got a screen message advising me to download and install 257 update programs.
   
  The download got up to at least program 241. That’s the last one I remember seeing
   
  Then the screen brightened for about one second and I got a message saying that Ubuntu had to be restarted to finish downloading
   
  I restarted and this is the screen I got.
   
  Any clues about what to type on the command line?
   
  Thanks in advance


[IMG]http://farm5.static.flickr.com/4036/4519845369_0c99779884_o.jpg[/IMG]

---

### Post by plucky on 2010-04-14
Welcome to the Forum

Is this a **wubi** install or a full install to its own partition?

The command ```
sudo dpkg --configure -a
``` should fix the problem,if not, post back any errors produced.

Good Luck

---

### Post by Joe Bloe on 2010-04-14
I installed from a disk onto a separate partition on the hard drive.

The sudo command didn't work - nothing happened (no error messages either)



I'll check back here regularly, try out any suggestions that you or others may have, and let you know the results as we go along.

Luckily I have no important data at risk so if we can't get the problem sorted, I will probably reinstall and start all over again - but as I say, not straight away - I'll wait a few days.

Thanks

---

### Post by plucky on 2010-04-14
Does it just stop at that screen?

If so , you should boot into **recovery mode** which is the second selection in the grub boot menu.
It will take you to a list of options.
Select "fix broken system" and see if that can fix it.

It might be just quicker to re-install again,as it is a new system.
But don't shutdown the system when updating,wait until all updates have downloaded and installed.

Good Luck

---

### Post by Joe Bloe on 2010-04-14
Thanks Plucky, I'll try your suggestion


Just for the record, I didn't accidentally shut down during the update. I got a specific message on the screen saying that the update could not continue until the machine was restarted.

---

### Post by Joe Bloe on 2010-04-14
I used recovery mode. A couple of hundred lines of text scrolled onto the screen and the picture below shows the final page.

No options, just the command prompt (and me without a clue what to do next).

[IMG]http://farm5.static.flickr.com/4009/4520884468_11036de916_o.jpg[/IMG]

---

### Post by Joe Bloe on 2010-04-15
Computer is still not working, but thanks for your efforts. I appreciate them.

The thing that intrigues me though, is the screen message telling me that the update could not continue without a restart. Why did that happen I wonder?

Obviously the system didn't need a restart yet somewhere deep inside Ubuntu there is a piece of code that triggers this message. It's a bug that needs to be fixed I reckon.

---

### Post by Joe Bloe on 2010-04-16
Somebody gave me a link to another question about the same problem. I haven't tried any of the suggestions yet (I'll do that tomorrow) but just in case anyone is interested, here is the link:

[http://forum.deviantart.com/os/unix/1439799/](http://forum.deviantart.com/os/unix/1439799/)

I'll come back tomorrow and tell you how it all worked out.

---

### Post by House101 on 2010-04-16
Looks like it's doing disk checks. If that's what it's doing then it might take a while. Have you let it go for a while??

I've had the same problem with recovery, it tries to load vbox and always marks it as failed. Then I'm stuck with a command line I have no idea what to do with!

---

### Post by Joe Bloe on 2010-04-17
Thanks everybody.

Unfortunately nothing worked so I finished up formatting the partition and reinstalling Ubuntu.

I really appreciate your efforts though. It's nice to know I'm not all alone when problems arise.

---

