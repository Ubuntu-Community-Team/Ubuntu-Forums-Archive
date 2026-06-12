---
title: "Nvidia drivers - slow kwin"
date: 2012-08-11
forum: General Help
---

### Post by kurci2 on 2012-08-11
I think i have a problem with my nvidia graphic drivers.

I have Kubuntu 12.04 64-bit with KDE 4.9 installed.
For some time I used pre-installed nouveau driver. All kwin desktop effects worked fine, but i had some other issues.
So I installed Nvidia driver (version 295.40). But now kwin effects are very very slow and choppy.
Does anyone know how to fix this.

I remember that i had similar problems with compiz and unity but i found this fix: [http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

This fixed those kind of problems.

So, does anyone know how could I fix Kwin-nvidia issues??

---

### Post by kurci2 on 2012-08-13
A little update.

I have installed Kubuntu 12.04 LTS 32-bit. I have updated to kernel 3.2.0-29 and KDE 4.9.
After that i installed Nvidia drivers 295.40.

But problem is still present... Maybe it is just a bit better, but still very bad...compared to nouveau.

so, does anyone experience same problems and possibly knows the solution?

---

### Post by robtygart on 2012-08-13
I am having nothing but trouble with ALL Nvidia drivers on both 32 and 64bit Ubuntu & Kubuntu. Its so slow you might as well call it a freeze. nouveau is the only one that works.

---

### Post by kurci2 on 2012-08-13
Yes, i am getting that.
But problem is that with nouveau drivers i have really serious problems with vlc and many other programs... And with nvidia drivers they work fine.

Only kwin seem to be the problem so far.

What about ATI cards? Are drivers for them better??

---

### Post by robtygart on 2012-08-13
> **kurci2 said:**
> Yes, i am getting that.
But problem is that with nouveau drivers i have really serious problems with vlc and many other programs... And with nvidia drivers they work fine.

Only kwin seem to be the problem so far.

What about ATI cards? Are drivers for them better??

According to what I have read, Nvida has not been very kind to Linux, in the way of drivers.  

ATI so far has been good to me, Accept for ATI is bad for gaming :confused:


Article [Linus Torvalds Gives Nvidia the Finger. Literally]("http://www.wired.com/wiredenterprise/2012/06/torvalds-nvidia-linux/")

---

### Post by kurci2 on 2012-08-14
I have seen that video when Linus gives finger to nvidia =)

So if i am getting this right I can not do anything but wait till nvidia fixes their driver??

---

### Post by robtygart on 2012-08-14
That is what I am doing, but I am sure one of the other members here would have a better answer.

Until then post the results of this. 
```
lspci -nnk | grep -iA2 vga
```

---

### Post by kurci2 on 2012-08-14
I also hope that someone knows that solution. I mean, this issue must affect every user who own nvidia graphic card and have KDE. =)

This is my output:

```
marko@ToShiba:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT216 [GeForce GT 330M] [10de:0a29] (rev a2)
        Subsystem: Toshiba America Info Systems Device [1179:fd30]
        Kernel driver in use: nvidia
marko@ToShiba:~$ 
```

---

### Post by SeijiSensei on 2012-08-14
> **kurci2 said:**
> I mean, this issue must affect every user who own nvidia graphic card and have KDE. =)

No, it doesn't.  I'm running Kubuntu 12.04 on my 9500GT card with nvidia-current.  I haven't had any problems whatsoever.  I don't bother with any 3D or other types of special effects on the desktop, though.  I also have an ASUS 1201n netbook with NVIDIA graphics and have no problems there either.

For those of you having problems, did you install a clean copy of Kubuntu 12.04 from the CD, or were you updating from an earlier version, or installing kubuntu-desktop on top of an existing Ubuntu installation?  Both my machines are using clean installs.

---

### Post by kurci2 on 2012-08-14
Lucky you.
I have done clean install just two days ago ...

---

### Post by SeijiSensei on 2012-08-14
Well, as I say, I don't use any desktop effects except the one where you can display all the open windows by moving the mouse the upper left corner of the screen.  I never saw much value in things like the "cube" other than eye candy.  I also have an older adapter (9500GT) that has been supported for some time.  Maybe there are issues with newer adapters?

---

### Post by kurci2 on 2012-08-14
What i think is that in my opinion Nvidia should make some good drivers for Linux sistems. They are one of the biggest companies...

And about Desktop Effect. I like them, because my desktop looks very beautiful and "custom made" ... for what i like.

---

### Post by robtygart on 2012-08-14
My install is clean too, I have effects on too.

---

### Post by kurci2 on 2012-08-14
I tried Xrender today - and it works just fine
So there is a problem with OpenGl i guess...

---

### Post by kurci2 on 2012-08-22
I have done some research and this is what i did (it makes my system significantly faster):

I'll just post a link =)
[LINK]("http://ubuntuforums.org/showthread.php?t=1748642")

---

