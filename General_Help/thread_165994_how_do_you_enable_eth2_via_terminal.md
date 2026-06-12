---
title: "how do you enable eth2 via terminal"
date: 2006-04-25
forum: General Help
---

### Post by cosmoshell on 2006-04-25
I want to know how to enable eth2 via terminal. two people already told my to ifup eth2 but i keep getting this
ifup: failed to open statefile /var/run/network/ifstate: no such file or directory

---

### Post by Zyphrexi on 2006-04-25
did you by any chance do it this way?

```
sudo ifup eth2
```

---

### Post by cosmoshell on 2006-04-25
[QUOTE=Zyphrexi]did you by any chance do it this way?

```
sudo ifup eth2
```[/QUOTE]
yes

---

### Post by Zyphrexi on 2006-04-25
are you able to enable it any other way? with like the network manager?

the only time I've run into problems dealing with that file is when I try running without superuser privilages.

really all I know is that I don't have that either, in fact it cuts off at /var/run on my system.

i got this from ```
man ifup
```

```
KNOWN BUGS/LIMITATIONS
       The program keeps records of whether network interfaces are up or down.
       Under  exceptional  circumstances these records can become inconsistent
       with the real states of the interfaces.  For example, an interface that
       was  brought  up  using ifup and later deconfigured using ifconfig will
       still be recorded as up.  To fix this you can use the --force option to
       force  ifup  or ifdown to run configuration or deconfiguration commands
       despite what it considers the current state of the interface to be.

       The file /etc/network/run/ifstate must be writable for ifup  or  ifdown
       to  work  properly.   If  that  location  is not writable (for example,
       because the root filesystem is mounted read-only for  system  recovery)
       then  /etc/network/run/ifstate  should  be  made  a  symbolic link to a
       writable location.  If that is  not  possible  then  you  can  use  the
       --force option to run configuration or deconfiguration commands without
       updating the file.

```

try ```
man ifconfig
``` and ```
man interfaces
```

other than that, my knowledge is limited

---

### Post by cosmoshell on 2006-04-26
hjklhhlkhjhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

---

### Post by pato101 on 2006-04-26
[QUOTE=cosmoshell]I want to know how to enable eth2 via terminal. two people already told my to ifup eth2 but i keep getting this
ifup: failed to open statefile /var/run/network/ifstate: no such file or directory[/QUOTE]

I don't know if I understand your question correctly. Let me point a couple of choices.:confused: 

I sometimes use the cli like this:
```

sudo ifconfig eth2 10.0.0.2 netmask 255.255.255.0 up

```
(supposing you want those IP/netmask;I do not know how to do it with dhcp :( ).

This works, but won't be "saved" so you will require to do it again if you reboot the machine. Furthermore, you may require to add routing, as, for instance:
```
sudo route add default gw eth2
```

This approach is useful to bring up the interface at "abnormal cases" (you plugged the laptop at a friend's DSL router or something like that).

However, I guess that  what you want to do is:
```
sudo ifup eth2
```

In order to do that, you will have to configure eth2 previously (system->networking graphical tool will do). There you can setup the static/dynamic IP and if the interface is to be up at startup or not (so you'll require ```
sudo ifup eth2
``` when you need the adaptor if you choose not to start the eth2 automatically)

---

### Post by Ramses de Norre on 2006-04-26
Is it configured properly? (settings are in /etc/network/interfaces) 
If so: does sudo ifup --force eth2 work?

---

### Post by cosmoshell on 2006-04-26
[QUOTE=Ramses de Norre]Is it configured properly? (settings are in /etc/network/interfaces) 
If so: does sudo ifup --force eth2 work?[/QUOTE]
i keep getting this only when i boot up with initng ifup: failed to open statefile /var/run/network/ifstate: No such file or directory. the only way for me to get my networked started is to goto >system>administrative>networking and i have to do it on every boot.

---

### Post by vitko on 2006-05-05
I got 

   $ ifup eth0
   ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

after upgrade to Dapper. Of course eth0 is properly configured in /etc/network/interfaces:

   ...
   iface eth0 inet dhcp
   ...

Now the problem is solved: I just did 

   # mkdir /var/run/network
   # touch /var/run/network/ifstate

and interface comes up even with DHCP nicely.

Just my USD 0.02.

---

