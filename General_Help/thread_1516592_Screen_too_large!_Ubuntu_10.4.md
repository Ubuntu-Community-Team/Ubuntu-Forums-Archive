---
title: "Screen too large! Ubuntu 10.4"
date: 2010-06-23
forum: General Help
---

### Post by Taiga-kaka on 2010-06-23
Hey guys! Um... Well, I'm using Sony VAIO laptop and I set up the resolution to 2048x1536. And it seems that the screen is now too big to fit in my monitor. It's basically like the right and the bottom part is chopped off. I have uninstalled the NVIDA drive because it seems to make my laptop too zoomed in. So, help?

---

### Post by Revolutionary101 on 2010-06-23
Did you go to System>Preferences>Monitors to change the resolution?

---

### Post by Taiga-kaka on 2010-06-23
> **Revolutionary101 said:**
> Did you go to System>Preferences>Monitors to change the resolution?

Yes. I went there and tried them out. It seems that 2048x1536 (4:3) is the best option among them, because it's the one that makes the screen less choppy. But, like I said it puts things into cutting off the right and the bottom part of the screen. The other ones are too zoomed in.

---

### Post by Revolutionary101 on 2010-06-23
This link may help you:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

It tries to change your screen resolution via the Xorg config file.

---

### Post by Taiga-kaka on 2010-06-23
> **Revolutionary101 said:**
> This link may help you:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

It tries to change your screen resolution via the Xorg config file.


cp: cannot stat ' /etc/x11/xorg.conf': No such file or directory

That's what it says...

---

### Post by Revolutionary101 on 2010-06-24
Well I look in that directory to see if I had an Xorg.conf file but it turns out that I don't. The tutorial I gave you might be out of date. I am sorry but I don't have any other ideas on how you could fix your resolution problem.

---

### Post by tbohaning on 2010-06-24
What is the native resolution of your display? The Vaio's appear to have 1600x900 displays. Setting the resolution above the native resolution for the panel will cause the effect you are seeing....

---

### Post by Revolutionary101 on 2010-06-24
> **tbohaning said:**
> What is the native resolution of your display? The Vaio's appear to have 1600x900 displays. Setting the resolution above the native resolution for the panel will cause the effect you are seeing....

From what I understand, he isn't selecting the resolution of his screen. His computer automatically selects a screen resolution that is bigger than the native resolution of his display.

---

### Post by tbohaning on 2010-06-24
Ok. Thought that he set it based on the problem statement..."I set up the resolution to 2048x1536".

---

