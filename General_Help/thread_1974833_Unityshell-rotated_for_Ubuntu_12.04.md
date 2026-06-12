---
title: "Unityshell-rotated for Ubuntu 12.04?"
date: 2012-05-06
forum: General Help
---

### Post by asuastrophysics on 2012-05-06
Hey guys,

In Ubuntu 11.10, I enjoyed using a really cool plugin called unityshell-rotated, which can be found here:
[https://launchpad.net/~paullo612/+archive/unityshell-rotated](https://launchpad.net/~paullo612/+archive/unityshell-rotated)

However, it appears as though the binary version of this plugin will not work with Ubuntu 12.04, as the plugin is compiled and built on top of Unity 4. The version of Unity included in Ubuntu 12.04 is 5.10.0

Is it possible to compile the unityshell-rotated plugin against this newer version of Unity? Does compiling work in such a way? Can I compile any program I want against newer versions of its dependencies? 

Thanks a bunch!

Jake

---

### Post by Charlietje on 2012-05-07
I'm waiting for it too.
It's too bad you can't do it by default...

---

### Post by asuastrophysics on 2012-05-07
Can you compile a package against newer versions of its dependencies though? I know it's a weird question to ask, but I'd rather ask now instead of doing it myself and breaking Unity. 


If this is possible to do, then I will compile it, and put it into a *.deb format so that everyone can use it!

---

### Post by Rockiholic on 2012-05-08
> **asuastrophysics said:**
> Can you compile a package against newer versions of its dependencies though? I know it's a weird question to ask, but I'd rather ask now instead of doing it myself and breaking Unity. 


If this is possible to do, then I will compile it, and put it into a *.deb format so that everyone can use it!

I would love you forever if you did that...I was very sad after I realized unity-rotated was supported in 12.04:frown:

---

### Post by asuastrophysics on 2012-05-09
> **Rockiholic said:**
> I would love you forever if you did that...I was very sad after I realized unity-rotated was supported in 12.04:frown:

I'm in the process of attempting to port the package over right now, but I'm tied up in college exams at the moment. There goes my free time for a few days :lolflag:

FACT: You can compile any program you want against newer versions of its dependencies, provided that the function definitions of the package have not changed. 

I started compiling it, but I ran into dependency problems. I probably will eventually be able to compile the program, but compiling and porting are two very different things. I might consult some more experienced linux users for help with this.

---

### Post by max100881 on 2012-05-11
Hi all 
Would be very helpfull for netbook !!!
I post to keep posted :p

---

### Post by zaiger on 2012-05-11
Signed.

This was the first thing I noticed after I upgraded. It hadn't even occurred to be that the Unity-rotated plugin would be a regression. Very annoying, especially when you are using Tree-view tabs with Firefox, the left side of the screen is very cluttered. I wish I had made a snapshot to back up to until this was recompiled to work with 12.04.

Thanks guys, Ubuntu community rules! \\:D/

:mrgreen:

---

### Post by zaiger on 2012-05-16
> **asuastrophysics said:**
> I'm in the process of attempting to port the package over right now, but I'm tied up in college exams at the moment. There goes my free time for a few days :lolflag:

FACT: You can compile any program you want against newer versions of its dependencies, provided that the function definitions of the package have not changed. 

I started compiling it, but I ran into dependency problems. I probably will eventually be able to compile the program, but compiling and porting are two very different things. I might consult some more experienced linux users for help with this.
Having any luck?

---

### Post by Rockiholic on 2012-05-30
Has anybody found a workaround for this yet?

---

### Post by asuastrophysics on 2012-05-31
> **Rockiholic said:**
> Has anybody found a workaround for this yet?

I tried to compile unity-shell rotated from source, but it definitely does NOT work. You must comment out distchecks (checks for the proper distribution). Then, if you try and "make" the final version of unity with the included unityshell-rotated plugin, the make will fail and unity completely breaks. It took me 2 hours just to get my desktop to work again. 

I must not know what I am doing, but there has got to be a way to "sandbox" compiled versions of programs, so that they do not adversely affect the rest of the system if something goes wrong. Surely there is a way to keep ubuntu from using my compiled version of unity, unless I specify otherwise...

---

### Post by WizardofOS on 2012-06-04
i tried to install the oneiric version of the missing packages and the rotated version of unity found here [https://launchpad.net/~paullo612/+archive/unityshell-rotated/+build/2955686](https://launchpad.net/~paullo612/+archive/unityshell-rotated/+build/2955686)

it didn't work....
gdebi told me it would break unity completely....

---

### Post by asuastrophysics on 2012-06-23
> **WizardofOS said:**
> i tried to install the oneiric version of the missing packages and the rotated version of unity found here [https://launchpad.net/~paullo612/+archive/unityshell-rotated/+build/2955686](https://launchpad.net/~paullo612/+archive/unityshell-rotated/+build/2955686)

it didn't work....
gdebi told me it would break unity completely....

Confirmed. It WILL break unity completely if you succeed in installing it. In order to make it compile from source, you must delete the DISTCHECKS in the make file (I'm guessing that just checks to verify that you're running 11.10). Once you disable distchecks, it will compile, but it will also break unity.

---

### Post by mdye on 2012-06-27
I have nothing against unity in its current incarnation, but I find that the placement on the left is a little awkward. It seemed fine when the Dash Home button was integrated into the panel on top, but since they decided that didn't work, it feels like maximized windows are broken up, unless you set the launcher to autohide. I just wish there was an option - even a hidden one - to put it where you like, pretty much like most other DE's.

Does anyone know if there will ever be any movement on this fork?  Doesn't look like any work has been done on it since late last year. :-(

---

### Post by oshirowanen on 2012-12-15
I think Unity as a whole has had a bad impact on Ubuntu based on distrowatch.  Ubuntu was number 1, but now it's number 3 on distrowatch.

I've been forcing myself to use Ubuntu 12.04 with default Unity since day 1, and although I am getting used to it's faults, I still don't like the left menu and all the extra clicks you keep having to do...

I guess I am not the only one, as clearly Ubuntu would't move from number 1 to number 3 on distrowatch if it was just me...

---

