---
title: "print to pdf.. over network"
date: 2011-11-13
forum: General Help
---

### Post by conradin on 2011-11-13
Hi all,
I want to set up a way that poeple can print pdfs to a shared folder on my desktop. How do I get this done?

---

### Post by gennatolls on 2011-11-14
> **conradin said:**
> Hi all,
I want to set up a way that poeple can print pdfs to a shared folder on my desktop. How do I get this done?

You might try samba, here s a really good guide to get it setup easily 
[http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)
Once you have that properly configured, just use the "print to file" option in the print dialog box and choose your samba share.

I prefer ssh, way easy and it just works. howtogeek.com also has a good ssh tutorial

---

### Post by conradin on 2011-11-17
I was thinking to assign an ip to a virtual printer. 
ssh tools might be available to windows users, but most MS users 
dont know how to use them. Ill have a look at the tutorial.

---

### Post by conradin on 2011-11-19
Ok, I am not sure about setting up samba. I want anyone to be able to print to my virtual (PDF) printer provided they only know my ip and share name. the poeple I want to print to my computer will be on subnets outside my network, and will not have user accounts on my computer. How should i hook that up?

(the bit about the security settings is confising me, given i want everyone to be able to write to my share, which authentication mode should i use?)

---

### Post by Synoc on 2011-11-20
You could set up a shared file, on your desktop and simply share that out with smb protocol. I am using 10.10, so it should work the same. I just have to create a folder and tell it to share that folder over the network. it installs the services and I'm up and running, then it's just a question of pointing other users on Windows PCs to that folder. A simple enough matter as long as their firewall has file and print sharing on.

---

### Post by conradin on 2011-11-20
Hi Synoc, 
Thanks for the reply, I was actualy just thinking about that. I just thought it would be neat to use the print option for poeple to submit thier documents to my share and have them come out as PDFs.

---

### Post by Synoc on 2011-11-20
the caveat to that is Windows does not print to PDF natively as GNU/Linux does. so ultimately OOo or LOo would have to convert it and it would have to be sent to a network share (that folder for example) or anyone with a windows machine. 

There is an open source program called PDF creator that will allow the printing to PDF. But I have discovered that, at least with my linux box, a standard Windows computer cannot read those PDFs without Sumatra PDF. it's possible the encoding is different, but Adobe Reader will not read my Linux-created PDF from printing.

---

### Post by conradin on 2011-11-21
hmm, I was starting to suspect something about a print pdf drver issue, after i verified my method on a usb printer I have. 
Agian, I am disapionted with windows, and Im not even trying to use it, only recognising my users will use it. Face+palm. Then again
pdfcreator is one of my favorite Open-source projects, Im not enitirely opposed to recomending it to poeple

---

