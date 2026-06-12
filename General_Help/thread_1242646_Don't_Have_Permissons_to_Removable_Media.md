---
title: "Don't Have Permissons to Removable Media"
date: 2009-08-17
forum: General Help
---

### Post by Bradj47 on 2009-08-17
I use sudo and everything. How do I get this command to work?
```

brad@rockstar:~$ sudo cat /usr/lib/syslinux/mbr.bin > /dev/sdc
bash: /dev/sdc: Permission denied
brad@rockstar:~$

```
sdc is a 4 GB flash drive.

---

### Post by JohnFH on 2009-08-17
Try this instead: 
```

cat usr/lib/syslinux/mbr.bin | sudo tee /dev/sdc

```

---

### Post by Bradj47 on 2009-08-17
> **JohnFH said:**
> Try this instead: 
```

cat usr/lib/syslinux/mbr.bin | sudo tee /dev/sdc

```


```

brad@rockstar:~$ cat /usr/lib/syslinux/mbr.bin | sudo tee /dev/sdc
&#65533;&#65533;s&#65533;|&#65533;&#65533;f&#65533;&#65533;&#65533;B&#65533;Z&#65533;&#65533;&#65533;?Q&#65533;&#65533;@&#65533;&#65533;RPf1&#65533;f&#65533;&#65533;f&#65533;!Missing operating system.
f`f1&#1211;|fRfPSjj&#65533;&#65533;f&#65533;6&#65533;{&#65533;&#65533;&#65533;&#65533;&#65533;Œ&#65533;6&#65533;{&#65533;&#65533;A&#65533;&#65533;&#65533;{&#65533;&#65533;&#65533;fa&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;f`&#65533;&#24318;&#65533;1&#65533;SQ&#65533;&#65533;t@&#65533;&#1923;&#65533;&#65533;&#65533;Ht[y9Y[&#65533;G<t$<u"f&#65533;f&#65533;Vf&#65533;f!&#65533;uf&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;f&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;fa&#65533;&#65533;bMultiple active partitions.
f&#65533;fFf&#65533;&#65533;0&#65533;r&#65533;>&#65533;}U&#65533;&#65533;&#65533;&#65533;&#65533;{Z_&#65533;&#65533;&#65533;&#65533;Operating system load error.
^&#65533;&#65533;&#65533;>b&#65533;&#65533;<
u&#65533;&#65533;&#65533;&#65533;brad@rockstar:~$ 

```
Um...

---

### Post by JohnFH on 2009-08-17
Are you trying to install syslinux bootloader on the USB drive?  If so, then just do it like this:
```

sudo syslinux /dev/sdc

```
Then mount /dev/sdc and check the contents.  It should now include an ldlinux.sys file and it should be bootable.

---

