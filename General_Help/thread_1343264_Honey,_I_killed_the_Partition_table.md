---
title: "Honey, I killed the Partition table"
date: 2009-12-01
forum: General Help
---

### Post by paddysteed on 2009-12-01
long story short, i typed "dd if=/dev/zero of=/dev/sd**a**" instead of "dd if=/dev/zero of=/dev/sd**b**". It killed everything. fsck fails as there is no mbr and disk manager detects it as "unused space". I failed. I know I will lose a lot, i think i stopped dd at around 400mb but i do have some important files in there and would like them back please. Ideas anyone?
P.S. I love hopeless situations

---

### Post by oldfred on 2009-12-01
I have not used it but some recommend testdisk and photorec. They are in the repositories and usually included in the linux based recover CDs.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by japju on 2009-12-01
I'm sorry but you are going to have hard time. It is possible to recover whatever was not overwritten. It will be painful (as a boring) and long process though. You want to mount the partition/disk read only and copy the raw device block by block on another disk. 

Then you have all the leisure to work on the puzzle of your life. You should consider how important are those files versus how much time and effort are willing to put on it. (Would not backups been so much easier? Will you do that in future?)

I've done it once when a friend managed to do "rm -rf" (yes, it was a friend; I have had few mistaken "rm -rf" experiences but so far avoided doing any real harm; for ages, I always do "ls -lR" before issuing "rm -rf". Always without exception) on a cvs repository instead of the working directory (too many windows open, listening to music and not paying attention what he was doing). I actually was surprised how easy the recovery process was, long but easy. We were helped with the fact that the content of the files was text and it was easy to see whether one block connected with another.

Some custom perl scripts made the the process faster but they took a long time to run: a day and half. One of the problem is that at times there were several choices for the next correct block and you have to see which choice gives you the maximum file recovery or which is most current. Note that those two questions are separate: it is quite possible that you could recover an older version of the file easier than partial copy of the latest version.

If you want to embark on this journey, you either want to use some tools (there are many around, but I have not used any of them so I cannot recommend) or you need to understand the filesystem structure.

As they say, everything is possible, it is just a question of how much time or money do you want to invest in it.

Good luck,

Jari

---

