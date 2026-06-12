---
title: "samba4"
date: 2010-02-07
forum: General Help
---

### Post by spiky001 on 2010-02-07
Hi i have just downloaded samba 4 via package man is there a gui interface for it, or did i not download all i need hope this makes sense

---

### Post by spiky001 on 2010-02-07
bump

---

### Post by spiky001 on 2010-02-07
anybody?

---

### Post by spiky001 on 2010-02-13
bump

---

### Post by RedRat on 2010-02-13
You're running 9.10 but in 8.04 Gnome you can install smb4k, which is a gui for KDE, but it runs in gnome too. I use this for mounting network drives. 9.10 might not have this particular program. Search Synaptic for it.

---

### Post by spiky001 on 2010-02-13
thks just downloading it now

---

### Post by Morbius1 on 2010-02-13
Unless there have been some fundamental changes since I used it last, smb4K is a client software used to access another box's shares. Samba is a Server software used to create shares on your own box for others to access.

Does **shares-admin** no longer work with Samba4?

---

### Post by RedRat on 2010-02-13
> **Morbius1 said:**
> Unless there have been some fundamental changes since I used it last, smb4K is a client software used to access another box's shares. Samba is a Server software used to create shares on your own box for others to access.

Does **shares-admin** no longer work with Samba4?

Well yes, but I use Thunar as my windows explorer and I find that when I use smb4k, it allows me to see those mounted drives on my Windows Computer. For me, I found it convenient, but maybe there is a better way. I use 8.04 and perhaps things are different for 9.10.

---

### Post by Morbius1 on 2010-02-13
My point wasn't that smb4K is a bad thing it's just that the original poster downloaded Samba4. smb4K isn't dependant on samba it's dependant on smbclient. I'm assumming he's downloaded Samba because he wants to share his folders to others on his network. smb4K isn't going to help him with that.

---

