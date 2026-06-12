---
title: "sudo problem"
date: 2006-03-27
forum: General Help
---

### Post by wizzkid on 2006-03-27
Hi! I have a problem with sudo command. below are the outputs.

wizzkid@:~$ sudo -v
sudo: unable to lookup  via gethostbyname()
wizzkid@:~$

Here's my /etc/hosts:
127.0.0.1 localhost.localdomain localhost nultech

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Before this happend, my konsole prompt was wizzkid@nultech:~$.. i dont know what went wrong. IF my memory serves me right, the last thing i did was to activate or set the password for su. 

Currently, my synaptic and other administration program does not work, unless I manually enter at konsole sudo synaptic, it does work but goves me this message 

wizzkid@:/etc$ sudo synaptic
sudo: unable to lookup  via gethostbyname()

(synaptic:8720): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8720): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed


Help please.

---

### Post by Barrakketh on 2006-03-27
Check your /etc/hostname file and make sure it has "nultech" in it (no quotes).

If not, you'll need to boot into recovery mode and edit the file to ensure that it has it in it.

---

### Post by codejunkie on 2006-03-27
[QUOTE=wizzkid]Hi! I have a problem with sudo command. below are the outputs.

wizzkid@:~$ sudo -v
sudo: unable to lookup  via gethostbyname()
wizzkid@:~$

Here's my /etc/hosts:
127.0.0.1 localhost.localdomain localhost nultech

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Before this happend, my konsole prompt was wizzkid@nultech:~$.. i dont know what went wrong. IF my memory serves me right, the last thing i did was to activate or set the password for su. 

Currently, my synaptic and other administration program does not work, unless I manually enter at konsole sudo synaptic, it does work but goves me this message 

wizzkid@:/etc$ sudo synaptic
sudo: unable to lookup  via gethostbyname()

(synaptic:8720): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8720): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed


Help please.[/QUOTE]
edit the hosts file and make it look like this
```

127.0.0.1	localhost
127.0.1.1	nultech

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
if you can't edit the file as root, here is a couple of things you can try that will let you.

1: reboot and at the grub menu choose (recovery mode) when you get into the terminal run ```
[COLOR="Blue"]nano /etc/hosts[/COLOR]
``` [COLOR="Blue"]make the changes and save the file by pressing ctrl+x then reboot by entering ```
reboot
```[/COLOR]
or

2: insert the ubunut install cd at the boot menu enter ```
rescue
``` follow the instructions when you get to the terminal run the steps in blue from the above post.

3: if you have a ubuntu live cd around boot using the live cd, when you get into the live enviorment open a terminal and run ```
sudo fdisk -l
```find your ubuntu partition it should be listed something like 
```
/dev/hdb2             183        2589    19334227+  83  Linux
```
then mount it like this ```
sudo mkdir /ubuntu
```then
```
sudo mount /dev/hdb2 /ubuntu
```replace **/dev/hdb2** with your partition location, now run 
```
sudo nautilus /ubuntu
```now you can just navigate to the /etc/hosts file and double click on it and edit it with gedit.

sorry for the long post, but i hope one of these helps.

---

### Post by wizzkid on 2006-03-27
Here's my host

#127.0.0.1 localhost.localdomain localhost nultech
127.0.0.1       localhost
127.0.0.1       nultech

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I tried to check my /etc/hostname.. its empty. 

Can you guys tell me what inside the hostname? or could you show me your /etc/hostname ?:)

Thanks

---

### Post by codejunkie on 2006-03-27
[QUOTE=wizzkid]Here's my host

#127.0.0.1 localhost.localdomain localhost nultech
127.0.0.1       localhost
127.0.0.1       nultech

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I tried to check my /etc/hostname.. its empty. 

Can you guys tell me what inside the hostname? or could you show me your /etc/hostname ?:)

Thanks[/QUOTE]
mine says```
ubuntu
```which is my hostname.

since your orginal hostname was **nultech** just add ```
nultech
``` to /etc/hostname and save the file.

---

### Post by wizzkid on 2006-03-27
Problem solved on hostname :)

Thanks a lot. :D

---

