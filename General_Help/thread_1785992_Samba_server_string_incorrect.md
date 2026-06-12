---
title: "Samba server string incorrect"
date: 2011-06-19
forum: General Help
---

### Post by Cool Javelin on 2011-06-19
Hello fellow Ubuntonians:

I have a 10.04.1 server running Samba.

I have the server string in smb.conf to read... 

server string = Legolas!

yet, when browsing with one of my XP machines I get...

Legolas server (Samba, Ubuntu) (Legolas)

Can someone help me figure out why it is wrong?

A little background, I had this machine running before and it had that string as the default once. I changed the string in smb.conf, but it didn't change in windows. At the time I didn't worry about it.

The server crashed due to a power failure, and I rebuilt it. 

I changed the string in smb.conf before I ever had samba running yet the default string still shows when browsing network neighborhood.

Is it possible it is being set somewhere else?

Thanks, Mark.

---

