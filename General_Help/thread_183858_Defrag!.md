---
title: "Defrag?!?"
date: 2006-05-28
forum: General Help
---

### Post by Grimboy on 2006-05-28
Hey, on my machine the hard disk ubuntu is installed to isn't very big (around 12GB, I survive by keeping media on a separate disk). So far I've got by more or less, but I like to be as efficient as possible space wise. All of the files on my disk take up a total of 5.1GB, according to filelight, however, according to di, the total usage is 10488.9MB (out of 12223.1MB). It seems to me that I need to defrag, however, I can't find any utility to do this on an ext3 partition. Can anyone fill me in on how to defrag or what I should be doing?

Also to shove in another couple of less important questions: How can I change the theme that kde applications use from gnome? And why has my firefox's (1.5 from FirefoxNewVersion on the wiki) find feature broken? Ok, unless you have an easy answer ignore the last one as dapper will probably fix it.

Sorry about the slight incoherance of this post.

Thanks,
Frankie.

---

### Post by henriquemaia on 2006-05-28
[quote=Grimboy]Hey, on my machine the hard disk ubuntu is installed to isn't very big (around 12GB, I survive by keeping media on a separate disk). So far I've got by more or less, but I like to be as efficient as possible space wise. All of the files on my disk take up a total of 5.1GB, according to filelight, however, according to di, the total usage is 10488.9MB (out of 12223.1MB). It seems to me that I need to defrag, however, I can't find any utility to do this on an ext3 partition. Can anyone fill me in on how to defrag or what I should be doing?

Also to shove in another couple of less important questions: How can I change the theme that kde applications use from gnome? And why has my firefox's (1.5 from FirefoxNewVersion on the wiki) find feature broken? Ok, unless you have an easy answer ignore the last one as dapper will probably fix it.

Sorry about the slight incoherance of this post.

Thanks,

Frankie.[/quote]

About fragmentation, if you're using a EXT3 fs, fragmentation is not very much a problem. Have you checked du for that drive? Maybe you have something on a specific folder that you're not aware of. Just an idea, though.

---

### Post by gwpritch on 2006-05-29
Try clearing the apt cache:

sudo apt-get clean

If you have done any upgrading etc, all those packages remain in the /var directory until you clean them out and can take up a lot of space.
Also mail can take up plenty of space before you know it.
That's why its often advisable to put /var on a separate partition especially if space is at a premium. If it fills up the root partition it can lock up your system.

---

### Post by tribaal on 2006-05-29
That's right, apt-get clean helps a lot.

On defragmentation though, the way the ext3 filesystem works, you won't actually have to defrag. Ever. You will get fragmentation eventually, but it'll never be more than 2-3%, which is negligible.

Isn't that cool?

- trib'

---

### Post by NeghVar on 2006-05-29
The KDE theme from Gnome I don't think you can because Gnome uses GTK while KDE uses Qt and I don't think they are compatible in that way. Anyone with more knowledge feel free to correct me.

---

