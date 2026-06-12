---
title: "Windows Ubuntu Communication"
date: 2009-12-08
forum: General Help
---

### Post by hawk007 on 2009-12-08
Hi, i have ubuntu installed on one machine and server 2003 on the other,
Using hosting controller (HC8) on both machines the windows cpanel shows the ubuntu server as DOWN.
 
HC8 relevent ports are open on windows machine and i can navigate to websites on windows machine.
 
I used "sudo ufw allow 8787 (etc) to open relevent ports on ubuntu machine.
 
Ubuntu machine registered with windows HC8 Cpanel but allways shows as down. I have eliinated all instructions given by HC as none made any difference. The ubuntu machine still shows as down.
 
From what i have read you cant disable ubuntu firewall wich closes the door to me finding out wether its the firewall causing the problem.
 
Could anyone please give me soe clues as to how to allow ALL so i can find out wether its a firewall problem or not.
 
Ubuntu installation i used encrypted method so dont know wether this could be the issue.
 
Any help appreciated thanks.

---

### Post by iMisspell on 2009-12-08
> **hawk007 said:**
> From what i have read you cant disable ubuntu firewall wich closes the door to me finding out wether its the firewall causing the problem.

```
man ufw
 - or -
ufw --help
```


```
ufw disable
```
Should work, no  ?



_

---

### Post by hawk007 on 2009-12-08
> **iMisspell said:**
> ```
man ufw
 - or -
ufw --help
```
 
TOO COMPLICATED
 
```
ufw disable
```
Should work, no ?
 
DISABLED IT Thanks but still dowsnt communicate with windows.
 
_DISABLED IT Thanks but still doesnt communicate with windows.
 
Could this be because when installing ubuntu i used/chose guided encrypted method

---

