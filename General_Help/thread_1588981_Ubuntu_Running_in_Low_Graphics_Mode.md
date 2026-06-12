---
title: "Ubuntu Running in Low Graphics Mode"
date: 2010-10-05
forum: General Help
---

### Post by [::AP::] on 2010-10-05
Greetings - 

I have been running Ubuntu 10.04 flawlessly for the past few months, and absolutely loving it. 

However, today I discovered an issue. Please excuse my... eh... noob-ish tendencies if they are prevalent. 

This morning, before heading off to school, I ran the update manager. I really didn't look at what was updating >.< It was just a normal updates. When it finished I shut down and went off to school. 

I expected to come home to a flawlessly working Ubuntu. However, when I booted into Ubuntu (but before logging in) I got a "Ubuntu is running in low graphics mode" window. I will take a picture exactly next time I boot up. 

Others have had this problem as I have observed on the forums. They tend to have screen resolution problems. 

My resolution is fine. Here are the issues:

Compiz does not work.
Visual effects don't work. 
Emerald Does not work.
Docky (it relies on Compiz) does not work. 

What can I do?

Here are some command that ***_DON'T_*** work...

```
sudo dpkg-reconfigure xserver-xorg
```

I can briefly see Docky pop up, then there is a random flash of multicolored boxes.

```
sudo dpkg-reconfigure xserver-xorg
```

Does nothing. 

Any ideas? 

Thanks...

Oh... The most important info...

Intel Graphics Chipset GMA950

If you need more info, please ask.

---

### Post by [::AP::] on 2010-10-05
Uh... All the sudden, Docky just started working...

No visual effects though. 

Compiz is on and some items are checked - looks like it reverted to the default. But no visual effects.

---

### Post by [::AP::] on 2010-10-06
Anyone? 

And Docky stopped working.

---

### Post by [::AP::] on 2010-10-18
An update fixed it. 

Its all good.

---

