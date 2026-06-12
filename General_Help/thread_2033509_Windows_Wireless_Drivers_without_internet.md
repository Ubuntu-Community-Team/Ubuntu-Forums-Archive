---
title: "Windows Wireless Drivers without internet"
date: 2012-07-26
forum: General Help
---

### Post by mmandemlin on 2012-07-26
Hello! 

I just started on this forum a literally few minutes ago and I am absolutely brand new to Ubuntu it's self so I know practically nothing about it, but I am a long time Windows user. I have a Netgear WNDA3100v2 (chipset: Broadcom BCM43XX) wireless adapter, I am using my friends copy of Ubuntu 11.10 and I have noted the lack of a functioning Netgear WNDA3100v2 drivers. I already have the drivers from the internet. But... I need the Windows Wireless Drivers, and the computer that I need it for isn't connected to the internet. We do have a router but all of the plugs are in use. And I need that computer connection to the internet so we can make our home e-mail server.

Please Help! 

Thank You!

---

### Post by daslinkard on 2012-07-27
Have you tried the following?

> sudo apt-get update

> sudo apt-get install firmware-b43-installer

> sudo apt-get remove bcmwl-kernel-source

> sudo reboot

---

### Post by Nixarter on 2012-07-27
> **daslinkard said:**
> Have you tried the following?

that works without the internet?  Does it search locally at first?

---

### Post by daslinkard on 2012-07-27
We can use Mint Linux and this link [here]("http://community.linuxmint.com/tutorial/view/692")

---

### Post by Ralph L on 2012-07-27
See [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) .  See the section at the beginning about identifying your chip.  Then see the section on no Internet access.  Basically what is required, when you don't have Internet access, is to get b43-fwcutter from the CD that you used to install ubuntu, and to get the firmware/driver from the location shown on the site above.  Downloading this firmware/driver can be done on any (including Windows) computer and brought over to your ubuntu system on a memory stick.  Then you run b43-fwcutter against the firmware/driver and it will extract the firmware and install it in ubuntu.

The web site talks about a patch, but there was no patch for 12.04 Precise Pangolin.  Probably isn't one for your system.

Hope this helps.

---

### Post by mmandemlin on 2012-07-27
> Have you tried the following?

Quote:
sudo apt-get update
Quote:
sudo apt-get install firmware-b43-installer
Quote:
sudo apt-get remove bcmwl-kernel-source
Quote:
sudo reboot

That will not work because I cannot connect to the internet at all with it.

---

### Post by daslinkard on 2012-07-27
> **mmandemlin said:**
> Hello! 

We do have a router but all of the plugs are in use. And I need that computer connection to the internet so we can make our home e-mail server.

Please Help! 

Thank You!

So what you are saying is you do have Internet but you are choosing not to connect via the wired connection to download the drivers?  May I ask why not disconnect one of the devices long enough to run the sudo commands I initially posted so you do have Internet?

---

### Post by cariboo on 2012-07-27
Have you tried inserting the install/Live cd and installing the drivers from it? Remember this is not Windows, most of the drivers are included with the kernel. The only time you need a network connection is if you are installing closed source drivers, for example graphics drivers from AMD and Nvidia.

---

### Post by mmandemlin on 2012-08-02
> **daslinkard said:**
> So what you are saying is you do have Internet but you are choosing not to connect via the wired connection to download the drivers?  May I ask why not disconnect one of the devices long enough to run the sudo commands I initially posted so you do have Internet?

Because. We do not have an ethernet cable long enough to reach the room I have the server in.

---

### Post by laserator on 2012-08-02
I had the same problem you may have to just sit next to the router plug it in and install it. It doesn't take too long.

---

### Post by daslinkard on 2012-08-03
I agree with laserator as that would make the most sense and would probably be the easiest solution.  Though it may not initially be convenient for you it will provide you with a solution to be able to get the wireless drivers.

---

