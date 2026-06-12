---
title: "Ubuntu asks for password which is disabled"
date: 2011-10-21
forum: General Help
---

### Post by CrystalMV on 2011-10-21
I was messing around with account settings. When I noticed that password can be disabled, I thought I'd give it a try. However, there's a problem now: whenever I want to do something like installing programs, I can't because Ubuntu still asks for password and it doesn't exist. I can't enable it because that needs authentication too. How to solve this problem?

---

### Post by bryncoles on 2011-10-21
Hi CrystalMV. 

Let's try resetting the password, shall we?

First up, reboot your computer.  When you get to the GRUB boot-loader (where it asks what operating system to load) select 'recovery mode.  type ```
ls /home
``` to get your user name.  now you should be able to type your username and a new password (or it might be a password and username, I can't remember which way round it goes).  

Did that help?

---

### Post by dave01945 on 2011-10-21
when you know your username you just type (Do this in recovery mode like the previous poster suggested)

```
passwd user
```

and then it will ask you to enter a new password replace user for your actual username

---

### Post by CrystalMV on 2011-10-21
It works! Thank you!

---

### Post by bryncoles on 2011-10-21
we're happy to help!

---

