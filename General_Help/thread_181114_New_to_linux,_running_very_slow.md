---
title: "New to linux, running very slow"
date: 2006-05-23
forum: General Help
---

### Post by Ben512 on 2006-05-23
Hi i recently installed Ubuntu using an iso iamge on a DVD. The pc i installed it on has the following spec

Intel celeron 2.4
128mb ram
40gb hard drive
integrated intel extreme graphics

The installation went as i think it should and the graphics look corect but everything takes ages to load and is constantly reding the hard drive when anything is clicked
On the partitioner i set the virtual memory to 200mb
Why does this happen?

Any help would be appreciated

---

### Post by Perfect Storm on 2006-05-23
Because you have only 128mb ram. PCs with low ram should (well recommended at least) running a lightweighted WM (windows maker) like XFCE. Try Xubuntu.

---

### Post by oyvindaa on 2006-05-23
And in case he doesn't know how to do that:

```
sudo apt-get install xubuntu-desktop
```

Then log out, and when logging back in, choose XFCE from sessions.

:)

---

### Post by Ben512 on 2006-05-24
Hi, thanks for the replies however i cannot get online as it is so slow. Also whenever i do anything i noticed that my cpu usage goes striaght from bout 3% to 100% and stays there until it stops loading?:mad: 

Any help? 

The only positive i can find bout what ive got is the screensaver. It doesnt load at all and the grphics care quite good for a screensaver

---

### Post by skippy81 on 2006-05-24
Just buy more ram.  At the moment your lack of ram is seriously bottlenecking the processor. 

My flatmate has an e-machines PC of a similar spec to yours.  I reinstalled Windows XP on it, and with messenger and itunes running it is unusable.  128mb is simply not enough ram.  Ram is so cheap at the moment, it really is a waste to run your system without at least 512mb of it.  

I think you may have made a mistake with the size of your swap partition also.  200mb is far too small, what was the recommended size chosen by the partitioner?  I know swap should be 1.5-2x physical ram, but when you have less than 1gb RAM you really need a bigger swap file.    

As for installing XFE...

You don't actually need to wait for your graphical interface to respond in order to install xubuntu desktop.  If you press Control-Alt and F1 - F6 you can open text consoles.  Log in through one of those and run the command suggeested by the above poster.

The 100% CPU use thing is normal.  Your only problem appears to be that you don't have enough memory space (RAM and swap) to fit the environment into.

---

### Post by oyvindaa on 2006-05-24
You could also install Ubuntu as a server (no gnome), then install xubuntu-desktop from terminal. There is a how-to for that on here somewhere. Search for it :)

I don't know whether it'll help much though, unless you buy more RAM.

---

### Post by nami on 2006-05-24
Get more RAM.  I have a slower processor than you, but my ubuntu flys as I have 2Gb or RAM!

---

