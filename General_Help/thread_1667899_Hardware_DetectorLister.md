---
title: "Hardware Detector/Lister?"
date: 2011-01-15
forum: General Help
---

### Post by mark2741 on 2011-01-15
I've had a custom-built desktop for a few years and am now looking to rid myself of it and go with a laptop as my only computer.

I'm running Ubuntu 64-bit 10.10 and was wondering if there was a program out there that does a scan of the hardware and lists out what parts are in the PC like type and manufacturer of RAM, processor, graphics card, etc.?

I know on the Windows side there is Belarc advisor (I think that's what it was called). Was hoping there was something available for linux similar.

---

### Post by Smart Viking on 2011-01-15
```
lspci
```
is useful for listing all the pci devices.

---

### Post by ebasa on 2011-01-15
hardinfo is in the repositoies

---

### Post by solar george on 2011-01-15
lshw is included in the default install, if you type ```
 sudo lshw -html > hw.html 
``` into a terminal it will create a html file called hw.html with a nicely layed-out, detailed hardware list.

---

### Post by mark2741 on 2011-01-15
Thanks. Unfortunately that program crashes when I click 'System' but the other buttons work. I've got most of what I need except for the manufacturer and type of RAM, as both of the above tools simply tell me how much RAM is installed and used but not the manufacturer name.

Reason I wanted a program to do all this was so I could list all of these parts on Ebay/craigslist without having to disassemble anything, since this is my only computer right now. I may just go ahead and buy the laptop soon and sell the PC parts after as it would definitely make it easier.

Thanks again.

---

### Post by mark2741 on 2011-01-15
Solar George - thanks - very useful. That useful command gave a lot of info. More than the other programs that I installed did.

---

### Post by Lt. Surge on 2011-02-04
> **solar george said:**
> lshw is included in the default install, if you type ```
 sudo lshw -html > hw.html 
``` into a terminal it will create a html file called hw.html with a nicely layed-out, detailed hardware list.

... All I get in the Terminal is

PCI (sysfs)

and nothing happens. I have a feeling I did something wrong, or DIDN'T do something.

---

### Post by cascade9 on 2011-02-04
> **Lt. Surge said:**
> ... All I get in the Terminal is

PCI (sysfs)

and nothing happens. I have a feeling I did something wrong, or DIDN'T do something.

If you want to see the readout in terminal, just use this command- 

sudo lshw

---

### Post by Lt. Surge on 2011-02-04
> **cascade9 said:**
> If you want to see the readout in terminal, just use this command- 

sudo lshw

Thank you :)

Oh, what does "recommend you super-user" mean?

---

### Post by cascade9 on 2011-02-04
super-user ('su' or 'substitue user', or 'root') isnt really used on ubuntu. 

lshw will give more information if run in su. If you used the sudo command before lshw you will get the same readout as su would. 

'sudo' = 'su do' 

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by Lt. Surge on 2011-02-05
> **cascade9 said:**
> super-user ('su' or 'substitue user', or 'root') isnt really used on ubuntu. 

lshw will give more information if run in su. If you used the sudo command before lshw you will get the same readout as su would. 

'sudo' = 'su do' 

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

Thank you thank you

---

### Post by cascade9 on 2011-02-05
No problem ;)

---

