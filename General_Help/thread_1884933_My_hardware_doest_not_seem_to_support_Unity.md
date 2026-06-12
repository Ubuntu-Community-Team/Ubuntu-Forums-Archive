---
title: "My hardware doest not seem to support Unity"
date: 2011-11-22
forum: General Help
---

### Post by asifnaz on 2011-11-22
My video card is

Intel (R) 82865g graphic controller 

can you figure out why My pc cant support Ubutnu with unity 

(and Fedore 15 with gnome 3 as well )

thank you

---

### Post by gandaran on 2011-11-22
run this test code from terminal on ubuntu
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by BC59 on 2011-11-22
You can use a Live CD.

If you can use the system through a CD or USB, without installing it, it's almost sure the OS will work installed as well.

---

### Post by asifnaz on 2011-11-22
Both of you didn't get my question . I have actully installed Ubuntu 11.04 on hard disk so when it boots up it tells my system is not sufficient to run Unity . Then it starts in classic mode (gnome 2)

I installed fedora 15 and it boots in failsafe mode (no launcher etc)

---

### Post by 2F4U on 2011-11-22
Unity and Gnome3 require a 3D capable graphics card, and your card cannot fulfil this requirement.

---

### Post by Mark Phelps on 2011-11-22
You could go to unity.ubuntu.com and check the minimum requirements for Unity. 

If you have an intel card, the minimum is the i945 and i965. Your intel chipset precedes those and is not sufficient.

---

### Post by haresear on 2011-11-22
> **Mark Phelps said:**
> You could go to unity.ubuntu.com and check the minimum requirements for Unity. 

If you have an intel card, the minimum is the i945 and i965. Your intel chipset precedes those and is not sufficient.

Does that mean i915 is considered not sufficient? I have both a laptop and a desktop with i915 graphics, and they seem to run unity 3D and gnome-shell fine.

---

### Post by bluexrider on 2011-11-22
Run the test program in terminal /usr/lib/nux/unity_support_test -p 

You should get an output like this:

$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R350
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

If you get a NO then it won't run.

Good luck

---

### Post by HermanAB on 2011-11-22
Howdy,

Use Xubuntu or Fedora with XFCE.  

You'll be in good company.  Even Linus uses Fedora with XFCE.

---

### Post by jocko on 2011-11-23
> **asifnaz said:**
> Both of you didn't get my question . 
Actually, gandaran did get your question. That's why he answered you with something that will actually **tell you why** you can't run unity:
> **gandaran said:**
> run this test code from terminal on ubuntu
```
/usr/lib/nux/unity_support_test -p
```

> **HermanAB said:**
> Howdy,

Use Xubuntu or Fedora with XFCE.  

You'll be in good company.  Even Linus uses Fedora with XFCE.
And that helps the op... how? Unity won't work... ...so use xfce instead?
If your car stereo doesn't work, is taking the bus really the most convenient solution?

---

### Post by asifnaz on 2011-11-23
> **HermanAB said:**
> Howdy,

Use Xubuntu or Fedora with XFCE.  

You'll be in good company.  Even Linus uses Fedora with XFCE.

In such case I will switch to Lubuntu or unity 2d

---

