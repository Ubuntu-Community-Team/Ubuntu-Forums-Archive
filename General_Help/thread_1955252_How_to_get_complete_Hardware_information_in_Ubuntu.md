---
title: "How to get complete Hardware information in Ubuntu 10.04 (Lucid Lynx)"
date: 2012-04-09
forum: General Help
---

### Post by keymeh on 2012-04-09
Hello friends,

I am new user in Ubuntu 10.04 (Lucid Lynx). 

I want to collect all hardware details including Ram, cpu, processor, hard drive, pci controller, ethernet card, mother board, & all hardware information in detailed. 

I tried to install sysinfo & hardinfo but it was not installed in my os. So I try to collect information using Terminal. I have used dmidecode & lshw command. But some information are not available like mother board brand, ram type (DDR2 OR DDR).

One more thing I want to know is that in my pc, zotac 8400 gs spliter card is installed. but i did not get any information related to card using above command.

So pls. help / guide me in getting details.

Thanks in Advance

Keyur

---

### Post by kimda on 2012-04-09
You can try this command at the terminal. I've piped the output to hardware.txt. 

```
sudo lshw > hardware.txt 
```

---

### Post by kimda on 2012-04-09
You can also use hardinfo which is a gui program.

---

### Post by kimda on 2012-04-09
Sorry. I answered a bit too quick ;-). You allready tried these things. I do not think you can find a program which will tell you exactly what the brand name is of (ex.) your videocard.

---

### Post by keymeh on 2012-04-09
Any terminal command that can give full information about motherboard and other hardware details ?

---

### Post by malangaman on 2012-04-09
Ultimate boot cd has helped me with some of these problems.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Yellow Pasque on 2012-04-09
dmidecode does tell you the mobo manufacturer (assuming manufacturer correctly placed the info in the BIOS):
```
Base Board Information
	Manufacturer: BIOSTAR Group
	Product Name: TA890FXE

```

---

