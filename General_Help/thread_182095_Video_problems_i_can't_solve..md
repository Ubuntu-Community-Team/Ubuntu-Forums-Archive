---
title: "Video problems i can't solve."
date: 2006-05-25
forum: General Help
---

### Post by Biffy on 2006-05-25
The problem i have is that there are tearing in my videos. I am using the fglrx driver and when trying non-tearing video drivers such as vidix or XV, there is only a blank image where the video should be on my TV. I can use the gl2 driver and enable vsync in driconf, but then i only get non-tearing on my monitor and tearing on my TV. Was thinking about using fbxine with vidix driver cause that would solve my problem, but i only get a "Video port failed" error message. Using fbxine was how i solved the issue in Suse. Ok, so here are my questions:

1) Why is there a blank screen where the video should be on my TV when using XV and/or Vidix? If i use the vesa driver instead, the Vidix driver works. But it wont do that in fglrx.

2) When having enabled vsync in driconf, why was the tearing removed ONLY on my monitor but not my TV?

3) This one is important. Why does fbxine just says "Video port failed" when trying to play a video?

4) In the ATI control panel (fireglcontrol) there is no TV-out options. Only "Dualscreen" . I dont know why this is, because there have been a TV-out tab there last time i checked. Maybe fglrx think my TV is a monitor?

I would be really glad if someone could help me with this. I have searched for answers but can't find any.

---

### Post by Biffy on 2006-05-25
Fixed by doing this:

1) Install grubconf
2) sudo grubconf
3) Find your kernel and click "Edit"
4) Add the line vga=0x318
5) Reboot and use the kernel you just edited
6) Your framebuffer is now 1024x768 with the colordepth 24 and fbxine works without problem.

---

### Post by chabayo on 2006-08-13
...as i tried running fbxine a long time before got this...have a look.

If fbxine fails try:```
fbxine --verbose=3 <mrl>[CODE]
```[/CODE]
...that should give you output to solve most Problems.

Me took "Video port failed." too strange.

The solution was ```
fbset --depth 16
```
...me told fbxine by itself.

Take about 16 or more.

Yous can try the "-A" option as Audio driver Selection too, beside it is not explained by```
fbxine --help
``` the Option works - maybe more do...

---

