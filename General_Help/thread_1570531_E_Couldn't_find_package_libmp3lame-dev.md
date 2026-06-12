---
title: "E: Couldn't find package libmp3lame-dev"
date: 2010-09-08
forum: General Help
---

### Post by sosyopat on 2010-09-08
Hi There!
 
I'm newbie in ubuntu and trying to install ffmpeg but there's an error which i couldn't figure out.
 
**E: Couldn't find package libmp3lame-dev**

 
i'm trying somethings according to this article;
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
 
p.s: sorry for my bad english.

---

### Post by TNT1 on 2010-09-08
Share a little more around what you were doing when the error arrived?

---

### Post by Achilles124 on 2010-09-08
what version of ubuntu do you use? So, paste the command: uname -a in this thread.

---

### Post by coffeecat on 2010-09-08
> **sosyopat said:**
> **E: Couldn't find package libmp3lame-dev**


It's in the multiverse repository. In your link, under No 2, it does tell you to enable the universe and multiverse repositories. Normally, these would already be enabled but, if not, open System > Administration > Software Sources. Under the 'Ubuntu Software' tab make sure the universe and multiverse repositories are ticked and do a 'reload' if prompted.

Your system should now be able to find libmp3lame-dev. But if those repositories were already enabled, I don't know. Are you using Lucid, version 10.04?

---

### Post by sosyopat on 2010-09-08
> **coffeecat said:**
> It's in the multiverse repository. In your link, under No 2, it does tell you to enable the universe and multiverse repositories. Normally, these would already be enabled but, if not, open System > Administration > Software Sources. Under the 'Ubuntu Software' tab make sure the universe and multiverse repositories are ticked and do a 'reload' if prompted.
 
Your system should now be able to find libmp3lame-dev. But if those repositories were already enabled, I don't know. Are you using Lucid, version 10.04?
 
 
i've enabled universe and multiverse repositories according to this tutorial.
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
 
but there's no change at all. still can't find libmp3lame-dev.
using  Ubuntu Server 2.6.24-24-server

---

### Post by coffeecat on 2010-09-08
> **sosyopat said:**
> 
using  Ubuntu Server 2.6.24-24-server

That's version 8.04, Hardy heron. You've been following the wrong instructions - there probably was no libmp3lame-dev in Hardy. There would have been a different package. Go to your link and under 'Choose your Ubuntu', click on the link that takes you to the Hardy Heron/8.04 page. Then follow those instructions and you should be fine.

> **sosyopat said:**
> i've enabled universe and multiverse repositories according to this tutorial.
 [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

You didn't need a tutorial. I gave you all the steps necessary. Anyway, that's beside the point. Follow the Hardy howto.

**Edit:** out of interest - you describe yourself as a newbie, yet you are using a server version of a 2-year old release. Why did you not install the desktop version of the current long-term release - 10.04, Lucid Lynx?

---

### Post by sosyopat on 2010-09-08
> **coffeecat said:**
> That's version 8.04, Hardy heron. You've been following the wrong instructions - there probably was no libmp3lame-dev in Hardy. There would have been a different package. Go to your link and under 'Choose your Ubuntu', click on the link that takes you to the Hardy Heron/8.04 page. Then follow those instructions and you should be fine.
 
 
 
You didn't need a tutorial. I gave you all the steps necessary. Anyway, that's beside the point. Follow the Hardy howto.
 
**Edit:** out of interest - you describe yourself as a newbie, yet you are using a server version of a 2-year old release. Why did you not install the desktop version of the current long-term release - 10.04, Lucid Lynx?
 
 
is there any way to install ffmpeg on this relase?
8.04 hardy server

---

### Post by coffeecat on 2010-09-08
> **sosyopat said:**
> is there any way to install ffmpeg on this relase?
8.04 hardy server

Go back and read my previous post:

> **coffeecat said:**
> Go to your link and under 'Choose your Ubuntu', click on the link that takes you to the Hardy Heron/8.04 page.

All the instructions on that link can be done from the command line, so it should work in the server version. The problem with libmp3lame-dev is that you were (I guess) following the Lucid/10.04 instructions. I can't help you any more. The instructions you found seem clear and complete. It's just that you were using the wrong version.

---

