---
title: "mounting smb share"
date: 2010-06-03
forum: General Help
---

### Post by warri0r on 2010-06-03
i have a smb share on ubuntu machine, how can i access this from another ubuntu machine. i tried mounting the share but no gain! i could access the share from windows xp which was installed under virtualbox of the same machine where the smb share is present. am i confusing ?

---

### Post by mittwit on 2010-06-03
I'm using ubuntu 9.10 and using the GUI I click on places > then select "Connect to Server" In the pop up box select "Windows Share" for service type. Enter the computer name or ip in the server field. The other fields are optional. You then may need to give a share name and login details. I use this process to access shared folders on ubuntu machines from other ubuntu machines. Sorry I can't give you a command line option.

---

### Post by warri0r on 2010-06-03
thanks dude, i could access the share by ur method. :)

but i m just curious why is tat i cant mount the share, this is wat i got for the mount operation,

when i press tab, i could see the shares:

```
sudo mount -t smbfs /mnt/smb/ //nemesis/
nemesis/  IPC       music     print     public
```  

choosing the share gives an error,
```
sudo mount -t smbfs /mnt/smb/ //nemesis/public/
mount error: improperly formatted UNC name. /mnt/smb/ does not begin with \\ or //
No ip address specified and hostname not found
```

any idea folks?

---

### Post by warri0r on 2010-06-05
**Bump** :D

---

### Post by warri0r on 2010-06-09
*bump* still no clue! any idea?

---

### Post by KenSharp on 2010-06-09
It couldn't be any clearer.
> mount error: improperly formatted UNC name. /mnt/smb/ does not begin  with \\ or //You haven't used the command correctly.

**sudo mount -t smbfs //nemesis/public /mnt/smb/** is what you want.

---

### Post by warri0r on 2011-01-20
> **KenSharp said:**
> It couldn't be any clearer.
You haven't used the command correctly.

**sudo mount -t smbfs //nemesis/public /mnt/smb/** is what you want.

i look like a stupid now. thanks dude

---

