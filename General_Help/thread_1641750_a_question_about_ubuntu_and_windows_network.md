---
title: "a question about ubuntu and windows network"
date: 2010-12-09
forum: General Help
---

### Post by zarzor_2010 on 2010-12-09
Hi All,

I have a small question about making a network with ubuntu and windows.

I want to make my ubuntu pc as a server. So, I have a windows PC and I want to add a new drive in "my computer" so that this driver will be just my home/username in he ubuntu PC.

Is there any tutorial about how to do that?

Thank you for your help
Thanks
Mina

---

### Post by pricetech on 2010-12-09
Probably.

What you want to do is install Samba and use it.

In Synaptic; search for system-config-samba which will install Samba and a GUI configuration tool which will appear in System - Administration - Samba

Using the configuration tool, change the workgroup name to match your workgroup (just makes browsing easier) then add the share you want.  Make sure you are listed as a Samba user.

On your windows box, you'll need to map the drive and have that mapping persistent.

You can also map with a batch file in case you want the option of connecting to that share only when you need it.

Let us know if you have questions or need help.

---

