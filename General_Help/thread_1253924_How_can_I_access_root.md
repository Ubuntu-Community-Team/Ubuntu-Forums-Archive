---
title: "How can I access root?"
date: 2009-08-30
forum: General Help
---

### Post by Snowyfox12 on 2009-08-30
So I got ubuntu and my problem is that I don't know how I can get to root
Help!
I tried this way:
1.log off
2.wrote root
3.also wrote root
and It dosen't let me access Root

---

### Post by credobyte on 2009-08-30
Execute command with root privileges:
```
sudo <command>
```

Simulate root ( privileges for the entire session ):
```
sudo -i
```

---

### Post by snowpine on 2009-08-30
Welcome to the forums!
There is no "root account" in Ubuntu; it is locked for security reasons. We use sudo instead to temporarily gain root priviledges.

Here is more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pedro3005 on 2009-08-30
LOGGING AS ROOT IS NOT RECOMMENDED! Use a terminal and sudo to do anything with root privilegies.

---

### Post by theozzlives on 2009-08-30
to gain root access, you use sudo. Example:
```
sudo <command>
```

---

### Post by scouser73 on 2009-08-30
Go to **Terminal**, copy & paste this command:  **gksudo nautilus**

That will get you in as Root, please be [COLOR="Red"]**_very careful_**[/COLOR] when using root.

---

### Post by uylug on 2009-08-30
I always use

```
sudo bash
```

---

