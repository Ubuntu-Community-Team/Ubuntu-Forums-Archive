---
title: "Weird crashing problem (&quot;Unknown key pressed&quot;)"
date: 2009-12-25
forum: General Help
---

### Post by lesath on 2009-12-25
Since installing Karmic, my computer has started to crash in steps, as though it were slowly going insane. First Firefox locks up and though it quits, the process cannot be killed so it won't restart. Then Pidgin dies in the same manner. Once this has started, many of the Gnome menus no longer work, and, significantly, the computer cannot be shut down or rebooted. It must be turned off manually. This all happens about once or twice daily. 

Today when it happened I switched to a tty screen to see if I could force the computer to reboot thus, when I saw my screen being spammed with the following error message:

atkbd.c: Unknown key pressed (translated set 2, code 0xd on is a0060/serio0)
atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known
atkbd.c: Unknown key released (translated set 2, code 0xd on is a0060/serio0)
atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known

My first instinct was that there was a stuck key, but after meticulous smashing of all the keys on my keyboard, it became clear this was probably not the case, especially since the computer works fine after rebooting and it's not a constant problem. It does happen often enough, however, that I'm beginning to worry about the integrity of my hard drive. Has anyone else ever encountered anything like this? What should I do?

Finally, I don't know if this is related, but when the computer is behaving normally and I switch to tty then try to switch back, I get an unassailable blank screen and must again reboot manually to get rid of it. What's up with that?

---

### Post by lesath on 2009-12-27
Just some follow-up information to this: Today when it happened, the error message was slightly different (it referred to a "raw" set rather than a "translated" one, among other things).

---

### Post by antony.s on 2009-12-27
Have you read [http://embraceubuntu.com/2006/02/10/unknown-key-pressed-error/](http://embraceubuntu.com/2006/02/10/unknown-key-pressed-error/) ?

atkbd = a keyboard driver, so it is a problem relating to keyboards though not necessarily anything to do with a physical problem with your keyboard

---

### Post by lesath on 2009-12-27
I hadn't seen that, but the file that the post says to edit doesn't seem to exist. I should note, though, that I am indeed using a laptop. However, this seems to happen only intermittently (since if I switch to a tty screen right now, it will display normally) and I've tried pressing every single key on my keyboard and none of them cause it.

---

### Post by antony.s on 2009-12-27
Hm, I think the file not existing any more could be to do with hotkey-setup being deprecated - [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/458961](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/458961)

Also [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111024](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111024) appears to be related

I am trying to figure out what this means for you :D

I have contacted the person who deprecated hotkey-setup to see if he has a better understanding

---

### Post by antony.s on 2009-12-29
According to Steve Langasek, "If the error message is happening repeatedly when no buttons are being pressed, then that's a kernel bug; the user needs to file a bug report
against the linux package with 'ubuntu-bug linux'.  Depending on how this is resolved in the kernel, there may also be a keymapping bug that needs to be resolved in the udev package."

So basically, run 'ubuntu-bug linux' to make a bug report, include everything you said in your original post

---

### Post by beanieweanie on 2010-01-08
This is very simple to fix; I had the same problem. (Do you have a Dell laptop? They tend to do this.)

According to some sources, a bug in the Dell BIOS is causing the spamming effect you are seeing. This apparently nonexistent key is resulting in the error. So all we have to do is disable the key. The post you read is old, and doesn't work with Karmic.

Place the following code in the file /etc/rc.local:
```
setkeycodes e00d 255
```This will set the code of the reported key, e00d, to 255 or 'null'; this will get rid of your problem. I can't help you with the random crashes, that's probably an altogether different issue.

---

### Post by lesath on 2010-01-09
I tried this and it didn't work. :\

---

