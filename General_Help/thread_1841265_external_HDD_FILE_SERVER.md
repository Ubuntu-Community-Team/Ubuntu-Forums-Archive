---
title: "external HDD FILE SERVER"
date: 2011-09-09
forum: General Help
---

### Post by Gargintua on 2011-09-09
i dont want a dedicated server computer.
im using my casual desktop pc and leaving it on 24/7

i dont want to use my computer's hdd for the server.
i want to use my external hdd for my server

how do i make an easy home file server(much like windows homegroup)
and use my external HDD?

Samba? apache? filezilla? gnome built in? windows workgroup? which one is suited for me?

---

### Post by Wim Sturkenboom on 2011-09-09
What's the OS on the server? What kind of clients (Windows, Linux, Mac).

If windows PCs are involved at the client side and the server is Linux, samba is the way to go (in my opinion) for proper sharing.

---

### Post by Gargintua on 2011-09-09
thank you so much for your response

im running ubuntu on my computer (server computer)
my family are the clients and they run mostly windows but sometimes ubuntu

so samba sounds good (if it could connect my external HDD to teh server). i tried to setup samba, but only i could see the shared folder (lol i hate all the terminal configuration.

---

### Post by egalvan on 2011-09-09
> **Gargintua said:**
> 
so samba sounds good (if it could connect my external HDD to teh server).
Samba can connect and share any file that the OS can "see"..

>  i tried to setup samba, but only i could see the shared folder 
yes, you need to specifically share everything you want to share...
if you want to see a whole drive, then you must specify the whole drive...


> (lol i hate all the terminal configuration.

then try Simple Sharing...

oepn a Nautilus window that shows the drive or folder you want to share...

if its a folder, right-click and choose "share options"..
follow the prompts

if its a drive, choose "properties", then the "share" tab..
again follow the prompts...

Simple.

---

### Post by Gargintua on 2011-09-09
alright thank you for your reesponse <333
ill give it a go, thread solved :D

---

