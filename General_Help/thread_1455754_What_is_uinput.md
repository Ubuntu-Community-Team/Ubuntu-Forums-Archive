---
title: "What is uinput?"
date: 2010-04-16
forum: General Help
---

### Post by tonysonney on 2010-04-16
Hi Guys,
     I was going through some of the linux Android code. It is then I came accross uinput? They were trying to open something like

/dev/uniput. What is it? How does it work? I googled it. But can't find anything much helpful?

Thanks in Advance..
Cheers,
Tony

---

### Post by thomasaaron on 2010-04-16
I don't know a lot about it, but uinput apparently is a module upon which several other pieces of software are dependent. It probably stands for user input.

[http://www.math.bme.hu/~morap/RemoteInput/](http://www.math.bme.hu/~morap/RemoteInput/)

---

### Post by tonysonney on 2010-04-16
I found that uinput is used to inject the kernel with userdata, like keyboard press, which will inturn be passed to the user-space. But I could'nt find how it is passed to the user-space? and How it is read from there?

---

