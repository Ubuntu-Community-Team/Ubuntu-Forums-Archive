---
title: "Using Middle mouse button click in vmplayer"
date: 2009-11-06
forum: General Help
---

### Post by wangrui on 2009-11-06
Hi,

I have some software which need middle click. And I want to run them in vmplayer, for example, blender. But unfortunately the middle click does not working in vmplayer. This is probably a bug of the vmplayer which will be fixed later. But currently it makes things impossible. It took me many days to finally find a solution. I post it here so other people who has the same problem won't need to stuck again.

There are three ways to make middle click work. If your mouse have two extra buttons (Backwords button and Forwords button) at the side, one of them act as middle button in vmplayer.

If your mouse only have five keys (Left,Middle,Right, Wheel Up, Wheel Down), then you can connect two mouses into your computer. And put the following line into vmx file,
```
usb.generic.allowHID = "TRUE"
```
And connect one of them directly into vmplayer.

The best solution I just find out is that, you can use
```
xinput list
```
to find out your mouse, and use
```
xinput set-button-map <device id> 1 9 3
```
to remap the middle button from 2 to 9. And then your middle button will works as it should in vmplayer.

---

### Post by wangrui on 2009-11-12
Sorry about this post. The middle button works very well in ubuntu 9.10 and vmplayer 3.0

---

