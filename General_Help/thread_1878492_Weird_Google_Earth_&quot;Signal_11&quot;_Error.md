---
title: "Weird Google Earth &quot;Signal 11&quot; Error"
date: 2011-11-09
forum: General Help
---

### Post by ATMSTopo28 on 2011-11-09
Hello all,

When I tried to install Google Earth, I got this "Google Earth has caught Signal 11" bug after the GE splash screen opens and the application crashes. I have looked throughout the internet for solutions and tried the most suggested one which was modifying the GoogleEarth.conf file somewhere in the ~/.googlearth directory. Though after doing this the error still happens. Does anybody have suggestions for a fix?

Thanks again,
Justin Reid

---

### Post by midden on 2012-02-01
I had this same issue today and found the answer [here]("http://ubuntuforums.org/showthread.php?t=1260492&highlight=google-earth+signal+11"), referencing [this fix]("http://www.webupd8.org/2010/10/fix-google-earth-crashing-on-startup-in.html"). It worked for me with 64-bit Xubuntu 11.10.

edit: Weirdly, this only worked once. Now I am having the same problem... I will have to keep digging.

---

### Post by midden on 2012-02-01
OK, so reading a bit more, I tried the following ([from the comments here]("http://www.webupd8.org/2010/10/fix-google-earth-crashing-on-startup-in.html")).

```
sudo apt-get install googleearth-package
make-googleearth-package --force
sudo dpkg -i ./googleearth_5.2.1.1547+0.6.0-1_amd64.deb
```

So far, it looks like it is working.

-midden

---

