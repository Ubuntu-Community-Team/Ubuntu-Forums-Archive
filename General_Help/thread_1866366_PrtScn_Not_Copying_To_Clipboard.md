---
title: "PrtScn Not Copying To Clipboard"
date: 2011-10-21
forum: General Help
---

### Post by jim_deadlock on 2011-10-21
I have a MS wireless keyboard, its works fine, but when I hit the PrtScn key I would like it to copy the desktop to clipboard, but it doesn't seem to do this, when I try to paste it into GIMP it reports the clipboard is empty. I've checked the keyboard bindings (see below) and it all seems in order. I've also tried it with F-Lock on and off, no joy. Any suggestions?

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/prtscn.gif[/IMG]

---

### Post by malsubhi on 2011-10-21
Hi 
I have same issue, all things well but I get nothing

[http://ubuntuforums.org/showthread.php?t=1866285](http://ubuntuforums.org/showthread.php?t=1866285)

I hope from expert friends to help us:lolflag:

---

### Post by jim_deadlock on 2011-10-21
Hmm maybe it's the upgrade that broke it, I'm on 11.10 (64) + Unity 3D. I think it used to work but not sure.

---

### Post by ajgreeny on 2011-10-21
Never bothered to try it before, but have just done so in 10.04 and it does not "Copy to clipboard" in that either.

I will do a launchpad bug search to see if it's known about.

---

### Post by crdlb on 2011-10-21
It's working fine in GNOME Shell. To be clear, the PrintScreen button is supposed to launch gnome-screenshot, whose dialog lets you save the file or copy it to the clipboard. In compiz, this appears to be handled by the Gnome Compatibility plugin.

---

### Post by jim_deadlock on 2011-10-21
I'm not running Gnome shell though, I have Unity 3D. I tried enabling Gnome Compatibility anyway just in case, but it broke my desktop so still no luck.

I've since put the (new?) screenshot tool on my launcher and it does the job but I would still prefer to just hit my PrtScn key for a quick clipboard copy.

---

### Post by ProntoAnthony on 2011-10-21
Try doing an Alt-PrtScreen instead of just PrtScreen.

Works for me on 11.10 Unity-2D.

---

### Post by jim_deadlock on 2011-10-21
Still nothing (tried shift and ctrl as well).

---

### Post by crdlb on 2011-10-21
According to /etc/compizconfig/unity.ini, the gnomecompat plugin is supposed to be loaded by default. So if something breaks when you enable it, there is a problem.

---

### Post by jim_deadlock on 2011-10-21
Now that's interesting because when I try to enable it there's a warning about conflicting plugins so maybe it's because of my cube or whatever. In any case, this gnomecompat plugin causes the PrtScn key to pop up a screenshot dialog right? If so that's still not what I really want. All I want is for nothing to happen, just a plain old desktop image on my clipboard, no fuss, no screenshot tools.

---

### Post by crdlb on 2011-10-21
You could change the screenshot command in that plugin's settings to: ```
gnome-screenshot --clipboard
``` Or just set up a key binding in the Commands plugin.

---

### Post by jim_deadlock on 2011-10-21
OK I've set up a command like you suggested and it works well enough apart from the silly screen blink and camera shutter noise, I think that's as close as I'm going to get so SOLVED, thanks.

---

### Post by malsubhi on 2011-10-22
Oh, Good news
Congratulation [U][jim_deadlock]("http://ubuntuforums.org/member.php?u=1108068")

[/U]Sorry, because I have same problem . How I can set up a command??

Also when I press Ctrl + Alt + T    I don't get a Terminal only nothing

Thank you

---

### Post by jim_deadlock on 2011-10-23
You have to open ccsm (install it if necessary), then go to the General section -> Commands -> enable the plugin, then on the first tab where it says Command line 0 put the following:

```
gnome-screenshot --clipboard
```

... then switch to the Key Bindings tab and click the button with a pencil on it (edit) and select the PrtScn key. When you've done that the button should say Print (instead of Disabled). Now when you hit your PrtScn key it blinks like a camera and copies your screen to clipboard, then you can paste it into GIMP or whatever.

You can probably work out how to set up your terminal in the same way although I haven't tried.

---

### Post by malsubhi on 2011-10-23
> **jim_deadlock said:**
> You have to open ccsm (install it if necessary), then go to the General section -> Commands -> enable the plugin, then on the first tab where it says Command line 0 put the following:

```
gnome-screenshot --clipboard
```... then switch to the Key Bindings tab and click the button with a pencil on it (edit) and select the PrtScn key. When you've done that the button should say Print (instead of Disabled). Now when you hit your PrtScn key it blinks like a camera and copies your screen to clipboard, then you can paste it into GIMP or whatever.

You can probably work out how to set up your terminal in the same way although I haven't tried.


:D:lolflag::lolflag::lolflag::lolflag::lolflag:

Thank you so much
It solve the problem and now I can take a screenshot

---

