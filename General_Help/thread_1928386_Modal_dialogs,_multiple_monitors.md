---
title: "Modal dialogs, multiple monitors"
date: 2012-02-20
forum: General Help
---

### Post by jdawg70 on 2012-02-20
[http://askubuntu.com/questions/80546/modal-popup-showing-on-the-wrong-monitor](http://askubuntu.com/questions/80546/modal-popup-showing-on-the-wrong-monitor)

is pretty much exactly what I've been experiencing, though I'm only rocking 2 monitors.  Applications on the left monitor will spawn their modal dialogs on the right monitor, hugging the left border, vertically centered relative to the Y resolution of the left monitor.  As much as I've learned to live with it, it still does drive me bonkers sometimes.

Is there a way around this?  I'd love it if modal dialogs would show up on the screen that my cursor was on.  CompizConfig settings with the Place Window plugin don't seem to have any effect.

Running Ubuntu 11.10 x86-64, HD3000 video.

Thanks!

---

### Post by fluteflute on 2012-03-13
I've reported this as a bug.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/954292](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/954292)

---

### Post by SushiAddiction on 2012-04-18
Can't believe the problems I've had with dual monitors since I did a fresh install of 11.10
A temp work around > all windows open in a fixed location. 
[http://askubuntu.com/questions/66069/how-to-prevent-launcher-from-influencing-window-placement](http://askubuntu.com/questions/66069/how-to-prevent-launcher-from-influencing-window-placement)

                  If you want all your windows to be initially placed in the top left corner, the follow settings in *ccsm > Place Windows* makes it work for me: in the *fixed window placement* tab, add an entry for *Windows with fixed positions* and set the type to any, x to -1, y to 48 and untick *keep in workarea*. It's quite a hack and the window is 1px off screen (which you'll hardly notice).

Because I have other problems with HIS RadeonHD6570, my settings are x 0, y 125.

With these settings it opens all windows on top left on left screen.
I mainly use first monitor, my second monitor is for video (plasma tv)  :wink:  

For noobs > ccsm is compiz config settings manager.

---

### Post by HiImTye on 2012-04-18
if you regularly use the same programs on specific monitors, it makes sense to use CCSM to redirect all windows from that app to that monitor

---

### Post by kapad on 2012-06-30
Is there any temporary workaround other than fixing a permanent monitor for frequently used apps. A plugin into compiz etc.

---

### Post by SushiAddiction on 2012-10-19
Still not fixed in 12.10. For those that have lived with this for more than a year read on.
I found a new solution besides the post above.
Switch to gnome for a year or two. Gnome is not so bad when you can use gnome extensions [https://extensions.gnome.org](https://extensions.gnome.org) (Dash to Dock,  Panel Settings)

It is more stable.

---

