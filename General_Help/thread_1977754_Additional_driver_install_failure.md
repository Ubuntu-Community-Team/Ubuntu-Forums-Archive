---
title: "Additional driver install failure"
date: 2012-05-10
forum: General Help
---

### Post by samwillc on 2012-05-10
Hi everyone,

So I'm up and running on ubuntu 12.04 and liking what I see so far!!

However, problem #1, knew it wouldn't be long:

"Sorry, the installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

Trying to install additional drivers: No proprietary drivers are in use on this system

ATI/AMD proprietary FGLRX graphics driver (post release)

Wont install basically. Any ideas? Got an AMD Phenom II if that makes any difference?

Maybe I could post the log file if I knew how to find it.

Thanks.

Sam.

---

### Post by samwillc on 2012-05-10
And as I am used to windows, there used to be a little ATI icon in the bottom right where I could set overscan settings etc. Right now I'm stuck with a 1.5" black border all the way round and can't find where to access these settings.

Sam.

---

### Post by steeldriver on 2012-05-10
does it give you the option of a non post release driver? if so try that

I couldn't get the post-release one to install on my AMD A-6 either, I've seen a few reports of that failing - the log file is exactly where it says it is (/var/log/)

the regular proprietary and the one I downloaded direct from the web both installed (the latter fixed my 64-bit HDMI sound issue) - either should include the catalyst control center application (which is the thing for managing the settings)

---

### Post by samwillc on 2012-05-10
Hi thanks yes, I am familiar with the CCC.

It wouldn't allow me to make any changes until I opened as super user in terminal i.e. gksudo amdcccle

Pardon my ignorance, I haven't even tried navigating folders/files yet!

I had to change overscan to 0% in order to get full screen. Working now. Thanks to another thread with the above code posted (haven't got the URL). :)

Sam.

---

