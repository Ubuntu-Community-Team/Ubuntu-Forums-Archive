---
title: "no internet connection"
date: 2006-03-25
forum: General Help
---

### Post by JohnJSal on 2006-03-25
Hi everyone. I just tested out the Ubuntu (and Kubuntu) live CDs, and I noticed that I wasn't able to connect to the internet. How would I find what I need to do that? Does Ubuntu not auto configure it, or could it not find what it needed?

Thanks.

---

### Post by IYY on 2006-03-25
It's supposed to be autoconfigured, but depends on your network card. Which one do you have? Is it wired or wireless?

---

### Post by JohnJSal on 2006-03-25
I have a regular network card and a wireless card, but I don't think either was configured. I have a Dell 8600 (laptop).

---

### Post by Djartklom on 2006-03-25
From the top panel, check Networking preferences under the System menu and find out what (if any) network interfaces you have up and running.

---

### Post by akshaysrinivasan on 2006-03-25
try going to system>administration>networking in gnome and manually configure it

---

### Post by JohnJSal on 2006-03-25
P.S. Here is what I have in my Device Manager in Windows:

1394 Net Adapter (not sure what this is, FireWire? probably not relevant to my issue)

Broadcom 440x 10/100 Integrated Controller

Intel PRO/Wireless 2200BG Network Connection

Also, like I mentioned, I was using a Live CD, so I don't know if that affected anything. I will try your suggestions too.

---

### Post by jamesr on 2006-03-25
post the output of```
sudo ifconfig -a
dmesg |grep eth0
```

---

### Post by JohnJSal on 2006-03-27
There was too much there to write down, and I didn't have any other way of copying it. But I did notice that my network cards weren't configured, so perhaps manually entering the IP address, etc. might fix that. But I still don't know if I'll need extra software or drivers that don't come with the installation.

---

### Post by jamesr on 2006-03-27
I often copy and paste to a file then to a floppy in this case.

When you said
> But I did notice that my network cards weren't configured 
what do you mean, no tcp/ip address, no eth0 ?

Do the first two lines look like > eth0      Link encap:Ethernet  HWaddr 00:0A:E6:C6:07:85
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0


---

### Post by nanotube on 2006-03-28
hey johnjsal,

i have a dell inspiron 5150, and my network interfaces are exactly the same, Broadcom 440x 10/100 Integrated Controller, and Intel PRO/Wireless 2200BG. 
when i was booting with a live cd, the wireless did not work properly (although the wired worked). when i installed to disk, both interfaces were properly configured, automagically.

so, if you are trying to figure out how to enable your nics while booting livecd, i am not sure i can be of much help - but if you are wondering if it will work when you install to disk, i can say that that is almost a certainty, based on my own experience with these same network cards. :)

---

