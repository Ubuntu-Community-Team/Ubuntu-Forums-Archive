---
title: "Adding program to startup"
date: 2012-02-04
forum: General Help
---

### Post by Sachin_ruk on 2012-02-04
Hi all,

I want to add my sticky notes application, xpad to startup so that I dont need to manually go about opening it up everytime.

How would I do this.

Thanks,
Sachin

---

### Post by lechien73 on 2012-02-04
If you're using Ubuntu 11.10, then click on the power & settings button (the cog icon in the top right corner), choose **Startup Applications**

If you're using 10.04, then go to **System –> Preferences –> Startup Applications**

Then click **Add**. For the *Command* simply type **xpad**. Click the **Add** button, and then it's done.

When you restart your computer, xpad should start up automatically.

---

### Post by chickenPie4breakfast on 2012-03-04
What are the switches for this?   like %F
I want to add a program but dont want it to expand onto the desktop but instead remain in the background untill I call it  is there a minimize switch or something?

---

### Post by MG&amp;TL on 2012-03-04
> **chickenPie4breakfast said:**
> What are the switches for this?   like %F
I want to add a program but dont want it to expand onto the desktop but instead remain in the background untill I call it  is there a minimize switch or something?


Should really be a separate thread, but...

That's program-dependent. You can see if a program has such an option with:

```
man <program name>
```


For example empathy has --hidden, which minimises it by default.

---

