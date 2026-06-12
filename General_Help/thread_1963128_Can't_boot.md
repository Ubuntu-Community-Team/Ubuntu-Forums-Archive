---
title: "Can't boot"
date: 2012-04-22
forum: General Help
---

### Post by stefcep on 2012-04-22
i have ubuntu 9.04 installed on a machine I rarely use. I needed to access some documents.  On booting I get the following:

Starting the Firestarter firewall....
ppp0: error fetching interface information: Device not found [fail]
Loading LIRC modules [ok]
Starting remote control daemons(s): LIRC [ok]
not starting bwbar, please edit /etc/default/bwbar      

and then booting hangs.

Any help would be appreciated as I want to get to the stuff in my home directory

---

### Post by HDave on 2012-04-22
I would either:

a) boot the machine from a live CD of Ubuntu and then copy the files over the network or via a USB memory stick
or

b) pop out the hard drive and stick it in an external enclosure and plug it into another computer

Either one will be way faster than figuring out what has gone wrong.  Once you get the files you need off of it, just install the latest 12.04.

---

### Post by stefcep on 2012-04-22
> **HDave said:**
> I would either:

a) boot the machine from a live CD of Ubuntu and then copy the files over the network or via a USB memory stick
or


Did this, but the files can't be opened because I'm not the owner

---

### Post by tmaranets on 2012-04-22
Then who is the owner? Are the files encrypted with a password?

---

### Post by HDave on 2012-04-23
> **stefcep said:**
> Did this, but the files can't be opened because I'm not the owner

Unless they are encrypted that will not matter.  If you are opening them from another Linux box then do it as super user (e.g. sudo).

If you are opening them from a Windows box then it won't care.

---

### Post by stefcep on 2012-04-27
> **HDave said:**
> Unless they are encrypted that will not matter.  If you are opening them from another Linux box then do it as super user (e.g. sudo).

If you are opening them from a Windows box then it won't care.

I boot up the machine with a copy of 9.10 as a live cd. I am the physical owner, but if I try to open the files eg pdf's I am told I can't because I am "not the owner".

So how do i use sudo to open a pdf after booting off a live cd?

---

### Post by HDave on 2012-04-29
You need to open the files as super-user.  Try this from a command line:

```
sudo nautlius
```

---

