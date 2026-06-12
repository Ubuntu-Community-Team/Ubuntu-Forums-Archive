---
title: "Is this possible?"
date: 2009-07-27
forum: General Help
---

### Post by Grant A. on 2009-07-27
Is it possible for a LiveCD written to a CD-RW disk to be permanently/temporarily infected by a piece of malware/a rootkit while the LiveCD is running?

I was surfing the web on my Ubuntu 9.04 LiveCD, and I was worried about this for these reasons:

1) the LiveCD runs as root when activated
2) I was visiting odd sites
3) I tried to connect to a 192.x.x.x IP address via Firefox
4) It's a rewritable disk (CD-RW)

My paranoia has been flaring up lately, and I think it's a relapse of my OCD, as I keep worrying about the strangest things. :(

I would really appreciate an answer, so that I can quit worrying.

---

### Post by lukeiamyourfather on 2009-07-27
I would say that's pretty unlikely. The live discs run in memory and don't write anything back to the disc as far as I know. Somebody directly involved with the live disc part of Ubuntu would be able to give a definite answer. Cheers!

---

### Post by jerome1232 on 2009-07-27
I'm going to just throw in, what are the odds of running into an exploit targeted against users of a live cd which is writable (VERY small target audience), they are probably extremely, insanely slim.

---

### Post by jocko on 2009-07-27
> **jerome1232 said:**
> I'm going to just throw in, what are the odds of running into an exploit targeted against users of a live cd which is writable (VERY small target audience), they are probably extremely, insanely slim.
... and, is it even possible to write to a mounted cd? At least in my experience a cdrw always has to be unmounted before it can be written to, and if a live cd was forced to unmount the entire live cd environment would stop working as soon as something had to be read from the disk...

---

### Post by CatKiller on 2009-07-27
> **Grant A. said:**
> Is it possible for a LiveCD written to a CD-RW disk to be permanently/temporarily infected by a piece of malware/a rootkit while the LiveCD is running?

No.

> I was surfing the web on my Ubuntu 9.04 LiveCD, and I was worried about this for these reasons:

1) the LiveCD runs as root when activated

No it doesn't. It runs as a normal user, the same as in a standard install. It's true that you don't get prompted for the password, since it's blank, but you do still need to use sudo to run things as root in the Live CD environment.

>  3) I tried to connect to a 192.x.x.x IP address via Firefox

And? Are you hosting Linux-specific malware on your local network specifically to try to infect machines? No, thought not.

>  4) It's a rewritable disk (CD-RW)

Doesn't matter. The environment isn't on the disk, it's in RAM. The programs on the cd are expanded into a tempfs RAM drive. That's why it takes so long to load anything in the Live environment, even though it's all moderately responsive once the programs have loaded. Nothing is run directly from the CD, and certainly nothing is written to the CD, even if it's RW. You would need to (manually) run something that actually wrote to the files on the CD rather than the files "on disk" for it to be a problem.

---

### Post by Grant A. on 2009-07-27
Ok, thanks for clearing all of that up.

I really appreciate the help, guys! :)

By the way, CatKiller: You didn't have to come off so abrasively, it was just a question. :|

---

### Post by CatKiller on 2009-07-27
> **Grant A. said:**
>  By the way, CatKiller: You didn't have to come off so abrasively, it was just a question. :|

I certainly didn't mean to. I was just trying to be clear. Sorry for any offence.

---

