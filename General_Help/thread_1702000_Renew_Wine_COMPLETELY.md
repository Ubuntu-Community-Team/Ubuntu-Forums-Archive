---
title: "Renew Wine COMPLETELY"
date: 2011-03-07
forum: General Help
---

### Post by Earl_Maroon on 2011-03-07
Wine used to work fine for me but a few days ago it started taking a long time to start (up to several minutes).

Several times now I have tried removing it completely in synaptic and following Winehq's own instructions (including deleting ~/.wine and other files) to remove it from my home directory before reinstalling various different versions (in case the binary was broken) but this did not work.

I thought that clearly something has been missed.

So I tried running Wine as root (I know I'm not supposed to) and it worked fine, so I now assume that there is something in my home directory that is causing this problem. But short of deleting every .file & .folder in ~ I don't know what to do.

***

So, does anyone know how to get rid of EVERY trace of Wine?
Or even better, do you have an idea what is wrong?

---

### Post by grahammechanical on 2011-03-07
You do not need to delete every dot file in your home folder. Just the one called .wine. You will lose all your wine installed programs and any data in them. Rename the file to .wineold and then reinstall wine. It will create a new .wine folder. I know. I have done this myself. Otherwise wine will continue to use the .wine folder that is already there.

Regards.

---

### Post by Earl_Maroon on 2011-03-07
I have deleted my .wine folder and the problem persists; that's the problem. There's something else in my home (I think) folder that's affecting Wine starting up.

---

### Post by Earl_Maroon on 2011-03-09
It seems that it's my .fonts folder that is causing the harm. I did

```
$ mv ~/.fonts /.fonts2
```

and now Wine starts in its normal timely fashion.

But this means I can't have my fonts and run Wine at the same time. I'll look into it more, but if anyone can give me any help that would be much appreciated.

---

