---
title: "Recovering files from clobbered ext3 partition"
date: 2009-11-07
forum: General Help
---

### Post by Jorenko on 2009-11-07
Through a sad series of events involving an abortive attempt at getting a dual-booting XP install on my Jaunty machine, I've ended up with the first few GB of my /home partition being totally overwritten with junk. I did manage to use gpart and parted to get the partitions themselves back, but there's no restoring the file system itself.

So I'm resigned to losing the thing, but there are just a few files on this disk that I really don't want to lose (a few hi-res originals of photos of my son from when F-Spot wasn't storing files in the right location). Is there a tool out there that will scan my partition for any raw data that looks like a file and help me restore whatever it finds to a new disk? I've found a few solutions but most of them seem to be commercial (and one was even a windows app -- how weird is that?). While I'd be perfectly fine paying for a service like this, I'm a bit shocked that there's not a well-known open source tool for this sort of thing (that I can find, anyway).

Any suggestions?

---

### Post by utnubuuser on 2009-11-07
Hello  ---  If your files still exist on the partition, then there is most assuredly a libre tool to recover them.  Personally don't know the name of the tool, but I've read enough to know that such tools do exits, and it's most likely a reasonably simple process from the command line.  I'd be inclined to try the Debian help forum or their irc channel.

---

### Post by mr_steve on 2009-11-09
> **utnubuuser said:**
> Hello  ---  If your files still exist on the partition, then there is most assuredly a libre tool to recover them.  Personally don't know the name of the tool, but I've read enough to know that such tools do exits, and it's most likely a reasonably simple process from the command line.  I'd be inclined to try the Debian help forum or their irc channel.

Try photorec. I'm not sure if it's a separate package in Ubuntu, or included with the 'testdisk' package.

It's kind of tricky to use, but it will recover photos as long as they haven't been totally overwritten.

---

