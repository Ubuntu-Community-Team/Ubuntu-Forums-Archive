---
title: "How to view local shares? (&quot;net share&quot; in windows)"
date: 2010-05-23
forum: General Help
---

### Post by ingramproductions on 2010-05-23
How do you view local shares from the terminal? I'm basically looking for something that is equivalent to the windows "net share" command.

---

### Post by new_tolinux on 2010-05-23
I don't know if there's a command for it like in Windows, but you can display the contents of /etc/samba/smb.conf to view the shares.

---

### Post by ingramproductions on 2010-05-30
Surely there is a way to view shares from the terminal??
Does anybody know a command that does this?

---

### Post by gmargo on 2010-05-30
Perhaps the **smbtree(1)** command from the **smbclient** package?

---

### Post by capscrew on 2010-05-30
This should do it```

net usershare info
sudo net usershare info
```

---

### Post by loopduplicate on 2011-01-06
This shows all your shares in the terminal:
```
#!/bin/sh
# list all shared folders
shares=$(ls -l /var/lib/samba/usershares | awk '{print "/var/lib/samba/usershares/"$8}')
for i in $shares
do
cat $i | grep path
done

```And this unshares all folders at once if you need to secure things fast:
```
#!/bin/sh
# unshare all folders
shares=$(ls -l /var/lib/samba/usershares | awk '{print $8}')
for i in $shares
do
net usershare delete $i
done

```

---

