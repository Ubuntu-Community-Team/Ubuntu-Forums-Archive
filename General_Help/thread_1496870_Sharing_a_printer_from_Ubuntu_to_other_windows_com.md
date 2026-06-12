---
title: "Sharing a printer from Ubuntu to other windows computers"
date: 2010-05-29
forum: General Help
---

### Post by mister_lister on 2010-05-29
I have installed Ubuntu 10.4 LTS and I want to share a printer on that computer with my windows network (mix of XP and Vista). I have network connectivity and and can see other windows computers and they can see me, I am just stumped on how to share a printer on my linux machine with all of the Windows computers on my network. Any suggestions appreciated? 

I have not used Linux in about two years, so newbie instructions are much welcomed.

---

### Post by N8N on 2010-05-29
I believe that you will have to install samba and it wouldn't hurt to install system-config-samba as well (that's the GUI interface that lets you change samba settings)

beyond that, sorry, I can't help because my printer is on an XP machine, I just know that you need samba to share pretty much anything between Linux and Windows.  I suspect that if you have your printer properly configured you will be able to navigate to it from your Windows machine but can't confirm that.

good luck

nate

---

### Post by mister_lister on 2010-05-29
How do I install "system-config-samba" I already have network access and can see both ways but I am not sure how to share my HP printer on my linux machine so other Windows machines can print to it. Additional information required, thanks.

---

### Post by N8N on 2010-05-29
both of those are packages in Synaptic, the system-config-samba package is not automatically installed with samba however (and samba is not installed by default, so you'll have to look up and select both)

nate

---

### Post by finlost on 2010-05-29
I did this earlier in two aught ten.  I think it lasted for all of one, maybe two, printing sessions.  To me, it wasn't worth the additional debugging to fight with it.  

I ended up using Dropbox to transfer documents to the computer that was connected to the printer or just connected directly to the printer with the computer in which I wanted to print from.

Sorry, no help.  :(

[soapbox]Printing and simple home networking need to be improved for Linux/Ubuntu to take the next step in bringing down MS and Mac.  I wish I knew more about networking to help, but I am out of my league with that stuff.[/soapbox]

---

