---
title: "File system permissions"
date: 2006-02-09
forum: General Help
---

### Post by net_spec on 2006-02-09
Ya I admit,  I have a Linux + cert and I just cant figure this one out. 

Nothing (suspicious) in my logs at all. My filesystem is now owned by root except a few folders. My Home/user is good,, everything works great, no traffic anywhere, everyone looks good in my users/groups. Am I missing something here or is this POT really good. :confused: 

I'm using Ubuntu 5.1

---

### Post by aysiu on 2006-02-09
That's how it's supposed to be.
The user has access to /home
Root owns everything else.

If you need to modify something in another folder via terminal, preface a command with the word *sudo* to temporarily gain root privileges. For example ```
sudo mkdir /usr/local/bin/firefox
```

If you need to modify something graphically then create a launcher or keyboard shortcut for the command ```
gksudo nautilus
```

---

### Post by net_spec on 2006-02-09
I don't remember everything being locked like my /opt dir

I've been studying for my MCSE certs too long I think.

[QUOTE=aysiu]That's how it's supposed to be.
The user has access to /home
Root owns everything else.

---

### Post by aysiu on 2006-02-10
[QUOTE=net_spec]I don't remember everything being locked like my /opt dir

I've been studying for my MCSE certs too long I think.[/QUOTE] Sounds a likely theory.

---

