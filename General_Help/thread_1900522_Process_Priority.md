---
title: "Process Priority"
date: 2011-12-26
forum: General Help
---

### Post by kurci2 on 2011-12-26
HI all!
I have a Toshiba laptop with 4gb ram and Intel i5 cpu. But some programs are really slow... Firefox, Nautlus, even compiz

Then i went to gnome-system-monitor and saw that all priorities are automaticali set to 8... Is it possible to permanentaly set priorities for these programs to 0 or maybe to -2. I think that this could really help.
And just to know. My processor is never on 100%... But programs are slow... A would really like to change that.

---

### Post by lovinglinux on 2011-12-27
That is most likely an issue with video driver an not a processor priority issue. 

Check if you have installed the latest driver for your video card. You can do that using the "Additional Drivers" application. If no drivers are available there, then most likely your card is blacklisted. In this case, get the model of your card and search for it in the forums for a solution.

Although I really enjoyed Unity 3D, I have found that Compiz performance wasn't great. Although I haven't experienced issues like you, dragging windows would temporarily freeze any flash video on my machine and window movement wasn't smooth. So I tried Unity 2D, which doesn't use Compiz, and it works great. Recently, I moved to gnome-shell, which also has better performance than Compiz.

---

### Post by kurci2 on 2011-12-27
I have Nvidia drivers enabled. I own Toshiba a660 laptop - Nvidia GeForce 330M graphic card.

When i configured priority for program called "plugin-container" every single movie in flash player was playet greatly.

And i don't feel like moving to other desktop environment. I tried Gnome Shell on Fedora and i didn't like it. One of the reasons to use Linux is COMPIZ... And i really don't want to move to Unity 2D or Gnome 3 where is no compiz.

There must be a way to fix these problems...

---

### Post by lovinglinux on 2011-12-27
> **kurci2 said:**
> I have Nvidia drivers enabled. I own Toshiba a660 laptop - Nvidia GeForce 330M graphic card.

When i configured priority for program called "plugin-container" every single movie in flash player was playet greatly.

And i don't feel like moving to other desktop environment. I tried Gnome Shell on Fedora and i didn't like it. One of the reasons to use Linux is COMPIZ... And i really don't want to move to Unity 2D or Gnome 3 where is no compiz.

There must be a way to fix these problems...

Looking at your desktop, without any window open, do you see a shadow below the top panel?

---

### Post by kurci2 on 2011-12-27
yes i do

---

### Post by lovinglinux on 2011-12-30
Try this: [http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

BTW, your issue with the *plugin-container* being resolved with the process priority is most likely to do with the fact that flash uses a lot of CPU. You could try to force GPU validation. See [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by kurci2 on 2011-12-30
Man... you are the best!!!
[http://www.jondev.net/articles/Ubunt...choppy_or_slow](http://www.jondev.net/articles/Ubunt...choppy_or_slow)
that fix made a miracle.
Now my computer is working fast. And Ubuntu 11.10 is working a lot faster than windows 7 on the same machine.

Thanks a lot really!!!!

Edit: And even all my HD 1080p videos are played as they should be. Great!

---

### Post by lovinglinux on 2011-12-30
You are welcome.

---

### Post by BifyMybriffup on 2012-06-01
[payday loans online](http://onedaypaydayloansonline.com/#bubuntuforums.org) - [payday loans online]("http://onedaypaydayloansonline.com/#aubuntuforums.org") , [http://onedaypaydayloansonline.com/#subuntuforums.org](http://onedaypaydayloansonline.com/#subuntuforums.org) payday loans online

---

