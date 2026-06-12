---
title: "PLEASE I NEED HELP - File Sharing"
date: 2010-01-31
forum: General Help
---

### Post by nickmrls on 2010-01-31
ok heres the deal i am using ubuntu 9.10 and im tring to set up a small home file server for my music. so i start by trying the net work tab PLACES > NETWORK and i get as far as WINDOWS NETWORK > WORK GROUP  and it recognises my computer but when i go to try to open it it says "Failed to retrieve share list from server" now i have tried on the sever computer to make a folder that is shared named music and give it the privileges and still nothing. i don't know if the problem is that im going from ubuntu to ubuntu or i know that the netgear router sometimes messes thing like that up. please help!!!

---

### Post by tolanri on 2010-01-31
If you want to share folders/drives over network Ubuntu <=> Windows, install Samba Server. It will allow you your Windows to access your Ubuntu shared folder, printers, etc.

For basic install and adding new folder to share without password prompts (insecure unless you are on LAN behind NAT) do sudo aptitude install samba and then follow this guide:

[http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/](http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/)

---

