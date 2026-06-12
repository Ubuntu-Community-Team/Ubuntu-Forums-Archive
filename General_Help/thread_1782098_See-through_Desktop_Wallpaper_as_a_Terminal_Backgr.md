---
title: "See-through Desktop Wallpaper as a Terminal Background"
date: 2011-06-14
forum: General Help
---

### Post by Ender985 on 2011-06-14
Hello,

An asthetic question for you all. 

-- Edit with pictures for clarification --

This is the terminal on top of a clear desktop:
[[IMG]http://img685.imageshack.us/img685/8483/terminalstart.th.png[/IMG]](http://img685.imageshack.us/i/terminalstart.png/)

This is what I'd like it to be when I move it around and on top of other applications that block the background:
[[IMG]http://img853.imageshack.us/img853/1778/terminalmock1.th.png[/IMG]](http://img853.imageshack.us/i/terminalmock1.png/) [[IMG]http://img832.imageshack.us/img832/5849/terminalmock2.th.png[/IMG]](http://img832.imageshack.us/i/terminalmock2.png/)

-- Follow up --

It turns out this is the default behavior for the terminal background transparency in a clean ubuntu install. However I always install and configure compiz right away, and it seems compiz provides "real-transparency" to the terminal, making it so that you don't see the desktop anymore, but the applications between the terminal and the desktop. 

Is there any way to disable the "real-transparency" for the terminal in compiz?


-- Original OP --

I'm trying to make my terminal background to be the same as my wallpaper, but, instead of it just showing the upper-left corner of the whole thing (which is what happens when I simply set the image as a background), I would like it to be "dynamic", so that when you move the terminal around, the corresponding part of the wallpaper is shown. The idea is to mimic the behavior I get if I set the terminal background to be black with some transparency and there is nothing else open, so the terminal shows the corresponding part of the wallpaper below, but to do it the same way when there are fullscreen applications between the terminal and the desktop wallpaper.

If there is confusion to what I mean let me know and I'll try to put together some mockups. I have seen this working in some screenshots and I even got it to work somehow one time my NVidia drivers were not properly loaded, so I'm sort of positive it is possible, but I never found a way to do it.

Thanks a lot!

---

### Post by Habitual on 2011-06-14
I must have stared at this query for almost 30 minutes before I decided you were 1.) Drunk, or 2.) Stoned, or 3.) not explaining enough...

I came back hours later and decided it must be #3. :)

"the upper-left corner of the whole thing" needs further explanation. Of what whole thing?
Screenshots!

Are you trying to set transparency to "see" a desktop wallpaper, or set the terminal background to an image file AND have transparency?

I have an embedded desktop terminal (EDT) and 100% transparency.
If I change my desktop wallpaper, the EDT "sees" right through to it.

If I've missed the point altogether, I am neither 1.) or 2.)

Please let us know...

---

### Post by blueridgedog on 2011-06-14
I think the "upper left corner" implies that he/she has the terminal set with his desktop image as a background image, and it is so large, that he only sees the upper left corner of it.

Have you tried checking the box regarding "background scrolls"?  I assume you have.

---

### Post by Habitual on 2011-06-14
blueridgedog:

I thought that might be "the issue" but my interpretive skills aren't what they used to be. :(

Resizing the image to use as a terminal b/g image is my answer to that. :)

---

### Post by Ender985 on 2011-06-14
Hahaha 

Nope, not drunk or stoned, but seeing your reactions it probably would have helped my explanations xD I'll try to somewhat clarify the issue tonight, but tomorrow I'll come back with some pictures to spare me some 1000 words.

"The upper-left corner of the whole thing": If I simply set my wallpaper image as the terminal background (no transparencies for the sake of the argument), since my wallpaper is of 1920x1080 size and the terminal is only 80x24 characters, I only see the upper leftmost corner of the whole picture. Indeed if I maximize the terminal it will show the whole picture, but this is not what I'm trying to accomplish.

Now, checking "background scrolls" does just that, as I scroll down the terminal, the leftmost part of the image scrolls down, but (short of resizing the terminal) I'll never get to see the rightmost part of the image.

