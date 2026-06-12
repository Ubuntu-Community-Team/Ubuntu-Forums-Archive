---
title: "A directory we can both access"
date: 2010-03-02
forum: General Help
---

### Post by Linux_Zoo on 2010-03-02
Hi,

I'm running Ubuntu 9.10 and have two users set up: me, and my wife.

I like the different logins because it keeps our desktops unique and files separated, but I want us to share photos.

Can anybody suggest a way to set up a directory, visible in Nautilus from both logins, where we can share photos without permissions headaches?

Ideally I would be able to pull them off the camera and drop them in that directory, log off, log in as her, then open Nautilus and browse the photos. What's more, it would be great if that folder showed up in the lower left pane of Nautilus under the existing "documents" and "pictures" shortcuts.

Thanks.

---

### Post by sisco311 on 2010-03-02
> **Linux_Zoo said:**
> Hi,

I'm running Ubuntu 9.10 and have two users set up: me, and my wife.

I like the different logins because it keeps our desktops unique and files separated, but I want us to share photos.

Can anybody suggest a way to set up a directory, visible in Nautilus from both logins, where we can share photos without permissions headaches?

Enable ACLs support in the partition, create a new group (i.e. photos) & set rw permissions for the group:
```
setfacl -Rdm g:**photos**:rwx **/path/to/dir**
setfacl -Rm g:**photos**:rwx **/path/to/dir**
```


[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport](https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)

> **Linux_Zoo said:**
> What's more, it would be great if that folder showed up in the lower left pane of Nautilus under the existing "documents" and "pictures" shortcuts.

To create a shortcut, simply drag the directory to the left pane.

---

### Post by Linux_Zoo on 2010-03-03
Thanks, I've installed ACL and started through the document you link to. Has taken a while to re-acquaint myself with issuing commands via a console.

---

### Post by sisco311 on 2010-03-03
> **Linux_Zoo said:**
> Thanks, I've installed ACL and started through the document you link to. Has taken a while to re-acquaint myself with issuing commands via a console.

You can use Eiciel a GUI tool to manipulate POSIX ACLs and extended user attributes. It's in the repositories.

[http://www.linux.com/archive/feature/138169](http://www.linux.com/archive/feature/138169)

---

### Post by Linux_Zoo on 2010-03-04
Thanks for your help. Directory is now set up and working.

---

