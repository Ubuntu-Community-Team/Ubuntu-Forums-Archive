---
title: "unable to install updates"
date: 2011-01-28
forum: General Help
---

### Post by geds40 on 2011-01-28
When attempting to install updates on 10.4, I get this message:

Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 60%: unrecoverable fatal error, aborting:
  files list file for package 'libpolkit-gtk-1-0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
Processing triggers for python-central ...

I'm fingers crossed that this means something to somebody...

---

### Post by geds40 on 2011-03-03
Hi all,

Well it's been a month now and still no response. I would like to kick some life back into this query because a re-install would be a nightmare, what with a production lamp server, development website and all.

running sudo apt-get update, this is how it ends;

Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libpolkit-gtk-1-0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

I've tried re-installing libpolkit-gtk-1-0 but that doesn't help. Does anyone know if I can simply un-install this package or is the desktop dependant on it. I wouldn't get very far with just the command line.

---

### Post by deserthowler on 2011-03-03
How are you doing your updates?  Using command line or automatic updates?  I have no clue what is happening with your situation but I found that I can have problems updating my desktop using Update manager and it will give me results in Synaptic.  Just a thought.

Earl

---

### Post by geds40 on 2011-03-03
Hi Earl,

Both. I get the same problem running automatic updates as I do on the command line.

---

### Post by adeee on 2011-03-03
> **geds40 said:**
> When attempting to install updates on 10.4, I get this message:

Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 60%: unrecoverable fatal error, aborting:
  files list file for package 'libpolkit-gtk-1-0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
Processing triggers for python-central ...

I'm fingers crossed that this means something to somebody...


Well try these steps.

If you want to upgrade to 10.04, run   	Code:
 	update-manager -d

  

got the same error message and tried the following;

$ sudo dpkg --clear-avail

then

$ sudo aptitude safe-upgrade

---

### Post by geds40 on 2011-03-03
Hi Adeee,

I've tried all that and am still getting the same error message.  It simply won't update or upgrade, always ends with that same message. Thanks though...

---

### Post by sikander3786 on 2011-03-03
Try using an older /dpkg/status file.

Applications > Accessories > Terminal:

Backup the existing one,

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Use the older one.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Update & Upgrade.

```
sudo apt-get update && sudo apt-get upgrade
```

Please post any errors encountered.

---

### Post by geds40 on 2011-03-03
Hi Sikander3786,

I did all that, herewith the important bit;

114 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/231MB of archives.
After this operation, 4,129kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libpolkit-gtk-1-0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

Same again I'm afraid.

---

### Post by vivek.pandey on 2011-03-03
here are two suggestions
go to synaptic search libpolkit-gtk-1-0 and install it from there see what error its showing....
second when you install updates from update manager you get to see the list of packages being installed or updated if you find this particular package uncheck it and then try  updating

---

### Post by sikander3786 on 2011-03-03
Ok try this one.

```
sudo dpkg --clear-avail
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by geds40 on 2011-03-03
Hi Neo_aryan,

Trying to re-install libpolkit-gtk-1-0 just gets me the same error message.

When upgrading, that package isn't one of the ones selected for upgrading, so I can't de-select it.

It appears that the package error, whatever it is, prevents all packages from upgrading.

---

### Post by geds40 on 2011-03-03
Hi Neo_aryan,

re-installing that package produces the same error. 

Libpolkit-gtk-1-0 isn't one of those selected for upgrading so I can't de-select it.



Hi Again Sikander3786,

Same old, same old I'm afraid. Exactly the same error message. Thanks for your input.

---

### Post by philinux on 2011-03-03
> **geds40 said:**
> Hi Neo_aryan,

re-installing that package produces the same error. 

Libpolkit-gtk-1-0 isn't one of those selected for upgrading so I can't de-select it.



Hi Again Sikander3786,

Same old, same old I'm afraid. Exactly the same error message. Thanks for your input.

This might help.
[http://ubuntuforums.org/showthread.php?p=9517069#post9517069](http://ubuntuforums.org/showthread.php?p=9517069#post9517069)

---

### Post by sikander3786 on 2011-03-03
The link posted by *philinux* actually lists the solution to this problem. That is the last thing we do i.e, delete the /info file itself. Did you solve it or need further help?

---

### Post by geds40 on 2011-03-03
This looks like I'm going to need a fresh head before starting, so it'll be tomorrow before I try. Thanks very much for all the help so far. I'll let you know how it goes. 

Hoping to post as solved...

---

