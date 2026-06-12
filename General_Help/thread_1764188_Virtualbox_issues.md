---
title: "Virtualbox issues"
date: 2011-05-21
forum: General Help
---

### Post by agarner98 on 2011-05-21
I think this photo should be pretty self explanatory. What do I need to do to fix this? I'm developing an OS and need VirtualBox to start linux Mint today.

The error says: Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

---

### Post by howefield on 2011-05-21
What photo ?

Try opening up Ubuntu Software Centre or Synaptic Package Manager and install the package.. 

```
virtualbox-ose-dkms
```

Once that is done, open a terminal and as advised in your error, issue the command

```
sudo modprobe vboxdrv
```

---

### Post by Mr. Shannon on 2011-05-21
Or if you want a gui then install
```
virtualbox-ose-qt
```
that should grab everything you need.

---

