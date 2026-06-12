---
title: "samba auto startup?"
date: 2006-03-24
forum: General Help
---

### Post by LordMerlin on 2006-03-24
I just installed and configured samba, as per [this link]("http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4")

How do I make it auto start when the server reboots? I don't want to run sudo /etc/init.d/samba start everytime. Any suggestions?

[EDIT]
And how do I start nmbd, without nmbd -D? Isn't there a startup script for it?

---

### Post by ranf on 2006-03-24
By default there is a `/etc/init.d/samba' installed. That is the startup script.
It gets its configuration from `/etc/default/samba'

Have a look at: 
```
less /var/log/messages
```

---

### Post by LordMerlin on 2006-03-24
Ok??? I'm a bit confused as to how this would help me. Though I found another post, relating to something totally different, suggesting to install sysv-conf, or something similar, which seems to have helped. I could simply tell it which services to automatically start, in for which run level

---

### Post by ranf on 2006-03-24
With a default install there already is a startup-script installed. So try a:
```
sudo /etc/init.d/samba restart
```

It should tell you if that's [ok] or [fail]ed.

---

### Post by bongobonga on 2006-03-24
The files in /etc/init.d are scripts which are started automatically when your computer boots up, but depending on the way which your computer starts up they will not all be started. The number and order of the scripts which are started are controlled by something called the run leve. 
First find out the run level by typing  

' grep initdefault /etc/inittab ' 

in a terminal,  and you will get something like 

'id:2:initdefault:' 

This says that my run level is number 2. Using this information check in the directroy '/etc/rc2.d' - replace the number 2 with whatever you got for your run level -  for a file named something like 'S20samba' . The files listed in this directory are the actual scripts that are started at boot up. If this file does not exsist then samba is not being started, Then you will have to create a link to file '/etc/init.d/samba' into the directory '/etc/rc2.d' with a name 'S20samba' 

If the file does exist, then you have bigger problems :(

---

### Post by Buffalo Soldier on 2006-04-01
[QUOTE=bongobonga]Then you will have to create a link to file '/etc/init.d/samba' into the directory '/etc/rc2.d' with a name 'S20samba'[/QUOTE]
How do you create that link?

---

