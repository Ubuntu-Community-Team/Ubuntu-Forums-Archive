---
title: "Browser issue in Ubuntu"
date: 2011-03-22
forum: General Help
---

### Post by testacc753 on 2011-03-22
Hi,

I have installed ubuntu recently. I am facing an eccentric problem with the browsers [firefox and chrome] on it...

Whenever i try opening the sites
[www.facebook.com](www.facebook.com) or [www.apple.com](www.apple.com) ........
The message in status bar will be "waiting for facbook.com or apple.com" and the sites never open, after 2 mins the an error message message is displayed...

But if i clear all the browsing data in firefox or chrome surprising the sites start working again for around 2 - 3 times...

I tried running firefox through command line but it never shows any error....

It would be a great help if any one could solve this problem.....

---

### Post by BlairKatu on 2011-03-22
That's a strange problem. See if restarting your networking system via ```
sudo /etc/init.d/networking restart
``` has a similar effect to clearing the cache and report back if you don't mind. Also is there a chance this could be a problem with your network and not with the ubuntu machine?

---

### Post by testacc753 on 2011-03-22
not a problem with net bcz this is a dual boot pc.. everything works fine in windows


prasanth@ubuntu:~/Software/firefox$ sudo /etc/init.d/networking restart
[sudo] password for prasanth: 
 * Reconfiguring network interfaces...                                                Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
                                    [ OK ]

in linux also sites like google work fine...

---

### Post by dineshs on 2011-03-22
I think it is a problem with MTU.What connection is it ? DSL?
Are you using network manager?

---

### Post by cipherboy_loc on 2011-03-22
Is this a home network? If so, try rebooting the router... First shut down all systems connected to the router, then shutdown the router, then the modem (applicable), wait 5 seconds, start up the modem (if applicable), start up the router, wait 5 seconds, and start up the rest of the network.

What type of ethernet card do you have? ```
lspci | grep -i 'net'
```
Cipherboy

---

### Post by theteju on 2011-03-22
I am facing the same problem.

For the first time in past three years my XP is better than ubuntu. Its making me think now to boot from XP since the internet is running slow on ubuntu. 

my problem is not resolved by disabling ipv6 .

please solve the problem asap.

Thanks.

---

### Post by cipherboy_loc on 2011-03-22
@thetju: Did you try rebooting the router as detailed in my post? Did it suddenly happen, or has it been getting gradually slower?

---

### Post by no2498 on 2011-03-22
for some reason im thinking  you need to reinstall adobe and your browser

---

### Post by theteju on 2011-03-22
> **cipherboy_loc said:**
> @thetju: Did you try rebooting the router as detailed in my post? Did it suddenly happen, or has it been getting gradually slower?

Thanks for the reply,
yes it happened suddenly, I think after I updated my system recently, which got new kernel and updates for chrome and firefox. I have restarted router and modem many times. I actually called my IPS and created a ticket as I was not convinced that my ubuntu go slower. But later I found that internet connection is fast. so the problem is in 10.04.

recently i just downloaded opera to test, but it seems all browser's are running slow. probably the intel driver. I do not know.

please continue help.

---

### Post by theteju on 2011-03-22
here is my network controller.

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

The driver is : iwlagn

I am not sure how to check its version or firmware. 

I found intel's current driver for the card. its in tar.gz file.. And I am not even sure how to install the driver from scretch.

---

### Post by jbslaw on 2011-03-22
Try disabling ipv6. Ubuntu follows a standard of doing ipv6 lookups before ipv4 lookups.  If ipv6 isn't available it will wait to time out before dropping down to the older standard.  

If you do a search for "disable ipv6" you'll find a number of threads discussing how to do it and why.

---

### Post by theteju on 2011-03-22
> **jbslaw said:**
> Try disabling ipv6. Ubuntu follows a standard of doing ipv6 lookups before ipv4 lookups.  If ipv6 isn't available it will wait to time out before dropping down to the older standard.  

If you do a search for "disable ipv6" you'll find a number of threads discussing how to do it and why.

i said it before, 

disabling ipv6 did not resolve my issue.

---

### Post by cipherboy_loc on 2011-03-23
@thetuju
What Intel gave you was a compressed archive, which (if I remember correctly), contains a bunch of source code to be added to your kernel. If you compiled your own kernel, you would add that bit of firmware to the kernel and re-compile it. What version of network manager are you using?

Also, you should probably start a new thread.

Cipherboy

---

