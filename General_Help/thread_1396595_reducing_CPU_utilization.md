---
title: "reducing CPU utilization"
date: 2010-02-02
forum: General Help
---

### Post by shariefbe on 2010-02-02
I am using Ubuntu Netbook remix which has ATOM processor, The Xorg CPU utilization is very high when i work on browser. I know this is because browser runs on X window. Now my question is How to reduce the CPU utiliazation of Xorg and browser. The CPU utilization is taken while running the browser is
In Atom processor :          Xorg    : 65-75 %
                             browser : 30-45%
 But in Core2duo processor : Xorg    : 8-15%
                             browser : 5-10%
   Now how to reduce Atom processor utilization should be reduced as core2duo processor. Please help me. Is it possible?

---

### Post by shariefbe on 2010-02-03
I think the problem is with plugins. If i remove all the plugins it is some what fast. But without plugin how can i work. any suggestion will be appreciated.

---

### Post by t4thfavor on 2010-02-03
Core2Duo is just a much better CPU, that said, it's probably based on the content f the sites you are on. I have ATOM N270 on my asus 900a, and my xorg never goes above 30% with firefox eating 35% Now put me on youtube, and it's another story with all the crap ads and flash. I dont think you will be able to reduce it much.

This is me with one tab on here, and one on youtube...
notice how ff thinks it can break the laws of physics...
```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2179 chance    20   0  384m  96m  30m S  114  9.7   5:35.80 firefox            
  951 root      20   0 37880  16m  10m R    7  1.7   2:29.17 Xorg               
 1500 chance    20   0  155m 4592 3480 R    4  0.5   0:03.34 pulseaudio         
 2153 chance    20   0 38144  13m 9992 S    2  1.3   0:03.31 gnome-terminal     
 1546 chance    20   0 28624  12m 9376 S    0  1.2   0:12.38 metacity           
 1496 chance    20   0  3240 1720  836 S    0  0.2   0:01.51 dbus-daemon

```
It changes to 95% if I turn off scaling.

---

### Post by shariefbe on 2010-02-03
yes ok . I am not using firefox here. I am using QtX11 browser. This is for my Project. firefox is quiet normal. Qt is very slow and taking more CPU utilization.

---

### Post by pkm4o93 on 2010-02-03
I use firefox addons 'adblock plus' and 'flashblock'. This greatly reduces my cpu usage.
I havent used UNRemix but perhaps also consider another graphical environment such as XFCE or LXDE.

---

### Post by shariefbe on 2010-02-03
Ok. how to change my GNOME to XFCE or LXDE?But i should not update or delete my gnome. I want to select like menu. So how to do that. How to install XFCE and LXDe in my ubuntu system?

---

### Post by NightwishFan on 2010-02-03
Top shows the result of all CPUS, so multicore apps I believe show up as 130%, etc. This happens if I render videos with multicore enabled.

On my machine, running flash gives me 50-80% cpu. I am running a AMD Athlon 64 x2 3800+ @ 2.0ghz, 64-bit OS. You could try to install the 64-bit flash from adobe, though you should uninstall the 32-bit one first.
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Also I do not think using a lighter DE will make much of a difference, but using a lighter browser might. Try Epiphany or perhaps Kazehakase.

---

### Post by shariefbe on 2010-02-03
No i have to work only in Qt browser. I dont want to change Browser. But i can change X server. I installed XFCE. But i am not getting any menu to select which desktop we want to use. it is directly going to XFCE. If i want to change to my old gdm desktop what should i do?

---

### Post by NightwishFan on 2010-02-03
I seriously think that using a different environment will make no difference. If you have a GDM login screen, then choose which session you want at the bottom of the screen.

---

### Post by shariefbe on 2010-02-03
so is there any option to make Qt browser ast in my atom processor?

---

### Post by NightwishFan on 2010-02-03
What exact browser are you using? With binary packages there is not much optimization you could do, however you can perhaps disable some features of the application you do not use. If smooth scrolling is enabled, then disable it.

---

### Post by shariefbe on 2010-02-03
just i compiled qtX11 and i am using only binaries. smoth scrolling means you are telling mouse scrolling?if yes how to disable that. Please help me

---

### Post by NightwishFan on 2010-02-03
I am really unsure how to help you there. Smooth scrolling as in non-jerky page scrolling.

---

