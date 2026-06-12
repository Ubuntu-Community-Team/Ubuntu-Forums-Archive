---
title: "Newbie deleted windows"
date: 2010-06-15
forum: General Help
---

### Post by marcymarc on 2010-06-15
Heys guys, sorry if this has been answered i can't find a solution myself, i delete windows a while back, but i have received a new modem from my telco, it has i disk with it that won't work on ubuntu so i need to either get the modem working or recovery my whole system and start again, the old 2wire work straght up so this might if i install it in windows and install ubuntu again, the problem is when i start the windows vista recovery wizard, it starts to format and i get an error 0x400110020000100A, the modem is a thomson TG782T, can anyone solve one of the problems?

---

### Post by warfacegod on 2010-06-15
Did you try simply plugging in the modem and seeing if it works. Generally modem drivers aren't necessary in Windows or Linux.

---

### Post by Mark Phelps on 2010-06-15
> **marcymarc said:**
> ... i delete windows a while back ... the problem is when i start the windows vista recovery wizard, it starts to format and i get an error 0x400110020000100A ...

How are you running the recovery wizard if you deleted Vista? Are you booting from a CD/DVD? If so, is it a Vista Installation DVD? OR is it a Vista Recovery CD that came with the machine?

Also, did you delete the Recovery partition when you removed Vista?

---

### Post by HermanAB on 2010-06-15
Hmm, firstly you should not need the junk telco software to get the modem to work.  Assuming that you mean DSL or Cable Router/Modem, just plug it in and connect to it with Firefox.

Secondly, if you need Windows, install Virtualbox or VMware Player and run Windows as a Virtual Machine.  Then you can run Windows in a window.  

Dual booting is so 20th century...
;)

---

### Post by lukeiamyourfather on 2010-06-15
> **HermanAB said:**
> Secondly, if you need Windows, install Virtualbox or VMware Player and run Windows as a Virtual Machine.  Then you can run Windows in a window.

Word. Virtual machines have come a long way, just make sure hardware virtualization is enabled in your BIOS (if it has it).

```
sudo aptitude install virtualbox-ose
```
...or...
```
sudo apt-get install virtualbox-ose
```

Sometimes ISP will require software to activate the service, not necessarily as a driver. Such rubbish but that's how it goes. Cheers!

---

### Post by spotted zebra on 2010-06-15
> **HermanAB said:**
> Hmm, firstly you should not need the junk telco software to get the modem to work.  Assuming that you mean DSL or Cable Router/Modem, just plug it in and connect to it with Firefox.

Secondly, if you need Windows, install Virtualbox or VMware Player and run Windows as a Virtual Machine.  Then you can run Windows in a window.  

Dual booting is so 20th century...
;)

if you are going to connect to the modem via firefox you just go the url bar (can't remember technical name) and type '192.168.0.1'. this should give the "back side" of the modem kinda like the back side of a router. 

just thought i would give some clarification here because not everyone knows how to do this.

dual booting is freaking awesome by the way but a virtual machine is much nicer if you are only using it for something like this.

---

### Post by marcymarc on 2010-06-15
ok so i called the telco and i disc is just the install guide, i plug in the modem all lights turn green but i can't seem to connect to it via the telco instrution, the procoess is the same as the old modem according to them, but it tells me it can't connect, i have to keep swapping modems so i know it's not the wiring, i do however lose the arrows connection icon but get a wifi symbol with a red ! i don't have a wifi computer

---

### Post by jarmore on 2010-06-15
try ```
sudo pppoeconf
```

(You have to hit <TAB> key to move around)

instructions from here ..if you have pppoe:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

I assume you don't have your own router.

---

