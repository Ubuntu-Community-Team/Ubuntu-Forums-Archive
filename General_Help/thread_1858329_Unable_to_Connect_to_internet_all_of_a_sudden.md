---
title: "Unable to Connect to internet all of a sudden"
date: 2011-10-12
forum: General Help
---

### Post by sarin_cv on 2011-10-12
Hi...I'm using a cable modem and connecting using LAN. It was working fine but stopped suddenly. Can you please help me in diagnosing the issue... I am using a Dell Studio 1535 laptop with a Broadcom Wireless 1397 802.11b/g Half Mini Card NIC. It was having Windows 7 and since it's under warranty, I called Dell customer care...They asked me to certain things and then asked to reinstall the OS. In Windows command prompt, when I do ipconfig it's showing media disconnected. Customer care person is insisting me to reinstall OS whcih I don't want to do since I've so many things to backup. They are damn sure that it's a software issue and not ready to inspect the hardware onsite unless I reinstall the OS. They also told me that it can be due to my Dual boot :)

Thanks in advance,
sarin

---

### Post by sarin_cv on 2011-10-12
up...

---

### Post by cryptotheslow on 2011-10-12
Some basics first.....
1. What version of Ubuntu are you dual-booting with Windows 7?
2. And is it a "proper" dual-boot configuration in its own partition(s) or a Wubi install?
3. Did the wireless connection previously work under both Ubuntu and Win7?
4. Does the wireless connection now **not **work under either (both) operating system?
5. Does the laptop have an ethernet port and can you connect using that (under either or  both operating systems)?

---

### Post by IanW on 2011-10-12
Are you sure it's your laptop & not your cable connection?

---

### Post by Mark Phelps on 2011-10-12
> **sarin_cv said:**
> Customer care person is insisting me to reinstall OS whcih I don't want to do since I've so many things to backup. They are damn sure that it's a software issue and not ready to inspect the hardware onsite unless I reinstall the OS. They also told me that it can be due to my Dual boot :)

WOW -- standard, useless responses.  And they dare to call themselves Customer "Care"!!

We can't do anything for you until you answer the question in cryptotheslow's post ...

---

### Post by sarin_cv on 2011-10-13
1. I'm using Ubuntu 11.04
2. Yes. Ubuntu has it's own partition. Not a wubi install.
3,4,5. The problem is with Ethernet. It was working previously in both Ubuntu 11.04 and Windows 7 and now it's not working in both. The modem has only the ethernet option, No wirelss.

---

### Post by sarin_cv on 2011-10-13
> **IanW said:**
> Are you sure it's your laptop & not your cable connection?

The Internet provider guys checked the connection and all and sugegsted it would be a hardware issue with NIC. They asked me to contact laptop technical support.

---

### Post by cryptotheslow on 2011-10-13
I am confused. In your OP you state:
> **sarin_cv said:**
> .... I am using a Dell Studio 1535 laptop with a Broadcom **Wireless 1397 802.11b/g** Half Mini Card NIC............


Then later:
> **sarin_cv said:**
> 3,4,5. The problem is with Ethernet. It was working previously in both  Ubuntu 11.04 and Windows 7 and now it's not working in both. The modem  has only the ethernet option, **No wirelss**.


Anyways up - if the ethernet connection stopped working in both Win7 and Ubuntu at the same time then it is **very** unlikely to be a software / OS related issue. Much more likely to be a fault with the ethernet NIC in your laptop, the cable modem or most likely a basic service fault with the ISP connection.

Most ethernet NICs have little green or yellow LEDs on them right next to the port that light up when a connection is made. Does this happen when you plug your ethernet cable into the modem (on either the laptop NIC or the modem NIC)?

Have you tried a different ethernet cable?

Do you have any other ethernet enabled device that you can plug into the cable modem to test with?

---

### Post by sarin_cv on 2011-10-13
The LED lights on the port are blinking. I haven't tried a different cable. Will try tomorrow and update. Don't have any other ethrenet device but I'll try with a friend's laptop tomorrow and will update.

---

### Post by sarin_cv on 2011-10-14
I tried with a different Ethernet cable...The modem has also support USB connectivity.....both didn't work....

---

