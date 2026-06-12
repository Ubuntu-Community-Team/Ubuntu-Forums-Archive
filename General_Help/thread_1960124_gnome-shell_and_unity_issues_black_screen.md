---
title: "gnome-shell and unity issues black screen"
date: 2012-04-16
forum: General Help
---

### Post by Yayestechlab on 2012-04-16
Whenever I launch Gnome Shell (non-fallback), Unity, or Unity 2D, I get my desktop background, then after a few seconds it goes to a black screen. Also, the lock bar at the top of the screen is there.The computer is totally unusable from this state. Photos are attached. This has been happening for some time now. How can I fix this?

---

### Post by bogan on 2012-04-17
Hi!, **Yayestechlab**,
Please clarify: Does "launch" mean you get the grub menu and select 11.04 from there ?

Do you get a GUI login screen and window, and you login, before the desktop background shows ?

Your screen-shot does not show clearly if the top bar is complete, are any of the Icons responsive to Mouse clicks?  Or the desktop to a Right-Click ?

Have you tried pressing 'CTRL+ALT+F1' or F2 ? do they give a login prompt ?

What video card do you have? Please Post:```
 lspci -nnk | grep VGA
```Chao!,** bogan**.

---

### Post by Yayestechlab on 2012-04-17
> **bogan said:**
> Hi!, **Yayestechlab**,
Please clarify: Does "launch" mean you get the grub menu and select 11.04 from there ?
First of all I use 11.10 not 11.04. My profile says 11.04 because the 50 post limit was added before I changed to 11.10. To answer your question, no, I don't mean that I choose 11.10 from the GRUB menu by launch. What I mean by launch is clicking on the settings wheel in LightDM and choosing the DE from the menu.  

> **bogan said:**
> Do you get a GUI login screen and window, and you login, before the desktop background shows  ?
Yes, I do get a graphical login screen.

> **bogan said:**
> 
Your screen-shot does not show clearly if the top bar is complete, are any of the Icons responsive to Mouse clicks?  Or the desktop to a Right-Click ?
The top bar is complete, it was an accident and like I said in the original post the computer is unresponsive except to a power button induced shutdown or a mouse move (not a mouse click).   

> **bogan said:**
> Have you tried pressing 'CTRL+ALT+F1' or F2 ? do they give a login prompt 
They work properly, in fact tty1-tty6 work properly. 

> **bogan said:**
> What video card do you have? Please Post:```
 lspci -nnk | grep VGA
```
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]

```

---

### Post by bogan on 2012-04-17
Hi!, **Yayestechlab**,
You Posted:> [QUOTE]Originally Posted by **bogan**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11850682#post11850682")                 
                 *Have you tried pressing 'CTRL+ALT+F1' or F2 ? do they give a login prompt?*
They work properly, in fact tty1-tty6 work properly. [/QUOTE] How about:'CTRL+ALT+F7'? Does that give you a blank screen with the topbar ? or text showing a hang up?
Ditto if you login on a  tty -'CTRL+ALT+F1'or F2 and run: ```
sudo service lightdm start
``` Does that show lightdm already running? or a blank screen?

```
01:00.0 VGA compatible controller [0300]: [COLOR=Red]ATI Technologies Inc M22
 [Mobility Radeon X300] [1002:5460][/COLOR]
```The symptoms look to me like video driver problems, but my knowledge of ATI drivers is limited to the fact that they seem, from the forums, to give even more problems than Nvidia drivers; as some ATI cards need one driver and others will refuse to work with it and need another.

Chao!, **bogan.**

---

