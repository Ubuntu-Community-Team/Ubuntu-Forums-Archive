---
title: "natty: no fonts in emacs over ssh"
date: 2011-06-21
forum: General Help
---

### Post by gghigliotti on 2011-06-21
Hi all,

I successfully installed Natty on my PC and everything works great. Or nearly!
If I connect to a server via ssh and try to open an emacs window on the server: no fonts are visualized (only empty boxes) and I get the following warnings:

Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

- running emacs with the "no window" option -nw works fine (but I don't like working with emacs in the terminal window).
- emacs works fine on the server, when accessed from other machines (my old PC, my laptop, etc...).
- emacs installed on my own machine (the one with Natty) works fine, if that matters.

any ideas? thanks!
    giovanni

---

### Post by cenit on 2011-06-29
> **gghigliotti said:**
> Hi all,

I successfully installed Natty on my PC and everything works great. Or nearly!
If I connect to a server via ssh and try to open an emacs window on the server: no fonts are visualized (only empty boxes) and I get the following warnings:

Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

- running emacs with the "no window" option -nw works fine (but I don't like working with emacs in the terminal window).
- emacs works fine on the server, when accessed from other machines (my old PC, my laptop, etc...).
- emacs installed on my own machine (the one with Natty) works fine, if that matters.

any ideas? thanks!
    giovanni

I had the same problem.
I installed many many fonts on my ubuntu (so I don't know exactly how to tell which one you should. Maybe "ttf-mscorefonts-installer" "xfonts-100dpi" and "xfonts-75dpi" are enough.
But, even with so many fonts installed, the problem persisted.
The solution was to edit the local /etc/X11/xorg.conf and adding this:
```

Section "Files"
  FontPath "/usr/share/X11/fonts/local/"
  FontPath "/usr/share/X11/fonts/misc/"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1/"
  FontPath "/usr/share/X11/fonts/Speedo/"
  FontPath "/usr/share/X11/fonts/75dpi/"
  FontPath "/usr/share/X11/fonts/100dpi/"
EndSection

```

---

### Post by gghigliotti on 2011-07-05
Hi Cenit,
thanks for the reply.
Unfortunately in Ubuntu 11.04 there is no /etc/X11/xorg.conf file, and creating it with the text you suggest does not solve the problem.
Any ideas?

thanks!
   giovanni

---

### Post by ReverseEngineered on 2011-07-18
I just ran into this problem too. Ubuntu doesn't seem to be adding the new fonts to the font path when you install the xfonts-75dpi and xfonts-100dpi packages. You can add them manually like this:
```

xset +fp /usr/share/fonts/X11/75dpi:unscaled
xset +fp /usr/share/fonts/X11/100dpi:unscaled
xset fp+ /usr/share/fonts/X11/75dpi
xset fp+ /usr/share/fonts/X11/100dpi
xset fp rehash

```

This adds the font directories to X11's font path. The first two lines add the fonts before all the existing ones in the search order (so they will get picked first), but only if they match the font size you asked for. If it doesn't match those, it will try its existing fonts (which are all scalable fonts and should draw nicely). Finally, we add the fonts to the end of the search path, but without the "unscaled" option, which says it can resize them if needed. They will look ugly, but at least it will be the correct font.

Finally, the "rehash" tells it to reload its list of fonts by searching through that path.

---

### Post by edith11 on 2011-08-04
Thank you so much, cenit - I had the same issue, and this worked beautifully for me.

---

### Post by ssjsonic1 on 2011-11-01
Confirmed success.  After installing the three packages and manually adding them with xset, emacs fonts show up through ssh while on my Ubuntu 11.10 laptop.  Great job team!

---

### Post by stillnotelf on 2011-11-14
I can confirm that ReverseEngineered's solution works in 11.10.

---

### Post by bbukh on 2011-11-21
> **ReverseEngineered said:**
> I just ran into this problem too
[...] You can add them manually like this [...]


Works wonderfully! I had the same problem in oneiric, and this has helped. Many thanks.

---

### Post by has64 on 2012-03-26
Great, thanks! The only addition thing is I have to install xfonts-75dpi and xfonts-100dpi before running your commands. 
But the the emacs displays different color in the server from  my laptop. Is this normal? Thanks

---

### Post by seventeener on 2012-04-09
Thanks cenit. I installed xfonts-75dpi and xfonts-100dpi, then rebooted. No need to add extra paths in xorg.conf or using xset. The original emacs warning disappeared after a reboot. Xubuntu 11.10.

---

### Post by jamaas on 2012-04-26
Worked for me too .... Thanks

J

---

### Post by lngndvs on 2012-04-28
I am using 2012.04, installed from Beta and upgraded.  I ran into a peripheral issue involving emacs dired-image, and a program from ImageMagick (which has been diverted to a different program in Precise Pangolin, at least), leading eventually to the following message:

 display: Unable to load font (-*-helvetica-medium-r-normal--12-*-*-*-*-*-iso8859-1) [Resource temporarily unavailable].


I found that xfonts 75pdi and 100dpi are not installed by default.  So I will find out whether this was the issue.

---

