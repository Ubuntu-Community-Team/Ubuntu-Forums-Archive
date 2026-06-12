---
title: "sudo doesn't work"
date: 2006-03-23
forum: General Help
---

### Post by Gujs on 2006-03-23
Hello,

I changed hostname from home1 to home3 with command:

```
sudo hostname home3
```

and rebooted.

Now sudo says

```
sudo: unable to lookup home3 via gethostbyname()
```

I don't have access to this computer, i can acces it only through network.
What can i do now?

Thanks

---

### Post by akiro.yamamoto on 2006-03-23
Check these files:
/etc/hostname and /etc/hosts (see my PICS)
Ensure your info is correct...
BTW: my hostname is badger ;) just for reference....

---

### Post by Gujs on 2006-03-23
I know that,

but i cannot get fisicaly to the computer.

So i can't get into rescue mode to change the hosts file.

Hov can i change it remotely, if it even can!

THanks

---

### Post by frodon on 2006-03-23
If you can't use the rescue mode just use a live cd.

---

### Post by Gujs on 2006-03-23
I can get to the computer, that is why i can't do it.

Can it be done remotely through ssh!

---

