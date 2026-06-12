---
title: "Chrome puts itself on Startup Applications"
date: 2012-05-14
forum: General Help
---

### Post by bobzr on 2012-05-14
Google Chrome puts itself on my Startup Applications. Processes like "chrome-no-startup-window", "chrome-sandbox", "chrome-type-zygote", etc. keep on running on the background. If I remove Chrome from my Startup Applications, it will show back next time I start the computer. Does anyone else noticed this?

---

### Post by fragos on 2012-05-14
It's called pre-loading. Chrome and Chromium do this so that the browser comes up very fast. If the memory used is needed by another ap it will be swapped out to disk. Restoring a swapped ap is faster than loading from the file system. There is no need to be concerned and you get improved performance.

---

### Post by bobzr on 2012-05-15
> **fragos said:**
> It's called pre-loading. Chrome and Chromium do this so that the browser comes up very fast. If the memory used is needed by another ap it will be swapped out to disk. Restoring a swapped ap is faster than loading from the file system. There is no need to be concerned and you get improved performance.

Thanks for your feedback, but I'm not sure if I should not be concerned about this behavior that reminds me of MS viruses and other malicious software.
Of course Chrome will come up very fast and a newbie would say that Chrome is faster than Firefox :)
But Ubuntu startup will be much slower. Chrome should not be the one to decide if today I'm going to use it or any other browser.
Moreover I've also noticed that sometimes it sucks all my bandwidth, downloading who knows what and why. And when I kill those chrome processes the download stops.
Google is getting too big. Everybody including myself is using a lot of useful Google services. But this is not a reason for misbehaving like this.
So for now I've just unistalled Google Chrome. ):P
I've heard in other forums that Chromium does not behave the same way. I may try it one of these day and see.

---

### Post by vasa1 on 2012-05-15
> **fragos said:**
> It's called pre-loading. Chrome and Chromium do this so that the browser comes up very fast. If the memory used is needed by another ap it will be swapped out to disk. Restoring a swapped ap is faster than loading from the file system. There is no need to be concerned and you get improved performance.
Do you see what the OP sees? I don't.

Just after you login and you check for the processes mentioned by OP, do you see any of them? I don't. 

Even if I use Chrome and then close Chrome and check for processes, I don't see what OP sees.

Which command enables you to see these specific processes, assuming you do see them yourself? "*"chrome-no-startup-window", "chrome-sandbox", "chrome-type-zygote",*"

I also don't see Chrome in my Startup Applications.

---

### Post by bobzr on 2012-05-15
> Do you see what the OP sees? I don't.

Just after you login and you check for the processes mentioned by OP, do you see any of them? I don't. 

Even if I use Chrome and then close Chrome and check for processes, I don't see what OP sees.

Which command enables you to see these specific processes, assuming you do see them yourself? "*"chrome-no-startup-window", "chrome-sandbox", "chrome-type-zygote",*"

I also don't see Chrome in my Startup Applications.


If I removed Chrome from my startup applications, and if I didn't start Chrome, nothing happened. But if I started Chrome and then checked my startup applications, Chrome was there again.

I saw those processes in the system monitor.

And by the way I'm using Precise with all updates.
I can't change my profile details. If I go to "Edit your details" I get the message "you do not have permission to access this page." Does anybody know what should I do to fix this?

---

### Post by Ubun2to on 2012-05-15
> **bobzr said:**
> Thanks for your feedback, but I'm not sure if I should not be concerned about this behavior that reminds me of MS viruses and other malicious software.
But Ubuntu startup will be much slower.
Startup applications are perfectly normal. Some less recognized examples include the clock, updater, system files, and Unity (or Gnome, depending on what you're using, or any other desktop environment).
You shouldn't worry about startup speed unless you have a low amount of RAM, such as less than 2 GB, in which case you probably have a slow boot time without any other applications starting automatically.

---

### Post by lolpenguin on 2012-05-15
Google Chomre has a settings where it keeps background processes after it quits. This can be turned off by going to Wrench > Settings > Under the Bonnet > Background Apps,

---

### Post by bobzr on 2012-05-15
> **lolpenguin said:**
> Google Chomre has a settings where it keeps background processes after it quits. This can be turned off by going to Wrench > Settings > Under the Bonnet > Background Apps,

Thanks lolpenguin ! I didn't consider this option ! I will install Chrome again, and see if I can do something in the Settings :)

---

### Post by vasa1 on 2012-05-15
> **lolpenguin said:**
> Google Chomre has a settings where it keeps background processes after it quits. This can be turned off by going to Wrench > Settings > Under the Bonnet > Background Apps,I have that **unticked**.

---

### Post by bobzr on 2012-05-15
> **lolpenguin said:**
> Google Chomre has a settings where it keeps background processes after it quits. This can be turned off by going to Wrench > Settings > Under the Bonnet > Background Apps,

That did it, I went to 'Under the Hood' and unticked "Background Apps". Thanks again lolpenguin!

---

### Post by Paqman on 2012-05-15
IIRC, the Chrome update the first included this behaviour also came with a popup that informed you and gave you the option to decline. But yes, it is now the default. It's a little bit of Chrome OS sneaking onto your machine.

---

### Post by dionizion on 2013-01-06
> **lolpenguin said:**
> Google Chomre has a settings where it keeps background processes after it quits. This can be turned off by going to Wrench > Settings > Under the Bonnet > Background Apps,

Thank you **lolpenguin =)**

---

