---
title: "How to access a passwordless shared folder"
date: 2009-07-15
forum: General Help
---

### Post by Chiuahuadogz on 2009-07-15
How can I access a vista computer's shared folder if it has no password? It is probably really simple... but for some reason I cant figure it out.

---

### Post by HermanAB on 2009-07-15
I don't think you can.

---

### Post by Chiuahuadogz on 2009-07-15
=/ there has to be a way somehow...

---

### Post by 3rdalbum on 2009-07-15
If it's an SMB share, you can go to Places > Network and double-click on Windows Network. The Vista host should appear in the window. If it doesn't, you can try putting "smb://" and then the Vista machine's IP address into the Nautilus location bar. If the share is open to guests or to your username, then you should be able to open it without any prompting for credentials.

---

