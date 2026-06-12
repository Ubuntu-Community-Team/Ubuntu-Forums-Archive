---
title: "Volumn Control &amp; Envelope not in Notification Area"
date: 2010-05-05
forum: General Help
---

### Post by held7over on 2010-05-05
Ubuntu 10.04 Gnome New Install, not upgrade.

The volume control Icon and the Envelope Icon are missing since the New Install of 10.04 in my Notification area.

Is there a way to add them back?

Thanks! ;)

---

### Post by blueridgedog on 2010-05-05
Right click the panel, click add to panel, then select "indicator applet"

---

### Post by held7over on 2010-05-06
Thanks blueridgedog!  I had looked at the applets, but didn't know what to look for. I was looking for volume control.

---

### Post by lidex on 2010-05-06
Yes...not very intuitive, is it?

---

### Post by blueridgedog on 2010-05-06
As an aside, it took me a long time to find the solution when it happened to me.  I had turned off the "envelope" in 9.10, so when I upgraded, I lost the applet, which caused me to lose the volume icon now.  Now, you can't get rid of the envelope without also getting rid of the volume icon.  I think it is a bit ill conceived, but will hope for the best.

---

### Post by John Bean on 2010-05-06
> **blueridgedog said:**
> Now, you can't get rid of the envelope without also getting rid of the volume icon.

```
sudo apt-get remove indicator-messages
```

---

### Post by held7over on 2010-05-06
I haven't figured out just how the volume control and the envelope are related at all! Ha Ha Ha

There are a whole lot of things in this version I really like, but removing the button that switches back and forth in Nautilus between text path and button path is not one of them. It was really handy, depending on what one was doing to be able to click between the two methods of navigating. I have a lot of new Ubuntu users who really don't need to have to commit to memory key functions in order to navigate. I just keep asking myself, why would they do that? Why would they make it more difficult? :p

---

