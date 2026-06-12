---
title: "100% free ubuntu"
date: 2010-06-29
forum: General Help
---

### Post by eec on 2010-06-29
Hi,

I just want to use 100% free (non-proprietary) softwares, can you help me to choose between the repos, and if someone has done it before, can s/he give me some advice (like how can I avoid installing nonfree software unintentionally) 

I want to experiment a bit because till this day, I did not care about it. For me it just should be working. Now, I want to see if I can do it without any problems, and experience the 100% free linux.

Thanks
eec

---

### Post by Noz3001 on 2010-06-29
Have you considered using gNewSense instead?

---

### Post by flick on 2010-06-29
Disable the Restricted and Multiverse repos in /etc/apt/sources.list

sudo apt-get update

sudo apt-get install vrms

vrms

sudo apt-get purge WHATEVER PACKAGES VRMS TELLS YOU ARE NON-FREE

vrms 

should be nothing non-free left

---

### Post by eec on 2010-06-29
> **Noz3001 said:**
> Have you considered using gNewSense instead?

Yes thought about it, but wanted to use ubuntu instead of a fork.

> **flick said:**
> Disable the Restricted and Multiverse repos in /etc/apt/sources.list

sudo apt-get update

sudo apt-get install vrms

vrms

sudo apt-get purge WHATEVER PACKAGES VRMS TELLS YOU ARE NON-FREE

vrms 

should be nothing non-free left

Thanks a lot, I'll give it a try

And, is universe also "safe" to use?

---

### Post by flick on 2010-06-29
The repository components are:

    *

      Main - Officially supported software.
    *

      Restricted - Supported software that is not available under a completely free license.
    *

      Universe - Community maintained software, i.e. not officially supported software.
    *

      Multiverse - Software that is not free. 

From : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Simian Man on 2010-06-29
> **eec said:**
> Hi,

I just want to use 100% free (non-proprietary) softwares...can s/he give me some advice

You could try to get some hobbies.  Maybe go outside sometimes.

---

### Post by alket on 2010-06-29
As I remember (im not sure) Alternate CD has an option to install Free Software Only

---

### Post by eec on 2010-06-30
> **Simian Man said:**
> You could try to get some hobbies.  Maybe go outside sometimes.

Thanks, I'll take it into consideration...

Do they pay people like you to write such unproductive ****, or is it just your stupidity?

---

### Post by ThesaurusRex on 2010-06-30
> **eec said:**
> Thanks, I'll take it into consideration...

Do they pay people like you to write such unproductive ****, or is it just your stupidity?

Simian was simply making a joke. It was funny, though overused.

---

