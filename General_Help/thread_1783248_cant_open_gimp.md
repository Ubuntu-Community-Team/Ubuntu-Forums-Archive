---
title: "cant open gimp"
date: 2011-06-15
forum: General Help
---

### Post by gandaran on 2011-06-15
> (gimp:4216): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
segmentation fault

gimp stopped working on kubuntu after installing updates, any fix?

---

### Post by collisionystm on 2011-06-15
re install gimp?

---

### Post by gandaran on 2011-06-15
> **collisionystm said:**
> re install gimp?
nope, just finished installing the gimp update and still no work

---

### Post by gandaran on 2011-06-16
-------------up

---

### Post by HotForLinux on 2011-06-16
> -------------up

what, why, how?

---

### Post by crispy_420 on 2011-06-16
Try reinstalling the broken dependency: libglib

---

### Post by gandaran on 2011-06-17
got it fixed, problem was gimp couldn't create the user profile (I must have deleted the original one) so I copied the one from Ubuntu install to Kubuntu home/user and it works now, this must be some Kubuntu bug as it doesn't happen on Ubuntu.

---

### Post by crispy_420 on 2011-06-17
Its nice that error code told you that...

---

### Post by Nayar on 2011-06-18
> **gandaran said:**
> got it fixed, problem was gimp couldn't create the user profile (I must have deleted the original one) so I copied the one from Ubuntu install to Kubuntu home/user and it works now, this must be some Kubuntu bug as it doesn't happen on Ubuntu.
total n00b here.

Can you tell me in more detail please.

This problem is with kubuntu. GIMP worked with Ubuntu. I managed to open GIMP on kubuntu using sudo command thingy. But i don't want to use command prompt for opening an image editing software

---

### Post by Thras0 on 2011-06-22
> **Nayar said:**
> total n00b here.

Can you tell me in more detail please.

This problem is with kubuntu. GIMP worked with Ubuntu. I managed to open GIMP on kubuntu using sudo command thingy. But i don't want to use command prompt for opening an image editing software



Same problem here. Haven't found a solution yet, beside using sudo.

---

### Post by Nayar on 2011-06-22
> **Thras0 said:**
> Same problem here. Haven't found a solution yet, beside using sudo.
here you go: [http://ubuntuforums.org/showpost.php?p=10748644&postcount=2](http://ubuntuforums.org/showpost.php?p=10748644&postcount=2)

---

### Post by Thras0 on 2011-06-22
> **Nayar said:**
> here you go: [http://ubuntuforums.org/showpost.php?p=10748644&postcount=2](http://ubuntuforums.org/showpost.php?p=10748644&postcount=2)


Tnkx for the reply. I was browsing for a solution and i found the same answer here [http://www.techjail.net/solved-gimp-not-launching-on-kubuntu-11-04.htmlhttp://www.techjail.net/solved-gimp-not-launching-on-kubuntu-11-04.html]("http://www.techjail.net/solved-gimp-not-launching-on-kubuntu-11-04.htmlhttp://www.techjail.net/solved-gimp-not-launching-on-kubuntu-11-04.html")


just didn't have time to reply on the thread

---

### Post by eldergeek on 2011-08-17
I too found that post on techjail however, under appearance on my wife's system Rayleigh isn't one of the available choices nor does it appear in additional themes.  So am I doing something wrong or are we up the proverbial creek?

---

### Post by ksgeek on 2011-09-23
The simplest fix I found that works for me is:

mkdir ~/.gimp-2.6

It all works now

:p

---

