---
title: "Cant Disable Root Account"
date: 2010-06-21
forum: General Help
---

### Post by Gl!tch on 2010-06-21
Hello early today i activated my root account to fix something and now i cant disable it does anyone have any ideas.

---

### Post by sisco311 on 2010-06-21
Hi and welcome to the forums!


Just the lock the root account password:
```
sudo usermod -p '!' root
```

[uhelp]community/RootSudo[/uhelp]

---

### Post by Gl!tch on 2010-06-21
k ive done that but another question when i shut down my computer then turn it back on and when i get to the log in screen do i only have to use my password i made or am i stuck like there.

---

### Post by Zip247 on 2010-06-21
Another way to lock the root user is 

```
$sudo passwd -l root
```

---

### Post by Gl!tch on 2010-06-21
nvm i answered my 2 question thinks very much for the information

---

### Post by Zip247 on 2010-06-21
> when i shut down my computer then turn it back on and when i get to the log in screen do i only have to use my password i made or am i stuck like there.

Use the name and password that you created during install.

---

