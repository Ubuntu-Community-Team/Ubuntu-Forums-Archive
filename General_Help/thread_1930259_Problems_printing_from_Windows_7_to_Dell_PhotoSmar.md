---
title: "Problems printing from Windows 7 to Dell PhotoSmart C4580 connected to Ubuntu Desktop"
date: 2012-02-23
forum: General Help
---

### Post by CarlWalters on 2012-02-23
Hello, 

I'm running Ubuntu 11.10 on my desktop while my wife has a netbook running Windows 7. I have a Dell PhotoSmart C4580 Wireless Printer which is attached via USB to my Ubuntu desktop. I can print fine from my Ubuntu desktop. 

Until recently my wife was able to connect wirelessly to the printer and print OK.  However we recently upgraded our router (as O2 sent us a shiny new one :)) and she is no longer able to connect to the printer wirelessly! (I've no idea why this should be though)

So I thought I would try to enable printing via CUPS.  I followed  the instructions [**here**]("http://askubuntu.com/questions/73367/what-is-a-cups-server-and-how-to-share-a-printer-over-a-network") to enable printer sharing over the network and then followed the instructions [**here **]("http://ubuntuforums.org/showpost.php?p=8404116&postcount=6") to make the printer visible to a Windows 7 machine. 

However the Windows 7 netbook still cannot find the printer even though it can see the address **[http://ubuntu:631/printers/Photosmart-C4500-series](http://ubuntu:631/printers/Photosmart-C4500-series)**

I'd love to be able to either get back to having the Window 7 netbook be able to see the printer wirelessly or via CUPS. 

Any advice gratefully received :)

---

### Post by davidvandoren on 2012-02-23
You have to open port 631 on your firewall.
Either through the terminal or install gufw firewall configuration and open it from there. 

If you have a stable ip through your service provider you could try to access the printer over the Internet. 

**[http://]("http://ubuntu:631/printers/Photosmart-C4500-series")[COLOR=Red][your ip]("http://ubuntu:631/printers/Photosmart-C4500-series")[/COLOR]****[:631/printers/Photosmart-C4500-series]("http://ubuntu:631/printers/Photosmart-C4500-series")**

---

### Post by CarlWalters on 2012-02-23
> **davidvandoren said:**
> You have to open port 631 on your firewall.
Either through the terminal or install gufw firewall configuration and open it from there. 

Sorry I'm a bit confused, doesn't the fact that I can access the printer which is connected via USB to my Ubuntu machine in the study from the Win7 netbook in the kitchen by going to **[http://ubuntu:631/printers/Photosmart-C4500-series](http://ubuntu:631/printers/Photosmart-C4500-series)** mean that Port 631 is open? 

I downloaded gufw, but I haven't worked out how to use it yet.

---

