---
title: "What's a NAK bailout?"
date: 2011-02-02
forum: General Help
---

### Post by sabersong on 2011-02-02
I switched to terminal mode today by pressing CTRL+Alt+F1 in order to try to bring back my disappearing mouse cursor. While in terminal mode, I noticed that a string of numbers would appear every few seconds, followed by the following:

i2c i2c-3: sendbytes: NAK bailout

I hadn't typed any commands, I had simply switched to terminal mode in order to change back and see if my mouse cursor would return. I wrote the thing down and went out for a few hours. Just now, I got back and switched into terminal mode again, and it was still happening. What does this mean? Is it something I need to be concerned about?

Edit -- This is still happening after a restart. Is my computer going to explode now?

---

### Post by cipherboy_loc on 2011-02-02
I have not read it, but it looks like it might help:
[http://www.mail-archive.com/git-commits-head@vger.kernel.org/msg32955.html](http://www.mail-archive.com/git-commits-head@vger.kernel.org/msg32955.html)

Edit: After a quick read, it looks like it is a bug in your kernel.

1) What kernel version are you using,
2) Did you compile your kernel yourself,
and 3) What hardware are you using?


Cipherboy

---

### Post by sabersong on 2011-02-02
It's not a custom kernel or self-compiled. I know HOW to do that, but I wouldn't actually know what I was doing, so I don't.

I'm using Kubuntu 10.10 on an off-the-shelf HP Slimline s3100n. Everything is onboard on the asus m2nc51-ar motherboard. Nvidia GeForce 6150 LE, standard onboard audio, onboard wireless and ethernet. I do have an Ipod and a USB external hard drive hooked up to it, if that helps.

I should note that while I consider myself a pretty advanced USER, when it comes to the really technical stuff I'm just starting to get into it, so I don't really know all that much.

---

### Post by hansdown on 2011-02-02
Hi sabersong.

As cipherboy_loc suggests, it does appear to be a bug regression.

[http://stackoverflow.com/questions/505023/reading-writing-fram-using-i2c-on-linux](http://stackoverflow.com/questions/505023/reading-writing-fram-using-i2c-on-linux)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606081)

Someone seems to have found a solution for ATI.

[http://nabi-in-a-dream.blogspot.com/2011/01/solved-ati-radeon-2100-edid-kernel.html](http://nabi-in-a-dream.blogspot.com/2011/01/solved-ati-radeon-2100-edid-kernel.html)

---

### Post by sabersong on 2011-02-03
Ok, thank you. I'll report it as a bug and not worry too much about it for now.

---

