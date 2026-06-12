---
title: "Postfix errors"
date: 2010-02-01
forum: General Help
---

### Post by AllanP on 2010-02-01
I'm totally in the dark here regarding Postfix. Did I install something by mistake? i don't know. However I am getting this update message and the enclosed attachments in numerical order. How can I get rid of Postfix?

---

### Post by t4thfavor on 2010-02-01
Very strange, it looks like an update, I have no idea how that would happen, unless they decided to add postfix to the base install.

If they didn't, you may have installed something that needed it.

the broken packages message can be fixed with this on the command line.
```

sudo apt-get install --fix-missing

```

---

### Post by AllanP on 2010-02-01
> **t4thfavor said:**
> Very strange, it looks like an update, I have no idea how that would happen, unless they decided to add postfix to the base install.

If they didn't, you may have installed something that needed it.

the broken packages message can be fixed with this on the command line.
```

sudo apt-get install --fix-missing

```
Thanks; here's the response I get to that
allan@allan-desktop:~$ sudo apt-get install --fix-missing
[sudo] password for allan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bsd-mailx: Depends: postfix but it is not installed or
                      mail-transport-agent
E: Unmet dependencies. Try using -f.
OK I'll try that.

allan@allan-desktop:~$ sudo sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Then tried "check" on the update and got "You have 1 broken package on your system! Use the "broken" filter to locate it. I found the problem in Synaptic and tried to remove "mailx" and got this response.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by AllanP on 2010-02-01
I gksudo'd nautilus; searched for "postfix". There were about ten entries. I deleted them all; logged out and back in and the little round red icon with the white bar through it was gone; for about a minute and now it's back. Grrrr.:mad:

---

### Post by AllanP on 2010-02-01
Solved I think. I tried sudo killall dpkg; didn't work. I then did "sudo pkill apt" then opened Synaptic and was able to remove "mailx". So far so good.

---

