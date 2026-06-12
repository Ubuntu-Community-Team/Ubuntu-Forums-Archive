---
title: "Safaricom 3g modem"
date: 2011-02-13
forum: General Help
---

### Post by L Style on 2011-02-13
I'm using ubuntu 10.04. I have a safaricom 3g modem but it's not work with ubuntu. I try using huawei E220 it's work fine. How can I work this safaricom modem. please help me

---

### Post by L Style on 2011-02-14
bump......... Please help me................

---

### Post by andrewcd on 2011-06-06
Bump with the same problem.  I am using Ubuntu 10.04, and have a SarariCom MobilePartner 3g modem -- its a usb stick that plugs into the computer.  It has autorun for windows, but the .exe file doesn't work with WINE.

Inside the stick there is a "Linux" directory, with the following readme file:

> --How to Install---------------------- 
*You need login as root* 
1. Run "install" in TERMINAL to install MobilePartner 
   eg: # bash /<path>/install 
    
2. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit. 
 
3. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct 
 
4. Finish installing 
 
--How to run-------------------------- 
* From shortcut in desktop 
 
* Run MobilePartner in your install path 
   eg: # /<install path>/MobilePartner 
 
* Plug in your device, it will run automatically(Not supported in Xandros)

OK.  So I point the terminal to 
```
andrew@andrew-laptop:/media/Safaricom/Linux$ 
```
and I type 
```
sudo install
```

it doesn't work.  

I'm at a loss.  Any help?

---

