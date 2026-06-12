---
title: "recompile software file into a iso"
date: 2011-06-23
forum: General Help
---

### Post by elliotn on 2011-06-23
hi I need help to recompile files into an ISO

I bought a DVD of reason 4.0 (windows music program),  I wanted to back it up but I didn't make an ISO I copied the files.

now I have lost the DVD and I want to install reason back to my windows machine but it needs a DVD in the drive, it wont proceed.

how can I recompile the files and make them a recognized ISO so my installation can continue.

thanks

---

### Post by inameiname on 2011-06-23
<snip>
Or download it (if possible), from its main website: [http://www.propellerheads.se/download/](http://www.propellerheads.se/download/)

---

### Post by elliotn on 2011-06-23
my problem is that I don't have internet so I can't download 1.7Gb of a ISO

---

### Post by dandnsmith on 2011-06-23
If you have the files copied from the original DVD, and in the original hierarchy, you should be able to burn this to a DVD directly, without messing about with creating an iso file.
If you really want the iso file, then you still need the files in the original hierarchy on the DVD, and use mkiso (qv).

HTH

---

### Post by elliotn on 2011-06-23
> **dandnsmith said:**
> 
If you really want the iso file, then you still need the files in the original hierarchy on the DVD, and use mkiso (qv).

HTH
any instructions please

---

### Post by psusi on 2011-06-23
If it is looking for the disc for copy-protection purposes, then it won't just accept any old disc.  It is looking for the original disc, so you are screwed.

Copy protection sucks doesn't it?

---

### Post by elliotn on 2011-06-23
> **psusi said:**
> If it is looking for the disc for copy-protection purposes, then it won't just accept any old disc.  It is looking for the original disc, so you are screwed.

Copy protection sucks doesn't it?

its not it

---

### Post by psusi on 2011-06-23
> **elliotn said:**
> its not it

Parse error.... what?

---

### Post by elliotn on 2011-06-23
> **psusi said:**
> Parse error.... what?

no error, the thing is when it installs it needs the DVD in the drive while I have the files that are contained on the DVD

---

### Post by psusi on 2011-06-23
> **elliotn said:**
> no error, the thing is when it installs it needs the DVD in the drive while I have the files that are contained on the DVD

The parse error is in my attempt to parse your statement "it is not it", which does not make sense.  Now you have just restated what you said in the first place, to which, my first answer still applies.

To clarify: the program's copy protection is not looking for the files you have, or that there is any old disc in the drive.  It is looking for some subtly corrupted part of the original disc that can not be copied.  Simply putting the files onto another disc won't help.

---

### Post by Grenage on 2011-06-23
> **elliotn said:**
> no error, the thing is when it installs it needs the DVD in the drive while I have the files that are contained on the DVD

To back **psusi** up, he is quite correct.  The data you have does not include the copy protection data, which is required to identify the disc.  You will not be able to make it work this way.

---

### Post by elliotn on 2011-06-23
ok o manage to make it work, I just made an ISO with ultraiso and and made the volume to match what reason wants and it worked

---

