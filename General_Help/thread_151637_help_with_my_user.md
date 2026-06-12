---
title: "help with my user"
date: 2006-03-28
forum: General Help
---

### Post by slipk487 on 2006-03-28
how do i add my self to file \etc\hosts because ubuntu wont open much with out it

---

### Post by izmaelis on 2006-03-28
/etc/hosts file binds some IP addresses to domain names, for example:
```
127.0.0.1 localhost
```
please ask more informative question.

---

### Post by slipk487 on 2006-03-28
im new so i dont know much right now and i have no internet connection on it eather because i have no nic drivers

---

### Post by taurus on 2006-03-28
Is that an onboard NIC, PCI card, wireless, USB, etc.?  Also, it would be nice to know the model of it too.  We need more info before we can help you to get your network card working!

---

### Post by slipk487 on 2006-03-28
its some kind of d-link pci card and im not sure what model it is

---

### Post by AndrewCaul on 2006-03-28
Is it saying it can't find the X server or whatever?
Just add the name of your computer to your hosts file on the same line as 127.0.0.1.

If you can't sudo because of this problem, you can use the recovery console or a Live CD to edit the file.

---

### Post by slipk487 on 2006-03-28
i dont know how to do that but i think it might be fixed after i can get online with that comp because im trying to find drivers for my nic card and dont know why my dial-up isnt showing up in the device manager

---

### Post by Mustard on 2006-03-28
HowToEditEtcHostsCreated Friday 20/01/2006 10:34

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname #returns the current hostname
hostname <hostname>  #sets the hostname according to the value entered for <hostname>
```

---

### Post by slipk487 on 2006-03-28
thanks i think it worked

---

