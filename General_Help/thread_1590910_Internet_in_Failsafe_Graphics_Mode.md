---
title: "Internet in Failsafe Graphics Mode"
date: 2010-10-08
forum: General Help
---

### Post by Edhas on 2010-10-08
I'm facing a peculiar problem with my Ubuntu 10.04. In the normal graphics mode, while connecting to the internet, it is showing "Resolving host" in the browser and never gets connected. However, when I boot the m/c in to FailsafeX Graphics Mode (under repair option), I can surf the internet. I think there might be some problems with the graphics. Looking for your suggestions to solve this.

---

### Post by Edhas on 2010-10-08
I need help guys....anyone there .. cant connect net in normal mode. internet works only in failsafe mode. cant figure out what's going wrong .

---

### Post by markh789 on 2010-10-08
I don' know what could be causing it.

Your Network Monitor (Top right hand bar, should be next to the sound icon), click it and select "Auto eth0" - that fix it?

---

### Post by Edhas on 2010-10-09
Hi,

  My Ubuntu does not have the icon as I use a diff theme (from when I switched to Ubuntu). I used to type "sudo pppoeconf" to connect my DSL modem (eth0). It is getting connected correctly. But all the browsers are showing "Resolving Host". Even, I booted Ubuntu in the text mode and tried in the text-based browser "Elinks". The same problem is there. After googling, I disabled the ipv6 and changed the "quiet splash" to "quite splash noapic" in /etc/default/grub.

File: /etc/default/grub
Actual text -> GRUB_CMDLINE_LINUX_DEFAULT="***quiet splash***".

It was changed to 
                       GRUB_CMDLINE_LINUX_DEFAULT="***quiet splash nomodeset***".
I tried too
                       GRUB_CMDLINE_LINUX_DEFAULT="***quiet splash noapic***".

Still the same problem. I don't know what is going wrong.

---

### Post by efflandt on 2010-10-09
Some things to check or compare between working or not working:

**ifconfig -a**
(whether pppoe0 has an IP)

**route -n**
(proper default route at bottom)

**cat /etc/resolv.conf**
[nameserver(s)]

Also check if the hostname in /etc/hostname is listed in /etc/hosts (in case something with pppoe changes your hostname)

But it has been many years since I have done pppoe in Linux because most DSL modems now are modem/routers that handle the pppoe.

---

