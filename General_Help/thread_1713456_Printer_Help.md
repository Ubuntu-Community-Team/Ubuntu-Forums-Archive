---
title: "Printer Help"
date: 2011-03-24
forum: General Help
---

### Post by dazman19 on 2011-03-24
Hi

I am trying to hook up a Zebra 2844 label printer using cups.
Its a USB printer and i jammed a dlink USB print server on it to give it an IP. I set it up with these addresses: 
socket://IP/
ipp://IP/ 
and [http://IP/](http://IP/) 
but no go on either of them yet.

Personally i dont care if the files come out looking terrible. I am developing some software and i only need it to print plain text. 
I know it definitely goes if i print through windows. And making the port the IP address.
But i have a PHP script that calls system('lpr filename.txt'); and i need it to print at that printer so my software has integrated printing. I have been reading about these .ppd files, I assume they are drivers. And i hooked one of them up to this particular printer and I can see all the label sizes etc in CUPS. But it still wont print. There is one more file on apples open source website that people have used with BSD and linux before the filesize is a LOT bigger so i will try it. 

Have you ever done much work with these before? Or have any idea what I can do to fix it?

---

### Post by Hakunka-Matata on 2011-03-24
what happens if you try to add the printer via System>Administration>printers?

---

### Post by dazman19 on 2011-03-24
Its says its all sweet until i print something.
When i add it using that method i have to select it from a list or specify a PPD file. The job just gets stuck there with a red triangle on the printer.

I have tried adding it using lpadmin aswell, I have the same problem.

I will try the other PPD file tomorrow.

In cups or in System>Administration>Printers i can get to the label sizes and settings (which i dont really care about now until i get a piece of text to come out of this machine).

---

### Post by Hakunka-Matata on 2011-03-24
.ppd file drivers are VERY convenient.

---

### Post by dazman19 on 2011-03-24
thanks the other ppd files i have are different to this one i will give it a shot tomorrow

---

### Post by dazman19 on 2011-03-24
You my friend are the bomb. This is the 4th ppd file i tried but it just worked! i am super stoked. Thanks very much for you assistance.

---

### Post by Hakunka-Matata on 2011-03-24
my pleasure you ole kiwi
Gday

---

