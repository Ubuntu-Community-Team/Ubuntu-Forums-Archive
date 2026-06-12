---
title: "print share inaccessable, permission denied..."
date: 2010-02-25
forum: General Help
---

### Post by switch10 on 2010-02-25
I have a DLink 323 NAS with a USB port for a printer.  Im trying to setup the printer.  When I get to the part where I have to enter the username and password for the NAS, no matter what I put in for a password and username, I get the same error message (see attached screenshot).  

I can not get my network printer to work because of this.

Any ideas?

Thanks

Dave

---

### Post by davec64 on 2010-02-25
Just a thought, Is the NAS box sharing the printer via SMB?
What does the NAS documentation say about this?
As an alternative have you tried using the Intenet Printing Protocol? Although my NAS box isn't a D-Link that's how it shares the printer. So in your case the URL for the printer would be something along the lines of:

```
http://<IP Address>:631/printer
```

(:631 is the default port number)

Give that a go and see what you get. You can decipher the URL by typing the first part into a web browser (minus the /printer). That will fire up CUPS if it is being used by the Print Server.

Hope that helps!  :)

---

### Post by davec64 on 2010-02-25
I also found this link if it's any use:

[http://forum.dsmg600.info/t1775-HOWTO:-GDI-Printers-DNS-323.html]("http://forum.dsmg600.info/t1775-HOWTO:-GDI-Printers-DNS-323.html")

Best of luck!  :)

---

### Post by switch10 on 2010-02-25
Thanks for the fast response!!  :)  

The documentation just shows how to configure the print server in Windows...  It doesn't say if it uses SMB or not.  I'm assuming it does.  

I tried using the Internet Protocol Printing that you suggested, no go.

---

### Post by mdimock on 2010-02-25
Maybe the problem isn't the  the printer it's Ubuntu:-k. Ubuntu doesn't always work with printers  such as Lex mark. I could be wrong. This is from personal experience. I don't know the results. Or what you could do is do some research on the printer you are using.

---

### Post by switch10 on 2010-02-25
> **mdimock said:**
> Maybe the problem isn't the  the printer it's Ubuntu:-k. Ubuntu doesn't always work with printers  such as Lex mark. I could be wrong. This is from personal experience. I don't know the results. Or what you could do is do some research on the printer you are using.

Thanks for the response, but I have an HP and it works great when I plug it in directly...

any other ideas??

I might grab a buddies computer that is running Windows, and see if I can pick up some clues from that...

---

### Post by davec64 on 2010-02-26
That link I posted mentioned firmware for an HP (I think!) that the NAS box requires if it isn't in it's list of printers.

I hope you manage to sort it!

---

### Post by switch10 on 2010-03-05
I had to install the driver on the NAS.  Works great now!

---

