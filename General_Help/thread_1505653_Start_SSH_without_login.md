---
title: "Start SSH without login"
date: 2010-06-09
forum: General Help
---

### Post by faithfracture on 2010-06-09
Does someone know how I can start ssh-server when my machine starts up without having to log in? I thought this happened by default, but either it doesn't or something got goofed up in my system. SSH works just fine if the remote machine is logged in to a user account, which is fine in most cases unless I need to reboot the machine (more often than not).

Thanks.

---

### Post by DouglasK on 2010-06-09
Your profile doesn't specify what flavour of Ubuntu you're using.  So I'm gonna take a guess and say you're using the Ubuntu Desktop installation.   

Most likely, your network is not coming up until you login.  I'm assuming that you have a wired connection to your network and that you use DHCP to get your network address.  Most networks do this.

Here's how to make your network come up at boot instead of login:

[LIST=1]
[*]open a run prompt by pressing **Alt+F2**
[*]Type "gksu gedit /etc/network/interfaces" (without the quotes) into the prompt and click "Run".
[*]in the text editor, add a blank line at the bottom, then type these two lines:
```
auto eth0
iface eth0 inet dhcp
```
[*]Save the file and close the text editor.
[/LIST]
Best regards,[INDENT]Douglas K
[/INDENT]

---

### Post by faithfracture on 2010-06-12
Ah ha! Great, thanks.

My network is a little complicated, and my machine needs a static IP assigned to it, but setting up my network configuration via interfaces fixed it. I had forgotten that let gnome-network-manager take care of all that for me and it didn't occur to me that gnome-network-manager wouldn't start until I logged in. Once I removed the network entry in the network manager and manually set it up (and set my DNS nameserver in resolve.conf), everything works perfectly now.

Thanks a bunch!

---

