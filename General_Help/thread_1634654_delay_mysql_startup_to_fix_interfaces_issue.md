---
title: "delay mysql startup to fix interfaces issue?"
date: 2010-11-30
forum: General Help
---

### Post by SonicComKid on 2010-11-30
I have a Ubuntu server installed however I find I have to keep manually running mysql after a reboot.

After reading through some posts about similar issues I think I worked out what's wrong. But don't know how to fix it.

I have the proper mysql script in my ../init.d dir and a symlink in my rc2 dir, but I think the issue is that mysql fails to start because I have a special entry in my interfaces settings due to that my ubuntu server is also a network bridge.

This is what's in my interfaces config:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
##auto eth1
##iface eth1 inet dhcp

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0

```

I have bridge utilities installed on the server to link two NIC cards together.

Does anyone know how I can get mysql to work? The only solution I can think of is me delaying the startup of mysql somehow to see if that does any good. Otherwise I'm not sure what else might resolve this.

---

### Post by DaithiF on 2010-12-01
take a look at 
/etc/init/mysql.conf

change the line that says 
```
start on (net-device-up
```
to
```
start on (net-device-up IFACE=eth0
```

that should cause mysql to wait until eth0 is up, rather than just any interface (ie. bridge).

---

### Post by SonicComKid on 2010-12-01
It seems I don't have a /etc/init/mysql.conf file.
I have the typical stuff in /etc/mysql/ but in /etc/init/ there's a handful of items but none for mysql.

Would this value be kept somewhere else?

---

### Post by DaithiF on 2010-12-02
what version of ubuntu server are you on?  Did you install mysql from the repos?
and what does ls -l /etc/init.d/mysql give?

---

### Post by SonicComKid on 2010-12-02
I installed Ubuntu server edition. I honestly can't remember which version it is any more. The uname -a output is: Linux zair-server 2.6.31-22-generic-pae #68-Ubuntu SMP Tue Oct 26 16:52:34 UTC 2010 i686 GNU/Linux

Also the output of the command you gave me is:
-rwxr-xr-x 1 root root 5917 2009-09-09 11:31 /etc/init.d/mysql

mysql runs just fine if I do the: sudo /etc/init.d/mysql start
command. But the autostart won't work and I think it's because of the bridge virtual network interface loading up after mysql fails to find the right network adapter.

Edit: oh, and I installed it using aptitude from the software repository. I didn't use any tarballs.

---

### Post by DaithiF on 2010-12-03
ok, the questions I asked were to determine whether you were using upstart or the older init.d scripts start-up mechanism.  The fact that /etc/init.d/mysql is a real file, not a symlink to an upstart script, and the fact that /etc/init/mysql.conf doesn't exist confirms that you are not using upstart.

In which case you don't get the ability to add dependencies on specific network interfaces, which is unfortunate, as that is exactly what you need.  

Instead you'll need to work with the /etc/rcX.d/ symlinks, there should be a symlink there for mysql something like SXXmysql, the number XX indicating the order in gets run at startup -- so I would renaming that to make it run later (e.g. S99mysql) to hopefully give the network interfaces more time to initialise.

---

### Post by SonicComKid on 2010-12-03
oh, okay. Sorry I never heard of upstart before.

I went through all of my /etc/rc*.d/ directories and found that mysql exists in most of them, typically as S20 or S19 (in one as K21).

I never understood the purpose of the rc numbers. I was told once that they are something to do with runlevels which in turn is something I never fully understood. The only thing I ever did with runlevels was very basic batch files in MS-Dos for the choice command way back.

I looked to see if I could find any entry that had to do with when the network interfaces load, but I couldn't find one, and I honestly don't know if me going through all these rc levels changing mysql to a higher number will guarantee that mysql is going to always load after the network bridge settings do.

What bridge utilities does is it takes eth0 and eth 1 and makes them basically non-existent and replaces them with br0 instead. Most of my applications like noip2 either bind to the ip address br0 acquires, or br0 itself.

---

