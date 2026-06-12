---
title: "Cannot change keyboard layout in login screen"
date: 2012-05-17
forum: General Help
---

### Post by mattiv on 2012-05-17
Hi, 

After a reboot I suddenly ran into a following kind of problem: 

In the login screen, keyboard layout is Russian by default, and the menu giving the layout options lists Russian as the only alternative. Because of this, there is no way for me to login with the ubuntu login prompt, since my password consists of latin characters.

Since I can access the GUI only as a guest user, I'm clueless as to how to fix this. Could someone please point me in the right direction? I'm using Ubuntu 12.04.

---

### Post by loklaan on 2012-05-17
Hi!

You can set your keyboard defaults and alternatives with setxkbmap:
```
setxkbmap us, ru
```
This sets your default keyboard layout to US, so at login you should be able to use those latin characters. It also sets Russian layout as an alternative; I think you can switch to this with the keyboard shortcut Alt+Alt (I am not sure on the shortcut..)

---

### Post by loklaan on 2012-05-17
You can access console at login by pressing ctrl+alt+f1 and to get back press ctrl+alt+f7.

---

### Post by mattiv on 2012-05-17
> **BuNsiE said:**
> Hi!

You can set your keyboard defaults and alternatives with setxkbmap:
```
setxkbmap us, ru
```

When I try to do this, it says 
```
Cannot open display "default display"
```
and the problem persists. 

Btw, the problem appeared while installing a second monitor, could this have messed up the X server?

---

### Post by biberce on 2012-11-28
I have similar problem. After instaling ubuntu 12.10 from windows it places SR (Serbian Cyrilic) keyboard in loginscreen, so now I can not login because before instalation I've input my pass in latin characters. 

And when I try to change dafault kayboard layout from console, even in console it tipes cyrilic, and even worst it asks me for a password first. 

It is frustrateing, and I can not find answer on this problem on other sites and forums. 

And now what? Back to windows?

---

### Post by biberce on 2012-11-28
> **biberce said:**
> I have similar problem. After instaling ubuntu 12.10 from windows it places SR (Serbian Cyrilic) keyboard in loginscreen, so now I can not login because before instalation I've input my pass in latin characters. 

And when I try to change dafault kayboard layout from console, even in console it tipes cyrilic, and even worst it asks me for a password first. 

It is frustrateing, and I can not find answer on this problem on other sites and forums. 

And now what? Back to windows?

Found a solution. Logd on as a guest, add english keyboard first. After went to Settings, then to Users, clicked on Admin account, clicked Locked button, tiped admin password, and in at the end under the password change put PASSWORD NONE.

---

### Post by mattiv on 2012-11-28
I eventually ended up reinstalling the whole OS. I probably could have edited the X.org keyboard configuration files by hand in something like /etc/X11/Xorg.conf.d/xx-keyboard.conf, had I known what I know now.

---

