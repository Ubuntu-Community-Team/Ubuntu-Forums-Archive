---
title: "Need Ubuntu 8.10"
date: 2010-06-30
forum: General Help
---

### Post by jaffarado on 2010-06-30
Hi.
I need Ubuntu 8.10 with kernel 2.4.XX because i have device who is using only me country. It is FLARION mobile internet some thing between 2G and 3G T-Mobile is testing this technology in my country. I download Ubuntu 8.10 but every time this ISO or Release have kernel 2.6.xx and my driver do not work. Therefore i need  image ubuntu 8.10 with kernel 2.4 or some manual how downgrade kernel. I find same how to manual and i am not able to do it.
PLS hellp and sorry for my English

---

### Post by yeleek on 2010-06-30
[http://old-releases.ubuntu.com/releases/intrepid/](http://old-releases.ubuntu.com/releases/intrepid/)

Sorry only read 2.4 bit after

By default 8.10 was 2.6

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs)

---

### Post by jocko on 2010-06-30
> **jaffarado said:**
> Hi.
I need Ubuntu 8.10 with kernel 2.4.XX because i have device who is using only me country. It is FLARION mobile internet some thing between 2G and 3G T-Mobile is testing this technology in my country. I download Ubuntu 8.10 but every time this ISO or Release have kernel 2.6.xx and my driver do not work. Therefore i need  image ubuntu 8.10 with kernel 2.4 or some manual how downgrade kernel. I find same how to manual and i am not able to do it.
PLS hellp and sorry for my English
There is NO way you can get a 2.4 kernel for ubuntu 8.10. Even the first ubuntu release ever (4.10) had a 2.6 series kernel.
If you really need a 2.4 series kernel, you need to go back to a distro released earlier than December 2003 when the first 2.6 kernel was released.
And I seriously doubt that an antique distro with a 2.4 series kernel would support anything as modern as mobile internet.

---

### Post by obscurant1st on 2010-06-30
i think if u compile it with the newer kernel it will work. not sure though :)

---

### Post by yeleek on 2010-06-30
Perhaps another angle is - what exactly is the actual hardware?  A usb device?  Whats the chipset?

Is it this 

[http://open-nandra.com/2010/02/t-mobile-leadtek-usb-modem-lr7f04-flash-ofdm-flarion-kernel-driver/](http://open-nandra.com/2010/02/t-mobile-leadtek-usb-modem-lr7f04-flash-ofdm-flarion-kernel-driver/)

---

### Post by jaffarado on 2010-06-30
Thank you for ALL, You are great.
I read link from you and i go tested it now.
After my test will  done. I will write result of my test.
Thank you again.

My (actually HW of my Father  ) HW configuration is:
MB        : MSI K8NEO3 chip set Nvidia 4-4X
VGA       : Nvidia FX 5600
CPU       : AMD Sempron 2800+
USB Modem : T-mobile Leadtek USB modem LR7F04 Flash-OFDM Flarion.

Father usually needed  only EMAIL and WEB browsing. :)

---

### Post by davidmohammed on 2010-06-30
can you just confirm the exact details of your modem

please type in a terminal

lsusb

---

