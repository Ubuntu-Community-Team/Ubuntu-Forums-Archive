---
title: "startup themes"
date: 2011-06-15
forum: General Help
---

### Post by link15 on 2011-06-15
so I installed the earth sunrise plymouth theme with super boot manager, and it worked, but only when I was turning it off, it still works when I'm turning it on, except it sits there for like 30 seconds blinking an underscore and then the theme starts up and does nothing for about 3 seconds (it doesn't animate or whatever), and then the gdm screen comes up, so why isn't plymouth really working on startup? and is there a way to fix it?

---

### Post by link15 on 2011-06-15
86 views and no responses? does anyone have any ideas?

---

### Post by link15 on 2011-06-16
129 views! bump

---

### Post by link15 on 2011-06-17
can someone at least tell me that this is normal to not work on startup???:confused: bump

---

### Post by ClientAlive on 2011-06-17
I feel for ya' man! I know that doesn't solve your problem; and, if I knew anything about it I would help. Maybe try posting here: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)  "Installation and Upgrades" or here: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)  "Multimedia and Video" or possibly even here: [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)  "Desktop Environments."

That's what I've done before when nothing was happening: re-evaluate where I had posted, marked that thread as solved and posted elsewhere. The folks here at the forum are really great. Probably just that no one has come along that knows.

HTH
----------------------

Edit:

Oh! And adding tags seems to help sometimes. I didn't notice whether you had them on this thread or not but they do help. I think (I think) that the tags come up when someone does a search - kinda like keywords or something. Don't quote me on that though.

---

### Post by mastablasta on 2011-06-17
You didn't post any relevant information for someone to help you. nothing about your computer, what kind of graphics card do you use. does it use proprietary or opensource drivers? nothing at all. just: my boot screen does not work.
 
anyway you could try typing this in terminal:
 
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
 
 
it worked for me.

---

### Post by nomko on 2011-06-17
> **mastablasta said:**
> You didn't post any relevant information for someone to help you. 
And nobody even asked him for more information.

---

### Post by ClientAlive on 2011-06-17
> **mastablasta said:**
> You didn't post any relevant information for someone to help you. nothing about your computer, what kind of graphics card do you use. does it use proprietary or opensource drivers? nothing at all. just: my boot screen does not work.
 
anyway you could try typing this in terminal:
 
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
 
 
it worked for me.


Does that code sample modify a configuration file on his system? If so, it might be wise for him to make a copy of the original first so he has it to go back to if necessary.

I'm not certain what that is though because the last part of the path does not look like a file name but a command. I'm not sure I've seen something like this before.

Just a suggestion.

---

### Post by link15 on 2011-06-17
sorry I didn't check the thread, but I'm using an acer aspire one 532h-2268 and it has an itegrated intel graphics card thats all I know. and I'll try ```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
``` I can't figure out how to quote so thats why i didn't quote hopefully it'll work

---

### Post by link15 on 2011-06-17
how do I find out what kind of drivers I'm using?

---

### Post by ClientAlive on 2011-06-17
> **link15 said:**
> sorry I didn't check the thread, but I'm using an acer aspire one 532h-2268 and it has an itegrated intel graphics card thats all I know. and I'll try ```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
``` I can't figure out how to quote so thats why i didn't quote hopefully it'll work

I'm not sure if this is going to display correctly or not but there is "Quote" and "Code" and they are based on what are called "tags." So I know you can see it correctly - just click the **button** at the bottom of this post that says "Quote" and it will make this message display in plain text so you can see it. So click the button and look at what is below.

> 
Above and below are called tags. There is an opening one and a closing one. The opening one is above and the closing one is below. Notice the difference between the two? On has a slash in it before the word but after the opening bracket. There is also a way to use the editor - some button to click - to do it, but I don't know what button it is. I always just type them in.


```

These tags work the same way the "Quote" ones do - with an opening and closing tag - but the word between the brackets is just different. The word in the brackets has to be the same between the opening and closing tag. If there is a capital first letter in the opening tag there has to be a capital first letter in the closing one too. HTML also works this way (with opening and closing tags. The basics of HTML are really pretty simple and you could probably make your own basic web site in a day if you wanted to.

```

---

### Post by link15 on 2011-06-17
now I know how to quote, I tried that and now it does the same thing axcept it starts earlier, and it still stays on the first frame (before the sun goes up)any other ideas?

---

### Post by link15 on 2011-06-18
no one else has any ideas? all that that command did was start it earlier, which is good, except it stays on the first frame or whatever you want to call it

---

### Post by link15 on 2011-06-19
really no one has any ideas:confused: bump

---

### Post by ClientAlive on 2011-06-20
is there a forum at gnome-look.org??

The folks there might be more familiar with this sort of thing. I've never messed with it. Just trying to offer some ideas where you might find some help.
-----------------------

Edit:

I found a link to their forum:

[http://gnome-look.org/comments/discussion.php?PHPSESSID=1b2ac3018f13d70323991869de790797](http://gnome-look.org/comments/discussion.php?PHPSESSID=1b2ac3018f13d70323991869de790797)

Hate to make a suggestion like that. I love the guys here at Ubuntu forums. Just hate to see you sit here and not get the help you need. What else can you do?
------------------------

Edit 2:

If it was me - I might even look for the type of startup thingy, whatever you are talking about there at gnome look, click a particular one (any one) and see if the window the opens up contains a link to the orig creator's site or some way to contact them. If you follow the trail you might find someone involved in that to ask where to look for help with it.

---

### Post by link15 on 2011-07-21
I have no idea what was wrong with it, but, I reinstalled ubuntu all over again and I did the echo framebuffer thing and it worked! if your wondering why I reinstalled you can look at this thread [http://ubuntuforums.org/showthread.php?t=1798191](http://ubuntuforums.org/showthread.php?t=1798191), so thanks for all your help and I'm gonna mark this thread as solved

---

