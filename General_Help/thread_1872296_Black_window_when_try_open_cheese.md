---
title: "Black window when try open cheese"
date: 2011-10-30
forum: General Help
---

### Post by xavi fernandez on 2011-10-30
Hi!!! I just connect my webcam for make it work in ubuntu 11.10, is a logitech hd webcam c270, they recognize the device but I can not make it works, I downloaded cheese two times, and when I try stat it, just open the window completely black. any suggestions?

Thanks in advance

---

### Post by Paddy Landau on 2011-10-30
What version of Ubuntu?

32-bit or 64-bit?

If you are using 64-bit, try doing this and tell us whether or not it works:

[LIST]
[*]Open a terminal.
[*]Type the following (you can cut-and-paste) and press Enter:```
LD_PRELOAD='/usr/lib32/libv4l/v4l1compat.so' cheese
```
[/LIST]

---

### Post by xavi fernandez on 2011-10-30
Thanks for your answer, no, I'm running in 32, can I use the same command?

---

### Post by Paddy Landau on 2011-10-31
> **xavi fernandez said:**
> Thanks for your answer, no, I'm running in 32, can I use the same command?
No, the command is only for 32-bit programs running on 64-bit machines. It was a bit of a shot in the dark.

I'm sorry, I don't know much about webcams. A quick search on Google indicated that you may need a different driver.

Plug in your webcam. Open Additional Drivers. See if anything is listed there. If it is, try enabling it (you may need to log out and in again) and see whether or not it works.

If that doesn't work:
Plug in your webcam. Open your terminal and enter the command [FONT=Fixedsys]lsusb[/FONT]. Look for the device ID -- it should look something like [FONT=Fixedsys]046d:0825[/FONT]. Google with that ID.

You could also look at [Logitech's website]("http://www.logitech.com/en-gb/support-downloads?selectedcrid=435") to see if there are any Linux driver downloads for your model. I tried looking but the site is not responding at the moment.

---

### Post by daftlad on 2011-10-31
Have you tried starting cheese from the terminal? This might help in finding out why cheese is not working. I have cheese working fine on my desktop, but not on my laptop. Too busy to fix it right now, skype works fine on it though so I know its not the cam.
I prefer using guvcview over cheese as it has more options.

---

### Post by no2498 on 2011-10-31
you may try this in a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese click enter

---

### Post by xavi fernandez on 2011-11-01
Thanks for your answer, I just typed the command for reload cheese and appear this in the terminal
[IMG]http://ubuntuforums.org/home/xavi/Pictures/Screenshot%20at%202011-11-01%2017:04:12.png[/IMG]

Sorry for the task bar, but is always there, never hide, but I will try solve it out

And after that is open cheese by his self and appears like this

[IMG]http://ubuntuforums.org/home/xavi/Pictures/Screenshot%20at%202011-11-01%2017:04:12.png[/IMG]

Thanks in advance for your help

---

### Post by xavi fernandez on 2011-11-01
sorry, this are the images I made mistake before :(
[Screenshot at 2011-11-01 17:04:12.png]("http://ubuntuforums.org/attachment.php?attachmentid=206026&stc=1&d=1320142523")
[Screenshot at 2011-11-01 17:09:08.png]("http://ubuntuforums.org/attachment.php?attachmentid=206027&stc=1&d=1320142523")

---

### Post by Paddy Landau on 2011-11-01
Yes; as I said, that command is only for use in 64-bit systems. But it shouldn't be necessary anyway for Cheese on Unity.

Did you follow the instructions in [post=11409602]post #2[/post]?

---

### Post by xavi fernandez on 2011-11-01
I just tried for second time and nothing, just come this on the terminal and after that open cheese with the black window, what I will do now is unplug the camera, restart ubuntu, open cheese and plug the camera later, sounds silly, but I don't know what to do. I can make work the camera with the vlc media player, so, the camera is working...

---

### Post by xavi fernandez on 2011-11-01
And this is what appeared when I try open from the terminal, I think is the same from the last post. any help will be appreciated.

---

### Post by xavi fernandez on 2011-11-03
In other post they told me that the program is installed in Dconf., so I need to delete the folders from there for install again and try, but some one knows how access to this folders? which command I must use for it???
I was looking for info in internet but was few and not clear at all for me.

Thanks all in advance.

---

### Post by xavi fernandez on 2011-11-07
I was reading from another users about cheese that is not working properly in ubuntu 11.10, so, maybe this is the problem. We hope will be fixed soon.
Thanks to all for your help and patience

---

### Post by Paddy Landau on 2011-11-07
> **xavi fernandez said:**
> In other post they told me that the program is installed in Dconf.
That does not make sense. dconf is the new replacement for gconf in storing *settings*, not installing programs.

I have Cheese on my system, and the settings are in gconf, not in dconf. However, if you install dconf-tools (if not already installed), you can run dconf-editor and explore.

> **xavi fernandez said:**
> I was reading from another users about cheese that is not working properly in ubuntu 11.10, so, maybe this is the problem.
Yes, maybe it is the problem. You can still check if a bug has been raised, and if not, raise a bug yourself. If the developers don't know about it, they won't fix it.

---

