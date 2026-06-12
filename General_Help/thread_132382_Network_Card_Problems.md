---
title: "Network Card Problems"
date: 2006-02-18
forum: General Help
---

### Post by aspenbus on 2006-02-18
I installed Ubuntu a few weeks ago, and can't get my wireless network card to work - I can "see" the card in the device manager, but Ubuntu doesn't seem to be able to find it otherwise. (I went to "Terminal" and installed the inf/sys drivers that I'd previously copied from the card's software disc, but that didn't change anything.) Help?

(Assume I'm a moron. Use small words and short sentences. ;) )

---

### Post by romdos on 2006-02-18
what is the brand and model number of the wireless card?
do you know what chipset it uses?
not all chipsets work out of the box with ubuntu

type this into your terminal

```

romdos@freekbox:~$ iwconfig

```

and post the output. This will give us more info to work with

---

### Post by aspenbus on 2006-02-21
Well, I tried iwconfig...

shannon@ubuntu:~$ iwconfig
lo         no network extensions.
sit0      no network extensions.

... but I do have a working network card, I swear! It's a "Linksys Wireless-G PCI Adapter Model No. WMP54G 2.4GHz 54 Mbps ver1.2", according to the setup disk. And it worked fine when I was on Windows, so I don't know why it's ignoring me now.

---

### Post by romdos on 2006-02-22
i *think* that the  WMP54G ver1.2 uses a broadcom chipset.
to get it going you are going to need to muck around with [ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

---

