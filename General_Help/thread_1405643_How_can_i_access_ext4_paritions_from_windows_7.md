---
title: "How can i access ext4 paritions from windows 7?"
date: 2010-02-12
forum: General Help
---

### Post by aviramof on 2010-02-12
thanks in advance.

---

### Post by jken146 on 2010-02-12
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by aviramof on 2010-02-12
already tried it didn't worked maybe because of thos "&#8220;-O ^extent" mention there.
 
what excelly is it and can i or should i disable it in any way?
 
thanks in advance.

---

### Post by lenoirrichelieu on 2010-02-13
Simply: at this very moment you cannot.

---

### Post by aviramof on 2010-02-13
that's a real good answear i'm sure there has to be a way to do that.

---

### Post by texaswriter on 2010-02-13
> **aviramof said:**
> that's a real good answear i'm sure there has to be a way to do that.I'm sure there is a way, but given how new ext4 is, I imagine there isn't too much done yet. But, be patient with google and you may find something useful.

---

### Post by The Cog on 2010-02-13
You could run Linux inside VirtualBox with raw partition access to the ext4 partition, possibly. Better to boot Ubuntu and copy the files to the NTFS. Just accept that windows can't read ext4, jfs, btrfs partitions, and probably never will because MS can't abide that kind of interoperability.

---

### Post by texaswriter on 2010-02-13
Interestingly enough, depending on how you specifically need it to work, Linux can look at NTFS, so you can just boot into your Linux partition to swap files or whatever you task is. 

I do this on my laptop. I have all my music on my Windows partition because it has to be synced with Ipod. But give authorization to mounting it, and I can do anything with those files as if they were on my Linux partition. 

Hope that helps. Sometimes small measures can be easier than more ambitious ones. In the world of politics this is called compromise.

---

### Post by bruno9779 on 2010-02-13
> **texaswriter said:**
> Interestingly enough, depending on how you specifically need it to work, Linux can look at NTFS, so you can just boot into your Linux partition to swap files or whatever you task is. 

I do this on my laptop. I have all my music on my Windows partition because it has to be synced with Ipod. But give authorization to mounting it, and I can do anything with those files as if they were on my Linux partition. 

Hope that helps. Sometimes small measures can be easier than more ambitious ones. In the world of politics this is called compromise.

+1

store the files you need on both systems on NTFS or FAT

---

### Post by aviramof on 2010-02-13
i am aware of the fact that i can do everything via linux but thanks any way.

---

### Post by texaswriter on 2010-02-14
> **aviramof said:**
> i am aware of the fact that i can do everything via linux but thanks any way. People are trying to help each other out. Not sure what that last statement was supposed to be. Guess I'll just zap this thread since it seems likely advice will get you a "nice" response.

---

### Post by Richard1979 on 2010-02-14
Run a small Ubuntu install in VirtualBox and share the directory using the built-in tech or by using Samba.

---

### Post by aviramof on 2010-02-14
i can access my ubuntu partition via ubuntu in virtual box?

sound like a good solution to me.:)

---

### Post by Richard1979 on 2010-02-14
> **aviramof said:**
> i can access my ubuntu partition via ubuntu in virtual box?

sound like a good solution to me.:)

Sounds like the only solution to me.
At least you can do a /mount

---

### Post by aviramof on 2010-02-14
thanks.

---

### Post by texaswriter on 2010-02-14
> **Richard1979 said:**
> Sounds like the only solution to me.
At least you can do a /mount

Linux should detect virtually any volume / partition, regardless of format [at the very least typical Windows ones]. To mount them will require user privileges [aka sudo or root]. My Ubuntu box just prompts me for my sudo password through a UI popup. But if I do it through the prompt, it would just be a ```
sudo mount
``` command as you say.

---

### Post by tristanbobistan on 2010-03-18
is there any way to mount via cygwin?

---

### Post by skliarie on 2010-05-16
> **aviramof said:**
> thanks in advance.

There is bug report for extents support in ext2fsd over here:
[https://sourceforge.net/tracker/?func=detail&atid=437368&aid=2995425&group_id=43775]("https://sourceforge.net/tracker/?func=detail&atid=437368&aid=2995425&group_id=43775")

---

### Post by Been Told on 2010-09-07
I normally don't dig out old threads, but just to let everyone know:
Ext2explorer now works with ext4, even with extents enabled! The link is in the second post.
I am using it right now with my ext4 HDs.

---

