---
title: "Can you reproduce HP's ePrint using postfix, etc.?"
date: 2011-08-29
forum: General Help
---

### Post by mwshook on 2011-08-29
HP's [ePrint]("http://h71036.www7.hp.com/hho/us/en/ep/articles/eprint-mobile-printing.html") technology allows its Wifi-enabled printers to work with any wireless device, no drivers needed. Basically, you send an e-mail to your printer's address. If the file is coming from a white-listed address, and the attachment is a valid type (PDF, DOC, JPG, etc.) it will print automatically. This would be really useful for our smartphones and tablets that don't support SMB printing.

I don't have a WiFi enabled printer, but this seems like it would be trivial to replicate on my desktop Ubuntu machine. I would only need to white-list two addresses (mine, and my wife). And I wouldn't need to access it from outside our home network, so I just won't forward the e-mail port. 

Is there a program that replicates this functionality? If not, setting up an e-mail server like postfix or courier doesn't seem like it would be too hard. But how would I get my machine to automatically print the selected file-types? Is there some way to save the attachments to a directory, and have files in that directory automatically print?

Any help would be appreciated.

---

