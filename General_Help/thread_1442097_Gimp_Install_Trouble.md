---
title: "Gimp Install Trouble"
date: 2010-03-29
forum: General Help
---

### Post by th1bill on 2010-03-29
This was a mistake and now I know it but I added the repository for Gimp 2.7.3 for Karmic and tried to upgrade using Synaptic.  Now I have about seventy photos I need to work on and Gimp will not run.  I went back to sources and removed the repository and then uninstalled Gimp.  Then Gimp 2.6.xx was there and I installed it but still no Gimp.  I did a restart and Repair Broken Packages but no help.  Can somebody help me out of my own manure?

I'm running a K8M800 BioStar MB with an AMD dual core and 2 gig of RAM.

Thanks in advance to anyone that can help.

---

### Post by linux4me on 2010-03-29
Have you tried starting Gimp from Terminal to see what error messages you get?

---

### Post by th1bill on 2010-03-29
Thanks, hadn't tried that.  The message and more below;

th1bill@th1bill-desktop:~$ gimp
gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory
th1bill@th1bill-desktop:~$ 

When I searched synaptic I found libgegl-0.0-0 but not the one in the error message.

---

### Post by n0dix on 2010-03-29
Do you install babl and gegl packages?

---

### Post by th1bill on 2010-03-29
> **n0dix said:**
> Do you install babl and gegl packages?

I did and still get the same error msg

---

### Post by n0dix on 2010-03-29
Try with:
```
sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean
```

---

### Post by th1bill on 2010-03-29
> **n0dix said:**
> Try with:
```
sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean
```

I don't are what those girls said about you... your a gentleman and a scholar and that command line is going in my notebook. 

Thank you many times.

---

### Post by n0dix on 2010-03-29
I supposed the problem is Solved so mark the thread please. ;)

---

