---
title: "dmesg explained"
date: 2012-06-09
forum: General Help
---

### Post by Binary-Synapse on 2012-06-09
Hello,
 
Taking the following dmesg excerpt from my system, I would like to know a bit more about the marked coloured parts:
 
[ [COLOR=red]1.614145[/COLOR]] ehci_hcd [COLOR=darkgreen]0000:00:1d.7[/COLOR]: irq 23, io mem [COLOR=navy]0x40104000[/COLOR]
[ [COLOR=red]1.628728[/COLOR]] r8169 [COLOR=darkgreen]0000:05:00.0[/COLOR]: eth0: RTL8102e at [COLOR=navy]0xf8228000[/COLOR], [COLOR=magenta]00:03:0d:fd:64:b1[/COLOR], XID [COLOR=darkorange]04e00000[/COLOR] IRQ 43
[ [COLOR=red]1.660074[/COLOR]] ehci_hcd [COLOR=darkgreen]0000:00:1d.7[/COLOR]: USB 2.0 started, EHCI 1.00
 
Red=???
 
Green=???
 
Blue=blue section is the _start memory interval_ a specific hardware device occupies in the system's RAM memory map. Correct if I'm wrong though...
 
Pink=pink section is the LAN MAC address. Correct if I'm wrong though...
 
Orange=???
 
Ah... one other thing:
In what conditions can the RED, GREEN and BLUE values change?
For example can they change if I reboot, or add a new hardware device?
And if they can change, what controls that change? The kernel?
 
Thank you

---

### Post by Doug S on 2012-06-09
Red is the time in seconds since the last re-boot or power up.

---

### Post by matt_symes on 2012-06-09
Hi

Red is the time stamp.

Green looks to be the PCI bus ID.

Blue is a memory address. Maybe the DMA address ? I don't believe it's the PCI configuration space address because of the values.

As you say, pink is the lan card MAC address.

I'm unsure about orange. Maybe it's a firmware ID or a chipset ID. I'm not sure.

As for what changes when, i'm not totally sure without looking at the code or reading the PCI spec. I'm not going to do that tonight though ;)

Kind regards

---

### Post by Binary-Synapse on 2012-06-10
Hello.
 
 
> **Doug S said:**
> Red is the time in seconds since the last re-boot or power up.
 
 
Using your information, I read a bit more, and indeed it is the time stamp.
It's not in human readable format though...
 
Thanks.

---

### Post by Binary-Synapse on 2012-06-10
> **matt_symes said:**
> Hi
 
Blue is a memory address. Maybe the DMA address ? I don't believe it's the PCI configuration space address because of the values.
 
I'm unsure about orange. Maybe it's a firmware ID or a chipset ID. I'm not sure.
 
As for what changes when, i'm not totally sure without looking at the code or reading the PCI spec. I'm not going to do that tonight though ;)
 
Kind regards
 
So blue is **not** the start of a dedicated portion of RAM space for hardware usage?
 
Thank you.

---

### Post by kreemoweet on 2012-06-10
I believe [1.660074] means just 1.660074 seconds. It doesn't get much more
human-readable than that.

---

### Post by matt_symes on 2012-06-10
Hi

> So blue is not the start of a dedicated portion of RAM space for hardware usage?

The blue is a dedicated portion of memory for the device. I'm just not sure what that memory is dedicated for.

I will be reading through the PCI spec at some point soon and then i will be able to tell you.

Maybe this will hold some clues for you.

[http://www.xml.com/ldd/chapter/book/ch15.html](http://www.xml.com/ldd/chapter/book/ch15.html)

Kind regards

---

### Post by Binary-Synapse on 2012-06-10
> **kreemoweet said:**
> I believe [1.660074] means just 1.660074 seconds. It doesn't get much more
human-readable than that.
 
Yes you are right.
 
But what I meant was: instead of the format seconds.microseconds, it would be better if it was in the ISO8601 format.
Something like 2012-06-09 21:30:00.
 
Because otherwise it only serves as a time counter starting from the boot moment (which is still usefull)... but you will have to perform some time calculations if you need to know for example at what time/date a specific error (trapped by dmesg) really ocurred.
 
But nevermind... I found what I was looking for:
cat /var/log/kern.log
 
The command above, will print both the normal dmesg time stamps AND ALSO the ISO8601 time stamp.
And in my system *dmesg -T* doesn't work.
 
Thank you.

---

### Post by Binary-Synapse on 2012-06-10
> **matt_symes said:**
> Hi
 
The blue is a dedicated portion of memory for the device. I'm just not sure what that memory is dedicated for.
 
I will be reading through the PCI spec at some point soon and then i will be able to tell you.
 
Maybe this will hold some clues for you.
 
[http://www.xml.com/ldd/chapter/book/ch15.html](http://www.xml.com/ldd/chapter/book/ch15.html)
 
Kind regards
 
Thank you Matt.
 
I would appreciate if you could provide me more insight on that matter (when you have the time).
 
And also... thank you for the provided URL.

---

