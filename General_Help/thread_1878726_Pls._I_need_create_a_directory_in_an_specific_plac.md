---
title: "Pls. I need create a directory in an specific place"
date: 2011-11-10
forum: General Help
---

### Post by xavi fernandez on 2011-11-10
Hi all
I need create a folder or directory called keys here: etc/openvpn must be inside the folder open vpn that is located in file systems/etc/openvpn but I'm not idea how I know how create a normal one, with mkdir whatever and directory whatever will be inside the home folder, but open a directory in this other place... I'm not sure and I don't want mess up.
I'm really new on it, I'm running ubuntu 11.10

Thanks in advance

---

### Post by Topsiho on 2011-11-10
You mention mkdir and "whatever", so need not be told about that. You can only do that in your own /home folder, however, as you "own" it.

If you need to do this somewhere else in the system, you need to be root, so you should use sudo:

sudo mkdir ... and are asked for your password. I assume here that it's your password that was entered during the install of Ubuntu.

Topsiho

---

### Post by carranty on 2011-11-10
Since it's in your root directory and not your home directory you'll need superuser access. You get this by writing 'sudo' in front of the mkdir command

[I]sudo mkdir /etc/openvpn/keys

[/I]should do it.  It will ask for your password, just enter it at the prompt and press enter.

---

### Post by xavi fernandez on 2011-11-10
Thanks Topsiho and thousands thanks to carranty, you just told what I need, the command for make it, and now I have my folder there, so I can configure the VPN!!!

Thanks a lot again!!!!

---

