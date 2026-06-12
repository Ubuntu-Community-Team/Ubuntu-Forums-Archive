---
title: "C to / ?"
date: 2011-01-20
forum: General Help
---

### Post by Nictra Savios on 2011-01-20
Just curious.... What would happen if i took all the files in The C:// of windows and put them in the / of ubuntu, alongside its regular files? .... Would that like.... make me able to open windows stuff? idk.. im really just curious i wouldnt do it :P

---

### Post by Nictra Savios on 2011-01-20
I'm just curious but... would i be able to use any windows programs if i say.... took whats in C and put it , with ubunt's files... into /? hmm? anyone wanna try lmao?

---

### Post by srs5694 on 2011-01-20
To run Windows programs in Linux, you use [WINE](http://www.winehq.org) or a virtualized environment (using [QEMU,](http://wiki.qemu.org/Main_Page) [VirtualBox,](http://www.virtualbox.org) or the like).

---

### Post by bodhi.zazen on 2011-01-20
> **Nictra Savios said:**
> I'm just curious but... would i be able to use any windows programs if i say.... took whats in C and put it , with ubunt's files... into /? hmm? anyone wanna try lmao?

In general, no. Linux is not a drop in free relpacement for windows.

You may be able to run some applications in Wine, but wine takes some technical expertise and can very much be hit or miss.

See: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Nictra Savios on 2011-01-20
Yea i know all that im not a noob. I wanna know what would happen, im curious.

---

### Post by Simian Man on 2011-01-20
> **Nictra Savios said:**
> Yea i know all that im not a noob. I wanna know what would happen, im curious.

You would have a bunch of useless files on your disk.  What do you *think* would happen?

---

### Post by srs5694 on 2011-01-20
> **Nictra Savios said:**
> Yea i know all that im not a noob. I wanna know what would happen, im curious.

You'd lose disk space. Linux wouldn't try to access the /Windows directory or use the programs it contains. Ditto for other Windows-specific directories. Of course, if a directory or file happened to have the same name as an important one in Linux, you'd run into problems because of a damaged Linux file. You could also access the files manually, but unless you used WINE to run the programs, they'd be useless lumps of gibberish. You could manually access at least some kinds of data files, but that's not extraordinary.

---

### Post by bodhi.zazen on 2011-01-20
> **Nictra Savios said:**
> Yea i know all that im not a noob. I wanna know what would happen, im curious.

You could read any text files, but you could not run any binaries or if you have them bat files.

---

### Post by andrewc6l on 2011-01-21
Nope, you'd still boot using the Linux boot loader, which would load the Linux kernel. If you want to run Windows apps on Linux, look into [Wine]("http://www.winehq.org/") - I'm pretty sure you can just install it using the package manager. (Haven't tried in a long time, though :-) )

---

### Post by Chronon on 2011-01-21
You would just be littering your root directory with useless files.  If you want to run Windows applications while running Ubuntu then look into Wine or install Windows inside of Virtualbox (or another virtualizer).

---

