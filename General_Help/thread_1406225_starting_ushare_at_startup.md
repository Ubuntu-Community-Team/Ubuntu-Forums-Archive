---
title: "starting ushare at startup"
date: 2010-02-13
forum: General Help
---

### Post by Crazy K on 2010-02-13
Hey guys, I need a little help with this. I use Ubuntu 8.04 and I recently re-installed ushare. Anyways I want to make it possible to start ushare at start up. I just don't feel like having to start ushare everytime I want to stream media to my 360. 

Help is needed. :)

---

### Post by mirosol on 2010-02-13
Normal installation of ushare should make symlink to /etc/rc3.d as S20ushare

If that's not starting like in your case, you can try to add it manually, or change it's order in loading.

Runlevel 3 is the graphical user's runlevel, if you don't run your ubuntu in graphic mode, i suggest you move your link to other runlevel like /etc/rc2.d

Or have you debugged why it fails to load?
+m

---

### Post by Crazy K on 2010-02-13
I don't use graphic mode in Ubuntu, because my computers quite old. 

But I have no idea what you're talking about. It works fine with my xbox 360, I just have to type "ushare -x" everytime to start it. I just want to make it startup at boot. I'm still fairly new to Linux/Ubuntu and I have no idea of what I'm doing.

Wait, I think I know what you mean. I'll check into it.

Yeah I have no idea on what I'm doing.

---

### Post by Crazy K on 2010-02-13
How would I change the runlevel to rc2.d? And if that's not it, how do I make ushare start right at the boot.

---

### Post by anselm on 2010-02-13
Check this link out                                   [https://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/](https://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/)

---

### Post by Crazy K on 2010-02-14
Sorry, that didn't help me at all. I was able to install ushare with no problems. I can start it and stream media to my xbox 360 with no problem. It's just that Ushare doesn't start up automatically when I start my computer. I'd like to change that.

---

### Post by shawnkltucker on 2010-02-17
I am using 9.1 but I had the same annoying issue.

I was able to solve it with these commands.

[PHP]
sudo update-rc.d -f ushare remove
sudo update-rc.d ushare start 90 2 3 4 5 . stop 10 0 1 6 .
[/PHP]

Now I'm working on making ushare scan the directories automatically periodically.
I'm going to do this by loading the web interface's refresh page with lynxx periodically with cron.

Good luck.

---

### Post by Spoony_Man on 2010-08-12
Sorry to drag up an old thread...

But I was having trouble getting ushare to load.

I had followed a guide somewhere, which suggested putting something along the lines of:

```
service ushare start
```

In /etc/rc.local (which is one of the files that executes when ubuntu boots)

I looked /etc/rc2.d/ and sure enough S20Ushare was in there.

After removing the command to start ushare from /etc/rc.local it starts up no problem.

Hope this will clear up some issues for people viewing this thread in the future.

---

