---
title: "cant use account after emerald"
date: 2009-09-12
forum: General Help
---

### Post by Richardarkless on 2009-09-12
Hey I installed emerald last night and tried it out, thing was it didnt work well for me so I removed it, thing was after I rebooted, I tried to login and now I get this error saying that my session only lasted 10 seconds, anyway I ticked to show the .xsessions-errors file and it comes up with a lot of writing.

I tried creating another account and that worked fine, so I know it has something to do with my account, I would remove it and start afresh but I have everything perfect and dont really want to customise everything again

---

### Post by NoaHall on 2009-09-12
Boot into your account -> Ctrl + Alt + F1 -> ```
metacity --replace
``` -> ctrl + alt + F7

---

### Post by Richardarkless on 2009-09-12
Hey I tried that and I get

windows manager error: unable to open x display

anyway here is my xsession error file

---

### Post by Richardarkless on 2009-09-13
sorry to double post but do you think I should just create a new account and start afresh, tempted to try other distributions as I have used ubuntu since 7.04

---

### Post by NoaHall on 2009-09-13
Hm. Do the same again, and run "sudo dpkg-reconfigure xserver-xorg" and then try.

---

### Post by Richardarkless on 2009-09-13
> **NoaHall said:**
> Hm. Do the same again, and run "sudo dpkg-reconfigure xserver-xorg" and then try.

just tried that and still it come up with window manager error:unable to open xdisplay

so I pressed control-alt and backspace and now I dont get any GUI, I can still use control alt and f1 to type commands though

had to boot into windows to write this :( , forgot how slow windows vista was

---

### Post by NoaHall on 2009-09-13
What graphics card do you have?

---

### Post by Richardarkless on 2009-09-13
> **NoaHall said:**
> What graphics card do you have?

nvidia geforce 7050

thanks to everyone for your help but I think I will reinstall and start afresh, might try kubuntu while im at it see what is up with the kde 4.3 hype

---

