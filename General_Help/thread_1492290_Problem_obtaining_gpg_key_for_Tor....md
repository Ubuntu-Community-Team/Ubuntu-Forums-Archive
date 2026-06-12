---
title: "Problem obtaining gpg key for Tor..."
date: 2010-05-24
forum: General Help
---

### Post by AcidMoon on 2010-05-24
Hello wise people of Ubuntu-Forum! 8)

I'm having a problem installing Tor. I've installed it successfully a few times before thanks the excellent guide at: [https://help.ubuntu.com/community/Tor?action=show&redirect=TOR](https://help.ubuntu.com/community/Tor?action=show&redirect=TOR)

The error I'm having is when I request the gpg key:

```
ocean@ubuntu:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
```Then after quite a delay all I get now (instead of "OK") is:

```
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```Has anyone else had this problem and found a solution? If so any help you can give would be appreciated. TY.

---

### Post by AcidMoon on 2010-05-25
Yay found a solution to my problem:

The error:

gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

It is because your firewall is blocking access to the Keyserver.  Keyservers use port 11371 to communicate, not port 80 which is the  normal HTTP port, so open 11371 as an outbound port on your firewall and  re-run the command and it will work fine.

Thanks to: [http://www.serenux.com/2009/07/howto-make-use-of-ubuntu-ppa-repositories/](http://www.serenux.com/2009/07/howto-make-use-of-ubuntu-ppa-repositories/)

I'll mark this as solved and hope it helps someone else one day!

---

### Post by Aisteru on 2010-06-19
Thanks, it did! :-D

---

### Post by crazyseagull on 2010-08-20
Hello there,

I don't know how to open up 11371 as an outbound port on firewall.
I am new user of Ubuntu.

Please kindly help me.

Kind Regards,
Seagull

---

### Post by hughh on 2013-01-25
> **crazyseagull said:**
> Hello there,

I don't know how to open up 11371 as an outbound port on firewall.
I am new user of Ubuntu.

Please kindly help me.

Kind Regards,
Seagull

Look up "Enable or block firewall access" in the Ubuntu Desktop Guide or:
 ```
ufw --help
```Note that you'll need to run the command with 'sudo', e.g.:
```
sudo ufw allow <port>
```This will cause the system to ask for your password.

A GUI alternative is to intall gufw, which merely provides a GUI front-end to ufw.

---

