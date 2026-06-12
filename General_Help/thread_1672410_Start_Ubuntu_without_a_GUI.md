---
title: "Start Ubuntu without a GUI?"
date: 2011-01-20
forum: General Help
---

### Post by aflyingturtle on 2011-01-20
I'm currently using Ubuntu to host a minecraft server on a very old computer. I was wondering if there was a way that I could start Ubuntu without the GUI so it would run better. Is there?

---

### Post by Iowan on 2011-01-20
There is a server version that comes without a GUI by default, but since you already have Ubuntu installed...
You might need to reconfigure some things before you disable the GUI (did you configure networking via Network Manager?).

---

### Post by James78 on 2011-01-20
I think you can get the desired effect by using "sysv-rc-conf" or "chkconfig" (or was it checkconfig?). Just unselect gdm or kdm. I'm not entirely sure, but I think this will do it for you.

---

### Post by psusi on 2011-01-20
Add "text" to the kernel command line.  You can do it one time by pressing 'e' at the grub prompt to edit the boot entry.

---

### Post by James78 on 2011-01-20
> **psusi said:**
> Add "text" to the kernel command line.  You can do it one time by pressing 'e' at the grub prompt to edit the boot entry.
Even better solution. :D

---

### Post by aflyingturtle on 2011-01-20
And the command to then start the gui is startx right?

---

### Post by Hatsune Miku on 2011-01-20
> **aflyingturtle said:**
> And the command to then start the gui is startx right?

Yes ^-^

```
startx
```

if that doesnt work (sometimes it gets DURPEH)
do is ;3

```
startx /usr/bin/startgnome
```

---

### Post by aflyingturtle on 2011-01-20
> **James78 said:**
> Even better solution. :D

So I press E at grub... And where in the text entry to I put text?

---

### Post by psusi on 2011-01-21
> **aflyingturtle said:**
> So I press E at grub... And where in the text entry to I put text?

Add it to the end of the linux line.  You might also want to remove the quiet and splash options.

---

### Post by aflyingturtle on 2011-01-21
Thanks... How do I connect to the wireless network from terminal?

---

### Post by James78 on 2011-01-23
Something along these lines...
```
sudo wpa_passphrase <router name> > config_file
<enter password at stdin prompt>
sudo wpa_supplicant -iwlan0 -cconfig_file -B
sudo dhclient
```

---