In order to clarify this a little bit more (before I actually get drunk and stoned xD), let's pretend I have an amazing pitch black wallpaper with four numbers: 1 in the top-left, 2 in the top-right, 3 in the bottom-left and 4 in the bottom-right. That wallpaper is 1920x1080 . Now if I simply set this wallpaper as my terminal background, I'll only see number 1. If I checking "background scrolls" I'll see 1 and eventually 3, but never 2 and 4. What I'm trying to accomplish is: if the terminal is located in the top-left part of the screen, it shows number 1 as a background, but if I manually move it to the bottom right, then it shows number 4.

You can accomplish this effect by having a transparent background for the terminal, and no other application open in your desktop. Then if you move the terminal from 1 to 4 it will show you both no problem. But as soon as you launch chrome or nautilus or something else, if you move the terminal on top of it, it will not show the desktop background anymore but whatever application is right below it. This is what I'm trying to avoid here.

Maybe I'm a complete utopist and no one thought this would be cool before me, or the answer is so simple no one had to ever ask about it (I'll double check the 'scroll background' think tomorrow when I'm back on my Ubuntu box, just in case). But I have the feeling the issue is simply too complex to be put in words for others to understand (this, and that I'm not the best book-writter ever xD). If this didn't made any sense to you whatsoever, please wait for my pictures tomorrow. Thanks for your patience! xD

---

### Post by Habitual on 2011-06-14
Quad[1-4] I "get". Seeing only Quad[13] I "get". 

Resize a copy of the desktop image and use that as the terminal b/g.

Scroll may have to be enabled to place the new terminal b/g image "just so" and then disable scrolling so it stays.

I suspect that your terminal is not really transparent. (see mine attached)
But you can't have both a trans terminal and a b/g image.

Please let us know...

---

### Post by Ender985 on 2011-06-15
Ok, as promised, the mockup of how I would like it to work.

This is the terminal on top of a clear desktop:
[[IMG]http://img685.imageshack.us/img685/8483/terminalstart.th.png[/IMG]](http://img685.imageshack.us/i/terminalstart.png/)

This is what I'd like it to be when I move it around and on top of other applications that block the background:
[[IMG]http://img853.imageshack.us/img853/1778/terminalmock1.th.png[/IMG]](http://img853.imageshack.us/i/terminalmock1.png/) [[IMG]http://img832.imageshack.us/img832/5849/terminalmock2.th.png[/IMG]](http://img832.imageshack.us/i/terminalmock2.png/)


I hope it is a lot clearer now. Is there any way to do this at all?

---

### Post by Helkaluin on 2011-06-15
That effect is generated when you set transparency in the terminal background and yet have no compositing manager running.  In this case gnome-terminal will emulate the transparency by doing a static shot of the desktop background.  You've mentioned this happened earlier when your NVIDIA card wasn't configured correctly - this is why it happened that way, because the compositing manager wasn't running.

Now, the problem here is that you're wanting it to be dynamic.  If you simply disable compositing then the effect would be that the background updates only when the terminal window is stationary, i.e. it won't re-paint when you're moving it.

I'm not sure about how to achieve a dynamic version of this.  Let me think...

---

### Post by Ender985 on 2011-06-17
You are right, if I disable compiz then the terminal transparency behaves exactly like I was asking for.

I take it that in the end this is a compiz 'feature', which provides 'real-transparency' for the terminal background. I have to say I find much nicer to always see your desktop background rather than the random application you happen to have open behind the terminal. 

So is there any way to disable the real-transparency for the terminal in compiz? I've searched around the compiz-settings-manager but I found no toogle, and google doesn't give me any answer either.

---

### Post by Helkaluin on 2011-06-17
Sadly you can only either get a composited desktop, or an un-composited desktop.  I don't think there's a way to selectively un-expose the composition to one window.

A quick workaround I can think of is to switch to a terminal emulator that doesn't support real transparency at all.  I can't remember but lxterminal might not.  Search your repository.

---

### Post by Ender985 on 2011-06-19
Well that is a pity. But at least the matter is clear now, thanks!

---

### Post by anishtain4 on 2011-07-08
If you found any way please send me a message and share it with me too. I liked the old style far more

---

