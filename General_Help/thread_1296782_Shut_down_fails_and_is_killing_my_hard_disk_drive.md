---
title: "Shut down fails and is killing my hard disk drive"
date: 2009-10-21
forum: General Help
---

### Post by startling on 2009-10-21
Ubuntu 8.10 on my laptop has recently been failing to shut down. It happens seemingly randomly. I am seriously worried about this because it is definitely causing hardware problems. Is there any way to force Ubuntu to shut down? The only way I can find is to press the power button for several seconds and then I get that nasty click sound from my hard disk drive that I know is going to kill it one day!

I have been using Ubuntu for years now and really don't want to go back to Windows but I cannot use software that might ruin my hard disk drive. A previous and not very old HDD was, I am fairly sure, broken by a previous version of Ubuntu. At the time I did not know that the clicking sound every time Ubuntu shut down was a bad thing. Recent versions of Ubuntu have not had this problem apart from this latest shutdown issue.

I noticed that the shutdown splash screen disappeared and the shut down process seemed to stop when it mentioned something about bluetooth. So I tried to uninstall bluetooth but that also removed Gnome! (I realise that that is a separate issue but I cannot help but mention it – it seems absolutely crazy to me that bluetooth is so welded into Gnome that you cannot remove it! I am really getting fed up with so many things about Gnome: it seems to be full of old and stupid bugs. Sorry about the rant but, as I say, I really hate the thought of going back to Windows - but if I can't get this sorted out, regrettably, that's what I'll have to do.)

I'd be really grateful for any help.

---

### Post by wilee-nilee on 2009-10-21
Your problem may be a hardware issue, rather then the operating system you might start with listing your setup and in general when this started happening and any associated possible installs. I have rarely seen this sort of behavior. Here is a alternative shutdown method you have to wait a second or two between key strokes after hitting alt-sysrq and then the key combination. [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by startling on 2009-10-21
Thanks for your reply wilee-nilee - it's much appreciated and thanks for the tip about the magic key.

I don't think it's hardware related. I haven't changed the hardware at all in over a year, but the shutdown freeze problem has started only in the last month or so and it occurs, at a rough guess, every tenth shutdowns. I'm pretty sure I haven't installed any software that might be causing it.

What information should I post, please?

---

### Post by wilee-nilee on 2009-10-21
> **startling said:**
> Thanks for your reply wilee-nilee - it's much appreciated and thanks for the tip about the magic key.

I don't think it's hardware related. I haven't changed the hardware at all in over a year, but the shutdown freeze problem has started only in the last month or so and it occurs, at a rough guess, every tenth shutdowns. I'm pretty sure I haven't installed any software that might be causing it.

What information should I post, please?

 You know I am not an expert with Linux I am more knowledgeable about what not to do then what to do. If it was me (I am from the reinstall camp as most of my computers have rather small HD sizes) I would back up and reinstall, but others may have a way of finding the root of your problems. I was not a big fan of Hardy, I upgrade as they come out or do fresh installs LTS means nothing to me as long as I have the ISO.

---

### Post by fluffman86 on 2009-10-21
You might want to take a look at this bug...everything should have been solved by now, though.
[https://bugs.launchpad.net/ubuntu/+bug/59695](https://bugs.launchpad.net/ubuntu/+bug/59695)

---

### Post by startling on 2009-10-24
Thanks Fluffman86, but I don't think that bug is affecting my laptop although it's impossible for me to tell because according to Smartmon tools by hard disk doesn't support SMART reporting!

The problem I have is the total lockup on shutdown that occurs sometimes. I wish I knew how to identify the culprit. Does anyone know if there's a log file anywhere that could help me trace what's causing the lockup?

---

### Post by ForgivenByJC on 2009-10-24
Well, I just had a similar problem and this finished the shutdown for me by running ssh from another computer--have no idea what caused the issue.
```
sudo reboot -fp
```
Hope this helps someone, as this was annoying.  I could not get the alt-sysrq to work for me.

---

### Post by startling on 2009-10-26
Thanks for your post, ForgivenByJC, but no other computer connects directly to this laptop. Thankfully the alt-sysreq worked for me yesterday. At first it didn't but then I pressed the alt-sysreq-b keys all at the same time and held them down for a few seconds and that seemed to do the trick. Though I have to say that this is not a good solution, and I'd be really interested to hear of any way to troubleshoot my shutdown problem.

---

