---
title: "I need some help setting up a printer!!"
date: 2009-10-02
forum: General Help
---

### Post by oospill on 2009-10-02
Hello fellow linux peeps!

I've got a desktop computer running Ubuntu Server, and a laptop running Ubuntu Desktop.

I would like to connect my printer to the server, and be able to print from my laptop. (I don't have to printer connected to anything right now.) 

Anyone have some applicable expertise?

Thanks!
oospill

---

### Post by ram2500 on 2009-10-02
localhost:901 will get you to the CUPS page. There, you can configure a local or networked printer. CUPS is Common Unix Printing System, and is a replacement for lpr from the Berkeley days. It's browser based, so it would be pretty simple.

What kind of printer is it (brand/model)?

---

### Post by ram2500 on 2009-10-02
localhost:631 is CUPS. I was thinking of Samba. Sorry.

---

### Post by oospill on 2009-10-02
okay.. I got cups installed in the server.. I set up the printer (it found and described my USB printer all by itself) .. I edited the config file to allow 192.168.1.0/24 .. I printed a test page.

I did all that on the server..

now, what do I do on my laptop to *use* that printer?  do I need to install cups?

thanks, oospill

---

### Post by ram2500 on 2009-10-02
I don't know about Ubuntu, but I do know that Fedora has CUPS preinstalled. From there, you can get to a networked printer and choose which one you'd want. I personally never worked with networked printers through CUPS, but I do know CUPS is a one-stop shop for local and networked printers.

---

### Post by oospill on 2009-10-11
well.. I got the printer working on the server.. printed a test page and everything.  I even got the [server's] printer to show up on my laptop..  but when I try to print a test page from the laptop, it does nothing!! help!

oospill

---

### Post by mechro on 2009-10-11
I don't know if it's the same with Server edition but try...

System > Administration > Printing > Server > Settings: check boxes for the first two items. Do that on the server and the laptop.

---

