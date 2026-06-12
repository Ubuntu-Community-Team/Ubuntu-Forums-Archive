---
title: "Adding patch to wine: &quot;Hunk #1 FAILED at 94"
date: 2010-07-07
forum: General Help
---

### Post by Drumber on 2010-07-07
So I'm trying to get Worms Armageddon working on linux via wine and following the instructions [here.]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1744") Downloaded source of Wine 1.1.39 from sourceforge, and using [this]("http://hifi.iki.fi/worms_armageddon-wine-1.1.39.patch") patch. I try to patch by running this command:

```
patch -p0 < ../worms.patch
```But I get this error in return:

```
patching file b/dlls/wined3d/swapchain_gdi.c
Hunk #1 FAILED at 94.
1 out of 1 hunk FAILED -- saving rejects to file b/dlls/wined3d/swapchain_gdi.c.rej
patching file b/server/window.c
Hunk #1 FAILED at 2310.
1 out of 1 hunk FAILED -- saving rejects to file b/server/window.c.rej

```I'm not to familiar with this patching and compiling from source business. Can anyone help?

---

### Post by Drumber on 2010-07-07
...bump

---

### Post by mc4man on 2010-07-07
I'd start with a fresh extracted source, then place your patch file inside and cd to the extracted source in terminal.
use - 
```
 patch -p1 < ./worms.patch
```

As Ex.
> doug@doug-desktop1:~/Downloads/test4/wine-1.1.39$ patch -p1 < ./worms.patch
patching file dlls/wined3d/swapchain_gdi.c
patching file dlls/winex11.drv/desktop.c
doug@doug-desktop1:~/Downloads/test4/wine-1.1.39$

---

### Post by priya9 on 2011-02-11
oot@ubuntu:/home/narayan/Downloads/click-1.8.0/etc# patch -p1 < ns-2.34-patchpatching file Makefile.in
Hunk #1 FAILED at 59.
Hunk #2 FAILED at 163.
Hunk #3 FAILED at 175.
Hunk #4 FAILED at 215.
Hunk #5 FAILED at 243.
Hunk #6 FAILED at 319.
Hunk #7 FAILED at 512.
7 out of 7 hunks FAILED -- saving rejects to file Makefile.in.rej
patching file apps/udp.cc
Hunk #1 FAILED at 104.
Hunk #2 FAILED at 119.
2 out of 2 hunks FAILED -- saving rejects to file apps/udp.cc.rej
The next patch would create the file classifier/classifier-click.cc,
which already exists!  Assume -R? [n] 

why is it happening ?plz help me out?

---

### Post by 3246251196 on 2011-03-14
I would appreciate if someone could answer this question because I am having a similar issue with a patch that is a MUST for me.

I keep on getting these Hunk FAILED errors.

What is this? Why is it happening? What to do to solve this?

---

### Post by 3246251196 on 2011-03-15
Anyone?

It is not even as if I am doing a lack of research. I have tried to look this issue up.

What are these errors and what to do?

---

### Post by LowSky on 2011-03-15
**3246251196** What are you trying to patch? and what instructions are you trying to use?
Have you tried using a more up to date version of wine

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install wine

Have you tried using PlayOnLinux.. it helps install games so the user doens't have to worry about dependencies.

---

### Post by 3246251196 on 2011-03-18
> **LowSky said:**
> **3246251196** What are you trying to patch? and what instructions are you trying to use?
Have you tried using a more up to date version of wine

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install wine

Have you tried using PlayOnLinux.. it helps install games so the user doens't have to worry about dependencies.

It was a mistake on my part. My problem was simply that I hadn't installed the WINE source code. How could I expect to patch the source code without having it.

I didn't realise exactly what I was doing until further reading.

Basically, installed SC, unpacked, patched, compiled and ran. Problem solved.

Thanks.

---

