---
title: "Broke Kernel how to setup linux file."
date: 2006-04-18
forum: General Help
---

### Post by jstad on 2006-04-18
I was following a thread about a HOWTO setup kernel 2.6.16 and it did not work out. I decided to just go back and use the old kernel. However I do not know how to undo this command and get my old linux file back.

sudo ln -s /usr/src/linux-2.6.16ck3 linux

I am trying to setup the linux file back with kernel 2.6.12-10 but I dont see how to do it. This should be a quick fix if someone knows the command. Thanks

---

### Post by /carlito on 2006-04-18
You should issue following commands as root:

cd /usr/src
sudo rm -rf linux
sudo ln -s 2.6.12-10 linux

---

### Post by PriceChild on 2006-04-18
You can then remove the installed kernel package from synaptic

---

### Post by jstad on 2006-04-18
[QUOTE=/carlito]You should issue following commands as root:

cd /usr/src
sudo rm -rf linux
sudo ln -s 2.6.12-10 linux[/QUOTE]

instead of 2.6.12-10 should I change that to:

linux-headers-2.6.12-10
linux-headers-2.6.12-10-386

I am not sure which to do....

---

