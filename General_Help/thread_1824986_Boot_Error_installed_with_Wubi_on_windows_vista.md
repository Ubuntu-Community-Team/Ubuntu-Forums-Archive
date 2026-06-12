---
title: "Boot Error installed with Wubi on windows vista"
date: 2011-08-14
forum: General Help
---

### Post by hiqbal on 2011-08-14
I have installed ubuntu 11.04 using wubi with Windows Vista Home Premium 32 bit. The operating system works fine.

  Althoughwhen I boot and choose linux I get an error message during boot which stays forever. I have to shut down using power button and start again when it boots fine. 

Another problem is when I restart from ubuntu it restarts back to the desktop but when I shut down, it does not shut down the computer. Stays on with blank screen forever. 

I am attaching the image of latest error I received on boot.

Thanks in advance for suggestions.

---

### Post by Rubi1200 on 2011-08-15
Hi and welcome to the forums :-)

Please post the make and model of the computer as well as the full specifications.

Thanks.

---

### Post by fdrake on 2011-08-15
type
```
dmesg |nl | grep "panic"
```
get the line number on the left where it says  "? panic+0x91/0x19c" .
type
 
```
dmesg |nl |less
```

and go to that line post here 5-10 lines before and after that number.

do you have any usb devices plugged?

---

### Post by plursheep on 2011-08-15
has it booted at all?

I had to work around WIndows.  Basically I downloaded Ubuntu and ran it right away through Windows.  Then stuck in a live CD during boot.  

Your first boot is actually still installing everything I believe.

---

### Post by hiqbal on 2011-08-15
> **fdrake said:**
> type
```
dmesg |nl | grep "panic"
```
get the line number on the left where it says  "? panic+0x91/0x19c" .
type
 
```
dmesg |nl |less
```

and go to that line post here 5-10 lines before and after that number.

do you have any usb devices plugged?

It does not reach desktop after this error. I have to shutdown using power button and then boot again. It works fine then. Also with the shutdowns and restarts in ubuntu, it just stops and doesnt shutdown.

I do not have any usb devices attached. I would like to know where to use the commands you mentioned?

---

