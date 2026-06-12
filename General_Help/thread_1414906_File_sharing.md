---
title: "File sharing"
date: 2010-02-24
forum: General Help
---

### Post by lemurid on 2010-02-24
Where does Ubuntu 9.10 keep its file sharing configurations? (Those enabled by right clicking a folder and choosing Sharing options)

I thought it was based on samba, but smb.conf doesn't contain any of it...

---

### Post by bab1 on 2010-02-24
> **lemurid said:**
> Where does Ubuntu 9.10 keep its file sharing configurations? (Those enabled by right clicking a folder and choosing Sharing options)

I thought it was based on samba, but smb.conf doesn't contain any of it...

It is based on Samba.  When you use Nautilus to configure the shares the configuration data is stored at [FONT="Courier New"]/var/lib/samba[/FONT].

---

