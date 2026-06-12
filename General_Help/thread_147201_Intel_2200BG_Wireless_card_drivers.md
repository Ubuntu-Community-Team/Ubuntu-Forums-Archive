---
title: "Intel 2200BG Wireless card drivers"
date: 2006-03-19
forum: General Help
---

### Post by globemast on 2006-03-19
Hello,

I have a laptop where i installed recently Ubuntu 5.10 and i have the following problem. 

It seemts that Ubuntu cannot recognize my Intel 2200BG wifi card. The wireless card interface is not even available.

Can you help me setup the wireless card drivers.


Thank you very much.

---

### Post by globemast on 2006-03-22
Anyone with a bit on help on the above please?

---

### Post by jethro10 on 2006-03-22
Well I'm as new as you, and your right this :- [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

lists all cards whos'e information is known.

If there is no native method, you can use ndis wrapper which actually takes the windows drivers and access then through linux. Aparently this should work for non native compatible ones.

I dont know much more, search for "ndis wrapper".

jeff

---

### Post by jethro10 on 2006-03-22
Here goes, hope it helps.
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)


Jeff

---

### Post by Ramses de Norre on 2006-03-22
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

---

### Post by Robor on 2006-03-22
I'm using an IBM T42 with an Intel 2200bg card and it was supported by Ubuntu out of the box.  However, the past few kernel updates have broken it.  I'm too new to Linux to understand why that happens but what I've done is go through the install process described in the beginning of this thread...  [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=intel+2200bg]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=intel+2200bg")

Yes, I know that's to get WPA working but if you look through the initial steps it walks you through unloading the old driver & firmware and how to install the new stuff.  Keep in mind you can't just copy/paste exactly what's there as you'll need to be using the newer driver and firmware from those download links.

Hope that helps!  :)

---

### Post by Robor on 2006-03-22
This is probably a better link for updating the IPW2200bg.  That's the one I used...

[http://doc.gwos.org/index.php/Install_ipw2200]("http://doc.gwos.org/index.php/Install_ipw2200")

---

