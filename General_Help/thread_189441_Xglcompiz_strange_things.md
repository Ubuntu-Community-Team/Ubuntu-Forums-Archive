---
title: "Xgl/compiz strange things"
date: 2006-06-05
forum: General Help
---

### Post by dwarfy on 2006-06-05
Hi everybody...

I have strange things happening with xgl/compiz ..

Each time a new window/panel/menu appears or popups I have a strange message in my /var/log/syslog file :
```

Jun  5 13:43:58 localhost kernel: [4304817.339000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xab460000 for 3768320 bytes
Jun  5 13:43:58 localhost kernel: [4304817.351000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
Jun  5 13:43:58 localhost kernel: [4304817.352000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xd0ba1140 for 3768320 byte
```

I have ubuntu dapper with all updates ....
(last xgl/compiz packages from beerorkid..)

I have Ati X1300 with latest propietary drivers (ubuntu packages)

I don't know if it is really a problem since everything works ok with xgl/compiz, I'm just getting ALOT of messages like the one above...

I don't know if it is the right forum to post this ...
Does anybody have the same errors messages ??

Thank you in advance
Mathieu

---

### Post by kwaanens on 2006-06-05
Me too. Combined with [this]("http://ubuntuforums.org/showthread.php?t=188960").

```
Jun  5 15:18:32 inspiron kernel: [4308223.159000] [fglrx:firegl_pcie_lock_pages]  *ERROR* unlocking pcie memory !
Jun  5 15:18:32 inspiron kernel: [4308223.159000] [fglrx:firegl_pcie_lock_pages]  *ERROR* unlocking memory at 0xf3f23500 for 622592 bytes
Jun  5 15:18:37 inspiron kernel: [4308228.046000] [fglrx:firegl_pcie_lock_pages]  *ERROR* locking memory at 0xa3809000 for 1261568 bytes
Jun  5 15:18:37 inspiron kernel: [4308228.051000] [fglrx:firegl_pcie_lock_pages]  *ERROR* unlocking pcie memory !
Jun  5 15:18:37 inspiron kernel: [4308228.051000] [fglrx:firegl_pcie_lock_pages]  *ERROR* unlocking memory at 0xf3f23300 for 1261568 bytes
```

- Ketil

EDIT: x300 here.

---

### Post by guga1981 on 2006-08-05
Hi!

I get the same messages!!! Weird!

Got an ati x1600!

Guillaume

---

