---
title: "Data loss after Hibernation with Truecrypt and SciTE"
date: 2012-06-11
forum: General Help
---

### Post by hutzlibu on 2012-06-11
Hi everyone, this is my first Post here, so maybe I am not in the right place, but since I don't know what the cause of my problem is, General Help seems like a good place to start ...

Now to the problem, like the caption says I had data loss, after I returned from Hibernation. So this is a big problem to me ...

Hardware:
Netbook Aspire One, Intel Atom

OS:
Lubuntu 12.04 (recently updated from 11.10)

What I did, before Hibernation:

I worked on some (Javascript) Textfiles with SciTE on 2 Sessions.
The files where stored on a mounted TrueCryptContainer (which sourcefile was stored on hd)

Then I made a break and switched to Hibernation.

after Rewakening:

I continued working on a textfile ... and tried to save it:

But then there was a Alert: 
"could not save to " *filepath*

First I tried saving under a different name -> didn't worked(Alert: "Could not save ..."), but I later found a file with the correct name, but it was empty

Then I tried closing and reopening the file -> didn't worked either.
Then I tried to dismount the (truecrypt) Volume -> wasn't possible, he claimed that the drive was still buisy and something, was still writing data to it.
	
Then I closed both SciTE - Sessions -> after that I was able to dismount.

Then I remounted the volume .... and opened the File I lasted worked on, **and it was empty**!!!

Now I have to find out, where the problem is, or which programm causes the problem, because obviously nobody likes his work getting wasted.
(sure I am doing backups, but still I don't like wasting my time)

My suspicion list:

TrueCrypt -> never gave me any problems, was allways reliable

Netbook -> possible, because it fell down once, but there hasn't been any other problems with the HD or RAM of any sort

Lubuntu, or Linux Kernel -> possible, but I doubt it

SciTE -> my suspect, I recently updated it. And before there where never any problems


So now I would appreciate your help to solve this problem, since I am kind of a noob with Linux, maybe by pointing me to log-files where I might find more Information, or maybe this is a known Issue?

---

### Post by hutzlibu on 2012-06-12
Nobody?

---

