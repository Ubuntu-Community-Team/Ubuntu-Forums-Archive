---
title: "Wireless randomly drops connection and refuses to reconnect"
date: 2010-03-23
forum: General Help
---

### Post by RonB123123 on 2010-03-23
Hi, my wireless will connect to a well known connection but will sometimes drop the connection then tries to reconnect. Sometimes it will reconnect w/o a problem but most times it will fail and when it fails it will refuse to even recognize that same wireless connection. 

If by a small chance it does recognize the network then when you click on it, it will ask you again for the password, which is already saved onto the computer. After entering the password it will try to reconnect, then fail.

Only solution is to reboot.

I was wondering if there was an easy temporary fix of just reloading the software that controls the wireless.Such as, my audio doesn't work when I boot. I need to reload the ALSA driver using sudo /sbin/alsa force-reload

Is there something specific to the wireless that I can force-reload and it will start working w/o having me reboot my PC?

Thanks,
Ron

---

### Post by cogier on 2010-03-23
I had issues similar to this with an eeepc. My solution was to remove all the router's security. This solved the problem. 

I then used the router's "Wireless Station Access List" to add the MAC number of the wireless card. This gave me the security I needed.

---

### Post by RonB123123 on 2010-03-29
This works fine on Windows, isn't there a way to fix this issue without putting in my mac address onto my router?

---

### Post by cryptotheslow on 2010-03-29
What wireless adapter are you using?

I have the ~exact~ same symptoms with a BT Voyager 1055 usb adapter in karmic (still unresolved) - only a reboot will recover the connection once it drops.

Running Win2K on the same pc and it works flawlessly, which leads me to suspect it is a driver problem - sadly I can't get the windows driver to work with ndiswrapper in karmic so I'm stuck with the native driver support.

Could you post up results of these commands (run from terminal):
lsmod
lspci
lsusb

Would be a start at least.

---

### Post by eflester on 2010-03-30
I will add my 2 cents here just to say that with 9.10 on two different laptops I have no wireless functionality. I have tried numerous fixes to the point of near insanity. Short term fix: a 50 foot patch cable. Long term fix: I ordered a usb wireless NIC, I hope it works.

To the fellow who is using MAC address filtering: this will probably keep someone from connecting to your router if they are innocent non-hacker types. What it will not do is prevent someone from reading the stream of data from your laptop to your router. Your credit card number, perhaps. 

It always used to be sound that didn't work with Linux. These days it's wireless. Oh well, some day this will get fixed. 

It's still better than frickin' Windoze. 

Oh, and, by the way, wireless works fine (WPA encryption) with both of these laptops when running Redmond's Finest Operating System.

For the curious, the laptops are a Dell XPS M1530 (Intel 4965agn nic) and a Dell Mini-9 netbook (Broadcom 4312, yes I installed the driver).

---

### Post by Fluffgar on 2010-11-15
It sounds like the same problem I am having. 

At seemingly random times the connection will disappear and nothing other than a reboot has so far fixed it.

---

### Post by eflester on 2010-11-15
First, I must apologize to everyone here for not following up on my last post. "I forgot" is the excuse, for whatever good that does. 

I solved the problem described above by replacing the router. I had been using a (cheap) Belkin F5D7230-4 wireless router. When I replaced it with a Linksys WRT54GL everything negative described above disappeared. Why the device would work with Windows and not with Linux is beyond my understanding.

I never used the USB NICs, and gave them away to a happy friend who needed them.

I have since upgraded to 10.04 and wireless is still working 100% of the time.

---

