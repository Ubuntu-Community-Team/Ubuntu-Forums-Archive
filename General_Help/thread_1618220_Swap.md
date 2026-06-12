---
title: "Swap"
date: 2010-11-10
forum: General Help
---

### Post by Chelidze on 2010-11-10
can any one tell my the commend of how to create a 2 gb swap
 thanks :)

---

### Post by sisco311 on 2010-11-10
Check out:
[uhelp]community/SwapFaq[/uhelp]

---

### Post by Chelidze on 2010-11-10
mmmmmm I seen it but no luck (what can i say i am a nub in linux :() can you write down a commend that will create a 2 gb swap file :)

---

### Post by sisco311 on 2010-11-10
First you have to create a 2GiB file, for example in /mnt:
```
sudo dd if=/dev/zero of=/mnt/swap bs=1M count=2048
```

Then format the file to swap:
```
sudo mkswap /mnt/swap
```

Add the swap file to the system:
```
sudo swapon /mnt/swap
```

Check it out, i.e.:
```
free -m
```

Edit the fstab file:
```
gksu gedit /etc/fstab
```
and add this line at the end of the file:
```
/mnt/swap  none  swap  sw
```

Save the file and exit. That's all. :)

---

### Post by Chelidze on 2010-11-10
Thank you very very very Much :)

---

### Post by sisco311 on 2010-11-10
My pleasure!

---

