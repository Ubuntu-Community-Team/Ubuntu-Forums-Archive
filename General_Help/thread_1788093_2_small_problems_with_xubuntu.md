---
title: "2 small problems with xubuntu"
date: 2011-06-22
forum: General Help
---

### Post by ade234uk on 2011-06-22
Installed xubuntu but am experiencing two problems

1) When I open a new application the windows pins itself to the top left  of the screen. I cannot move it, maximise it or minimise it.

2) For some reason I cannot find the applet to show my wireless networks either, therefore I cannot connect to the internet.

If you could help me with these problems it would be much appreciated.

---

### Post by Bucky Ball on 2011-06-22
Which release are you using? (PS: you mean'[B]2 small problems with Xubuntu')

;)
[/B]

---

### Post by Perfect Storm on 2011-06-22
> **Bucky Ball said:**
> Which release are you using? (PS: you mean'[B]2 small problems with Xubuntu')

;)
[/B]

fixed.

---

### Post by wildmanne39 on 2011-06-22
> **ade234uk said:**
> Installed xubuntu but am experiencing two problems

1) When I open a new application the windows pins itself to the top left  of the screen. I cannot move it, maximise it or minimise it.

2) For some reason I cannot find the applet to show my wireless networks either, therefore I cannot connect to the internet.

If you could help me with these problems it would be much appreciated.
Hi, if you are using 11.04 install compizconfig settings manager and click on move windows in the settings manager and set windows to move.

---

### Post by Bucky Ball on 2011-06-22
> **wildmanne39 said:**
> Hi, if you are using 11.04 install compizconfig settings manager and click on move windows in the settings manager and set windows to move.

Not sure why you would need to install compiz simply to move a window. This would be a dirty fix (if it worked) to the underlying problem, whatever that might be. (Installing compiz also kinda defeats the purpose of using a more lightweight DE). I love Xubuntu, have used it for yonks, and have *never* used compiz. 

I have never had this issue, either, though. ;)

---

### Post by wildmanne39 on 2011-06-22
> **Bucky Ball said:**
> Not sure why you would need to install compiz simply to move a window. This would be a dirty fix (if it worked) to the underlying problem, whatever that might be. (Installing compiz also kinda defeats the purpose of using a more lightweight DE). I love Xubuntu, have used it for yonks, and have *never* used compiz. 

I have never had this issue, either, though. ;)Hi, not if he is running in classic mode with effects when you use it like I tried I could not move the windows from the top left without enabling move windows in ccsm because it was disabled in classic by default and when I helped out in the desktop forum I have seen that same issue many times,and all solved by doing what I mentioned, however I know he is using xubuntu so it might not apply but it sure sounds like the same issue.

---

### Post by ade234uk on 2011-06-22
Sorry I am using version 11.04

---

### Post by ade234uk on 2011-06-22
> **Bucky Ball said:**
> Not sure why you would need to install compiz simply to move a window. This would be a dirty fix (if it worked) to the underlying problem, whatever that might be. (Installing compiz also kinda defeats the purpose of using a more lightweight DE). I love Xubuntu, have used it for yonks, and have *never* used compiz. 

I have never had this issue, either, though. ;)

Can you also tell me how I can display the wifi manager on the taskbar which will allow me to connect to the wireless network.

For your information, I basically installed xubuntu from Kubuntu. xubuntu looks very good, its simple does the job. This might be one of the reasons wh

---

### Post by Bucky Ball on 2011-06-22
Xubuntu 11.04 (or any other version) does *not* use Unity, nor does Kubuntu so probably a dead end there.

To the OP, you may want to uninstall Kubuntu by simply going to Synaptic Package Manager and selecting 'kubuntu-desktop' and removing it. That will stop any possible conflicts between the two.

As for getting the network icon in the taskbar, not at my Xfce box at the mo. You might want to go to Synaptic and install xfce4 to make sure you have everything installed for that desktop environment. There is also a package called Xubuntu-goodies (from memory) but not sure if that is the one that includes the network manager.

What works for a lot of people, and probably the best bet, is installing wicd. That should supply you with a network icon. You will also find that in Synaptics and works fine with xfce environment. ;)

(PS: I have Ubuntu installed, then xfce4, therefore I am using Network Manager which only works with Gnome. In my case, I have all the Gnome dependencies installed which allows me to use Network Manager. There is an option somewhere to enable Gnome (or KDE) dependencies somewhere in the Xubuntu menu. You might want to research that if wicd doesn't work for you.)

---

### Post by Bucky Ball on 2011-06-22
Ah, there it is! In Settings>Session and Startup>General you will find 'Launch Gnome services on startup?'. That may work if wicd is no good and you want to use Network Manager. ;)

---

### Post by ade234uk on 2011-06-22
> **Bucky Ball said:**
> Ah, there it is! In Settings>Session and Startup>General you will find 'Launch Gnome services on startup?'. That may work if wicd is no good and you want to use Network Manager. ;)

Thank you very much for your help. I will take a look at this.

---

### Post by Bucky Ball on 2011-06-22
No probs, but try wicd first. You can always uninstall if you don't like and that way you can leave out the Gnome stuff which keeps it a little more lightweight.

---

