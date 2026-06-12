---
title: "Restarting Gnome from thumb drive ?"
date: 2010-06-07
forum: General Help
---

### Post by Ububtubobl on 2010-06-07
My system crashed when I tried to boot to KDE. I would like to restart Gnome. Can this be done from a Live USB? 
Thanks

---

### Post by drpjkurian on 2010-06-07
hi
Boot in the terminal mode and type the command
```
startx
```

---

### Post by Ububtubobl on 2010-06-07
> **drpjkurian said:**
> hi
Boot in the terminal mode and type the command
```
startx
```


"user not authorized to run the x sever." was response, so tried
"sudo/startx" , got back "no such file or directory".

---

### Post by drpjkurian on 2010-06-08
> **Ububtubobl said:**
> "user not authorized to run the x sever." was response, so tried
"sudo/startx" , got back "no such file or directory".

Hi
First type the command
```
sudo -i
```

Enter your password

then type the command
```
startx
```

---

