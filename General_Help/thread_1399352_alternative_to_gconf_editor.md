---
title: "alternative to gconf editor?"
date: 2010-02-05
forum: General Help
---

### Post by rcayea on 2010-02-05
Hey everyone,

Is there an alternative to gconf-editor? I ask because I don't want to install all the dependencies that come with it. Or, do you know where I could go in the filesystem to edit there?

I am looking to find the path apps/nautilus/ and so on to tweak.

thanks,
Randy

---

### Post by agnes on 2010-02-05
Not really.

But, you can also tweak some stuff like gconf-editor does, using the program "Ubuntu Tweak".

gconf-editor can do more, albeit less user-friendly.

---

### Post by rcayea on 2010-02-05
Thanks for the feedback. I have Ubuntu-Tweak installed. A fantastic program indeed. :)

---

### Post by ajgreeny on 2010-02-05
> **rcayea said:**
> Hey everyone,

Is there an alternative to gconf-editor? I ask because I don't want to install all the dependencies that come with it. Or, do you know where I could go in the filesystem to edit there?

I am looking to find the path apps/nautilus/ and so on to tweak.

thanks,
Randy
If you mean you are looking for the files that contain the configurations set in gconf-editor, they are all xml files in the hidden ~/.gconf/apps/appname.

You could always try editing them manually, though I have no real idea about how you do that.

---

### Post by rcayea on 2010-02-05
Let me go have a look and see what I can do. If I am successful at all, I will post back. thanks,
Randy

---

### Post by dcstar on 2010-02-06
> **rcayea said:**
> Hey everyone,

Is there an alternative to gconf-editor? I ask because I don't want to install all the dependencies that come with it. Or, do you know where I could go in the filesystem to edit there?

I am looking to find the path apps/nautilus/ and so on to tweak.


```
man gconftool
```

~.gconf/apps/nautilus

---

### Post by rcayea on 2010-02-07
dcstar!

thank you, that did the trick!

---

