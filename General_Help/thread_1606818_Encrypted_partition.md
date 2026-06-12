---
title: "Encrypted partition"
date: 2010-10-27
forum: General Help
---

### Post by TNT1 on 2010-10-27
Ok, so I want to access my home folder on another partition... I have kubuntu 10.10 and Ubuntu 10.04.1, dual booting. I am in ubuntu now, and want to get a doc out of my home folder in the kubuntu partition. I access the partition, locate /home, open it and there's this icon called "Access-Your-Private-Data.desktop"

I click on it, and I get: 

The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

And a cancel button...How do I open it?

---

### Post by TNT1 on 2010-10-27
Am I the only person who has ever seen this?

---

### Post by ironic.demise on 2010-10-27
open it in terminal?

---

### Post by marin123 on 2010-10-27
thats similar to shorcuts created by wine.. try right-click, properties, permissions, allow file to be executed as a program...

---

### Post by TNT1 on 2010-10-27
> **ironic.demise said:**
> open it in terminal?


Same error...

---

### Post by TNT1 on 2010-11-01
I know it's frowned upon, but, Monday morning bump.

---

### Post by HiImTye on 2010-11-01
right click on it and select properties
go to permissions
check 'execute' for owner (make sure youre listed as the owner)

---

### Post by TNT1 on 2010-11-01
> **HiImTye said:**
> right click on it and select properties
go to permissions
check 'execute' for owner (make sure youre listed as the owner)

I can't.... It is an encrypted home folder in a dual boot partition, If I am logged into the other boot partition, I can never be the "owner" of the folder in question, can I?

---

### Post by HiImTye on 2010-11-01
you can always chown it, if you are able to view it and access it then you can change ownership

```
sudo chown user /path/to/file
```

---

### Post by TNT1 on 2010-11-01
Ok, maybe my question should be, how do I use what is presented without resorting to chown/changing permissions etc?
[URL="http://img248.imageshack.us/img248/582/screenshotta.png"][IMG]http://img248.imageshack.us/img248/582/screenshotta.png[/IMG]
[/URL]

---

### Post by TNT1 on 2010-11-01
And then:
```
jason@Asterix:~$  ecryptfs-mount-private
jason@Asterix:~$ sudo  ecryptfs-mount-private
[sudo] password for jason: 
Enter your login passphrase:
Inserted auth tok with sig [7a38558b5fa17a24] into the user session keyring
fopen: No such file or directory
jason@Asterix:~$ 
```

---

### Post by HiImTye on 2010-11-01
I thought about the easiest to explain way to do this and this is what I've come up with.

[LIST=1]
[*]create a new user. you can do this from system > administration > users and groups
[*]navigate to the /home/ folder on that drive
[*]right click on the users folder inside that folder and select 'create link'
[*]delete your new users' home folder
[*]cut the link you created and paste it inside your /home/ folder
[*]rename it to the new users' name
[*]log in to that new user
[/LIST]
if this doesn't work then all you need to do is delete that new user and you're no worse off. I dont use an encrypted folder, myself, but I imagine you could link the /.Private or whatever folder (if you choose view > show hidden files) and then run that command but this assumes you don't have an encrypted home folder right now.

---

### Post by HiImTye on 2010-11-01
any luck with this?

---

