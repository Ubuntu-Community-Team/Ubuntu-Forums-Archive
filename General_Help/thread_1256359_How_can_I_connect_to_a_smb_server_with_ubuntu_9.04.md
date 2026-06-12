---
title: "How can I connect to a smb server with ubuntu 9.04?"
date: 2009-09-02
forum: General Help
---

### Post by Hoobes1 on 2009-09-02
hi, well the question stands for itself. ^^

all i want to do is connect to our school's student file server, but don't know how. it's name is 

smb://sfs3

so i assume that it's an smb server.

thanks =)

---

### Post by fluffman86 on 2009-09-02
install samba and smbfs and try again.

```
sudo apt-get install samba smbfs
```

Also, try going to Places > Connect to Server... and connecting from there.  Change the drop down menu to samba share.  You may need to enter credentials to access it.  You can find out what to enter from your IT department.

---

### Post by bodhi.zazen on 2009-09-02
You do not need the samba package, that is the samba server.

```
sudo mount -t cifs //server/share /mount/point
```

---

### Post by Whiffle on 2009-09-02
smb://sfs3 

in the address bar of nautilus. Done.

---

