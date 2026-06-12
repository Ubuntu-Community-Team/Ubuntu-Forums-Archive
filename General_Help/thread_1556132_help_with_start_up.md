---
title: "help with start up"
date: 2010-08-19
forum: General Help
---

### Post by cowboy7305 on 2010-08-19
when i start up my computer a screen comes up with the os i have on computer which are Ubuntu 10.04 AND  WINDOWS 7
when i start up i have to arrow up or down to which os i want to load and i have to do it with in 10sec or it loads ubuntu  can i stop it from loading any thing until  i am ready,i have a bad habit of firing up computer then walking away  any help please

---

### Post by nbkr on 2010-08-19
[LIST=1]
[*]Edit the file /etc/default/grub with "gksudo gedit /etc/default/grub"
[*]Find the line that starts with "GRUB_TIMEOUT"
[*]Change the valule from 10 to -1 (that's minus one not minus L)
[*]Run the command "sudo update-grub" in a terminal.
[/LIST]

---

### Post by wilee-nilee on 2010-08-19
> **cowboy7305 said:**
> when i start up my computer a screen comes up with the os i have on computer which are Ubuntu 10.04 AND  WINDOWS 7
when i start up i have to arrow up or down to which os i want to load and i have to do it with in 10sec or it loads ubuntu  can i stop it from loading any thing until  i am ready,i have a bad habit of firing up computer then walking away  any help please

Assuming you have grub2 follow this information to edit grub.
> GRUB_TIMEOUT="10" specifies the default timeout. Change to anything you want. Very small values are not recommended. Setting to -1 will make GRUB wait indefinitely until you manually select an entry and hit Enter.

With this command to edit grub then run sudo update-grub after saving.
```
gksudo gedit  /etc/default/grub
```


Edit: Doh, same as post 2.

---

### Post by anirudhtomer on 2010-08-19
you can change that timer. There is a file /boot/grub/grub.cfg [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

there is one line set timeout = 10 

change that time out to any other value or even remove that timeout thing & have no timeouts & even you can set which OS should be booted by default after timeout.

another way is to go via GUI. I am sitting on my Windows OS now and I don't remember exactly where you get it but its in System/Preferences I think.

---

### Post by cowboy7305 on 2010-08-19
Many thanks 
worked a treat

---

