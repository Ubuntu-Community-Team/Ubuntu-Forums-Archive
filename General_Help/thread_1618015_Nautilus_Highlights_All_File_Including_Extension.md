---
title: "Nautilus Highlights All File Including Extension"
date: 2010-11-10
forum: General Help
---

### Post by Rytron on 2010-11-10
Hi.

At the moment, when I rename a file in Nautilus it highlights the full file name including the file extension. How can I make it only rename the first part of the file and ignore the extension (as it always did)? The odd thing is that if I rename a file on the Desktop directory, it does not highlight the extension.

Thanks.

---

### Post by mister_playboy on 2010-11-10
Just checked this on my new 10.10 install and Nautilus does not highlight the extension during rename... :confused:

---

### Post by Rytron on 2010-11-10
> **mister_playboy said:**
> Just checked this on my new 10.10 install and Nautilus does not highlight the extension during rename... :confused:

Hi. I installed Nautilus-Elementary but then removed it. I think that messed up a setting somewhere! :confused:

---

### Post by imbjr on 2010-11-12
> **Rytron said:**
> Hi. I installed Nautilus-Elementary but then removed it. I think that messed up a setting somewhere! :confused:

I not convinced that's the issue. I just noticed this effect and I have not installed Nautilus-Elementary.

Just checked: yup, rename on the desktop works as expected - only the filename body is selected.

---

### Post by almariado on 2010-11-18
This behaviour only happens in list view, in Nautilus version 2.32.0 and has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555)
Let's hope they fix it soon

Cheers

---

### Post by Rytron on 2010-11-18
> **almariado said:**
> This behaviour only happens in list view, in Nautilus version 2.32.0 and has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555)
Let's hope they fix it soon

Cheers

Yes. Can nautilus be downgraded to a version previous to 2.32.0?

---

### Post by almariado on 2010-11-18
> **Rytron said:**
> Yes. Can nautilus be downgraded to a version previous to 2.32.0?

Never tried it myself, but take a look at this thread:
[http://wwww.ubuntuforums.org/showthread.php?p=8555665](http://wwww.ubuntuforums.org/showthread.php?p=8555665)

cheers

---

### Post by Rytron on 2010-11-19
> **almariado said:**
> Never tried it myself, but take a look at this thread:
[http://wwww.ubuntuforums.org/showthread.php?p=8555665](http://wwww.ubuntuforums.org/showthread.php?p=8555665)

cheers

Thanks almariado. I fear breaking my system with that method. Thanks anyway though. I will make do with Nautilus for the time being. :)

---

### Post by ernz on 2010-11-28
> **Rytron said:**
> Hi.

At the moment, when I rename a file in Nautilus it highlights the full file name including the file extension. How can I make it only rename the first part of the file and ignore the extension (as it always did)? The odd thing is that if I rename a file on the Desktop directory, it does not highlight the extension.

Thanks.

Same problem exactly with Maverick. Very irritating.

---

### Post by giropizza on 2011-02-09
Any solution? I don't want to downgrade nautilus but I want a patch, possibly simply to apply, to solve the problem.

Thanks in advance

---

### Post by Plasma_NZ on 2011-08-01
i'm keen on finding a patch without down-grading..

---

### Post by Plasma_NZ on 2011-08-01
Well adding this ppa which has a patch-fix worked like a charm for me in natty 64bit...

[https://launchpad.net/~barcc/+archive/bugs]("https://launchpad.net/~barcc/+archive/bugs")

---

### Post by DarkDead on 2011-08-25
Working here too on a 32 bit maverick. Thanks Plasma_NZ.

---

