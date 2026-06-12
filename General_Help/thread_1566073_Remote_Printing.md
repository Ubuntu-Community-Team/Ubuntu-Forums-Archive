---
title: "Remote Printing"
date: 2010-09-01
forum: General Help
---

### Post by Bynw on 2010-09-01
I would like to be able to print remotely.

I am running 10.04 LTS and have an HP LaserJet P1006 printer connected to my computer. I have found a number of references over the net about internet printing via IPP or HTTP. And would like to be able to print from anywhere. Sending the print job via the net to my home printer where it will be waiting for me. 

My printer is marked as shared. Allowing printing over the internet. But yet if I try to print via IPP to the IP address of my computer which has the printer connected to it. I am unable to print. I can only print locally from the 1 computer connected to the printer.


Thanks

---

### Post by gypsumwolf on 2010-09-01
**1)** On the computer try opening we-browser and type in

```
IP_of_computer:631
```

**Note:** This will pull-up a cups server page.

**2)** Click on **"Printers"**

**3)** View the name of your printer in the list.

you printer is probably located at
```
your_ip_address:631/printers/your_printer_name
```

**Note:** For me, it does not print if I just use the ip address alone.

--------------------------------------------------->>
[B]
If you do not have CUPS than type this in Terminal:[/B]

```
sudo apt-get install cups
```

---

