---
title: "Two annoying problems"
date: 2011-08-10
forum: General Help
---

### Post by linuxman94 on 2011-08-10
I've been having these two problems for a little while now and they are getting to be annoying.

The first problem is that occasionally, a window will lock up and it seems to not refresh properly.  For instance, I'll be hitting the back button in firefox and sometimes it won't show the button highlighting and the window does not change.  If I maximize/restore the window, it refreshes properly.  I am using Compiz with wobbly windows enabled.

The second issue is in minecraft.  Whenever i launch it (using sun java, also occurs in openjdk), and click on an option, i get severe input lag.


Any ideas?

Edit: I'm using the catalyst 11.7 drivers installed from debs.

---

### Post by linuxman94 on 2011-08-11
Bump?

---

### Post by linuxman94 on 2011-08-12
Bump again.

---

### Post by pqwoerituytrueiwoq on 2011-08-12
install flashblock/noscript/adblock plus any one of those should help with that

---

### Post by linuxman94 on 2011-08-13
No, the freezing issue happens with other programs as well.

---

### Post by Frogs Hair on 2011-08-13
If you are using Unity , see the third item at the link .[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by linuxman94 on 2011-08-13
Nope, I've already turned off vertical sync system wide and through that setting.

---

### Post by linuxman94 on 2011-08-14
Bumping again.....

---

### Post by linuxman94 on 2011-08-16
Yet another bump.

---

### Post by mike555 on 2011-08-16
I have noticed some sites seem to not allow you to go back, but if you hold the left button down on the back arrow (in Firefox)for a few seconds it should show the websites you were on before, then just click one of them.

---

### Post by linuxman94 on 2011-08-16
> **mike555 said:**
> I have noticed some sites seem to not allow you to go back, but if you hold the left button down on the back arrow (in Firefox)for a few seconds it should show the websites you were on before, then just click one of them.

The problem isn't that i can't go back, the problem is that the entire interface stops responding to my input.  However, when the window looses focus, it starts responding again. The program does not freeze either.

---

### Post by dr1094 on 2011-08-16
Answer to your first problem:

I use to have similar porblems on my laptop. I think your problem occurs because you are running your system after the computer wakes up from either hibernation or suspend mode. If this is true, that you do often run your computer by bringing it out of suspend mode or hibernate mode, then there are two possible solutions. 

First, When you bring it out of suspend/hibernate mode, log out of the user name you are going to be using, and then log back in. please note: logging out, then suspending, and then running the computer does not seem to have the same effect for me. 

Second, you should try running the computer from boot.

If either of these does not solve your issue, then you can always use Alt+PrtSCrn+REISUB to restart your computer when frozen. Before you try this, you can try 'xkill'

---

### Post by linuxman94 on 2011-08-16
I don't ever use hibernate or suspend.  Furthermore, the system itself DOES NOT FREEZE, the currently active window just stops responding to input. Also, the program will respond to my input, it just won't show any response sometimes until i remove focus from the window then refocus it.

---

### Post by buddyd16 on 2011-08-17
have you tried disabling compiz? what you are describing sounds like an issue I was experiencing with xbmc which after some searching I found does not play nice with compiz.

note that unity requires compiz so you will have to select the classic session on the login screen or install unity-2d.

---

### Post by linuxman94 on 2011-08-17
It might be the wobbly windows plugin as i have that enabled.

---

