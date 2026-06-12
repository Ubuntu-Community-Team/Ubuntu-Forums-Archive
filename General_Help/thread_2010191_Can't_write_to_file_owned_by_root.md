---
title: "Can't write to file owned by root"
date: 2012-06-25
forum: General Help
---

### Post by O2Blevel on 2012-06-25
I'm trying to edit a file owned by root using this:

```
sudo -i
echo powersave > /sys/module/pcie_aspm/parameters/policy
exit
```

I think that gets around the redirecting sudo problem but I still can't edit the file.

I'd appreciate any help.

---

### Post by timswait on 2012-06-25
Use sudo to open whatever notepad editor you use (for example I use kate in kubuntu, it might be gedit in ubuntu). So from terminal just type "sudo kate", "sudo gedit", etc and it'll open your notepad editor with root access. You can then open the file you want to edit, edit and save it.

---

### Post by drmrgd on 2012-06-25
If you're going to run graphically, you should use gksudo (or kdesudo for Kubuntu), and not sudo.  See this (scroll down to the "Graphical sudo" section):

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by O2Blevel on 2012-06-25
Thanks for the quick replies, but when I tried gksu gedit, it would  not let me save the changes. It says I don't have the permissions necessary to save the file.

---

### Post by steeldriver on 2012-06-25
I don't see why 'sudo -i' wouldn't work (unless the file mode is readonly for root? by default it should be rw I think)

```
$ ls -l /sys/module/pcie_aspm/parameters/policy
-rw-r--r-- 1 root root 4096 Jun 25 09:04 /sys/module/pcie_aspm/parameters/policy

```

However I've worked around the redirect issue in the past using 'sudo tee'

```
echo powersave | sudo tee /sys/module/pcie_aspm/parameters/policy
```If you don't want to see the echoed output you can redirect *that* to /dev/null

```
echo powersave | sudo tee /sys/module/pcie_aspm/parameters/policy 1>/dev/null
```BTW those sys files are kind of funny - you don't really edit them literally - when you write a new powersave policy (e.g. 'powersave' or 'default') they kind of rearrange themselves i.e.:

```

$ cat /sys/module/pcie_aspm/parameters/policy
[default] performance powersave 
$
$ echo powersave | sudo tee /sys/module/pcie_aspm/parameters/policy 1>/dev/null
$
$ cat /sys/module/pcie_aspm/parameters/policy
default performance [powersave] 
$
$ echo default | sudo tee /sys/module/pcie_aspm/parameters/policy 1>/dev/null
$
$ cat /sys/module/pcie_aspm/parameters/policy
[default] performance powersave 
$ 

```

---

### Post by O2Blevel on 2012-06-25
When I do this command:

```
echo powersave | sudo tee /sys/module/pcie_aspm/parameters/policy 1>/dev/null
```

I get this result:

```
tee: /sys/module/pcie_aspm/parameters/policy: Operation not permitted
```

---

### Post by steeldriver on 2012-06-25
... and did you check the permissions?

```
ls -l /sys/module/pcie_aspm/parameters/policy
```

---

### Post by O2Blevel on 2012-06-25
Yes, the permissions are the same as yours.

I just tried running the command from the recovery console and got the same response, tee operation not permitted.

---

### Post by steeldriver on 2012-06-25
EDIT: OK I think I can confirm what's happening - notice your error is  now "operation not permitted" rather than "permission denied"? 

That's  likely because ASPM is disabled at the BIOS level - in fact I tested it on a different machine and got the same behavior as you - until I updated grub with 'pcie_aspm=force' and now it *does*  work

I don't know if forcing pcie_aspm is bad for other reasons though - ymmv

---

### Post by philinux on 2012-06-25
In the past I've edited this file.

/etc/init.d/ondemand

But it's easier to use indicator-cpufreq to change on the fly. (Unity 12.04)

---

### Post by steeldriver on 2012-06-25
nevermind - edited my earlier post instead

---

### Post by VanillaMozilla on 2012-06-25
You misused the sudo command.

The command is something like this:
sudo [switches] <command>

not
sudo [switches]
<command>

If you were using gedit (or another gui program), the command would be something like
gksudo gedit [filename]
or
gksudo gedit [filename] &

I would not recommend using su or gksu.

---

### Post by CharlesA on 2012-06-25
gksu is a link to gksudo. su is not a link to sudo, however.

---

### Post by O2Blevel on 2012-06-25
> **steeldriver said:**
> EDIT: OK I think I can confirm what's happening - notice your error is  now "operation not permitted" rather than "permission denied"? 

That's  likely because ASPM is disabled at the BIOS level - in fact I tested it on a different machine and got the same behavior as you - until I updated grub with 'pcie_aspm=force' and now it *does*  work

I don't know if forcing pcie_aspm is bad for other reasons though - ymmv

Looks like I'm going to have to edit grub. I wanted to edit the policy file to see how it worked and whether it caused any problems before I made it permanent, but I don't see any other way.

Thanks for your help.

---

### Post by steeldriver on 2012-06-25
you can always add it one-time (press 'shift' to get the grub boot screen if you usually boot straight in - then 'e' to edit the boot line) rather than editing/updating the grub config - that way if it fails you can just reboot as before

---

### Post by VanillaMozilla on 2012-06-25
> **VanillaMozilla said:**
> You misused the sudo command.
Oops, probably not, due to fancy use of the -i switch.  And gksu didn't work either, so I guess the problem is not the sudo command.  My mistake.

---

### Post by CharlesA on 2012-06-25
> **CharlesA said:**
> gksu is a link to gksudo. su is not a link to sudo, however.

It's the other way around for gksudo:

```
charles@Precise:~$ ls -l $(which gksu)
-rwxr-xr-x 1 root root 28128 Nov  9  2011 /usr/bin/gksu
charles@Precise:~$ ls -l $(which gksudo)
lrwxrwxrwx 1 root root 4 May 24 11:50 /usr/bin/gksudo -> gksu

```

---

### Post by Rebelli0us on 2012-06-25
Isn't that an awful lot of work just for editing **your **file on **your **computer?

---

### Post by CharlesA on 2012-06-25
> **Rebelli0us said:**
> Isn't that an awful lot of work just for editing **your **file on **your **computer?
I suppose so.

It would be easier just to open the file in gedit or nano or something and add powersave at the bottom instead of messing with redirects:

```
gksu gedit /sys/module/pcie_aspm/parameters/policy
```

---

### Post by O2Blevel on 2012-06-25
> **Rebelli0us said:**
> Isn't that an awful lot of work just for editing **your **file on **your **computer?

That's what my problem is, I can't edit the file. Don't know why.

---

### Post by CharlesA on 2012-06-25
> **O2Blevel said:**
> That's what my problem is, I can't edit the file. Don't know why.

Not even with nano?

```
 sudo nano /sys/module/pcie_aspm/parameters/policy
```

I just tested it on my 12.04 box and I was able to [s]change[/s] read it, but not change it.

Have you run a fsck lately?

```
sudo touch /forcefsck
```

Reboot.

---

### Post by sandyd on 2012-06-25
Probably
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=663202](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=663202)

---

### Post by steeldriver on 2012-06-25
> **O2Blevel said:**
> That's what my problem is, I can't edit the file. Don't know why.

um... didn't we figure out that the problem is **not** that you can't edit the file, it's that the operation implied by changing the file (i.e. changing the pcie power management policy) is **not permitted by BIOS**?

---

### Post by sandyd on 2012-06-25
> **steeldriver said:**
> um... didn't we figure out that the problem is **not** that you can't edit the file, it's that the operation implied by changing the file (i.e. changing the pcie power management policy) is **not permitted by BIOS**?
Check the bug above.
"**And indeed the parameter is no longer setable with kernel 3.2.9**:"

The other bug that references this is burried somewhere.

---

### Post by O2Blevel on 2012-06-25
> **steeldriver said:**
> um... didn't we figure out that the problem is **not** that you can't edit the file, it's that the operation implied by changing the file (i.e. changing the pcie power management policy) is **not permitted by BIOS**?

I've checked my BIOS a couple of times and I don't see anything there that would be a problem. Everything is set to the default values. It's a Dell laptop, E1505.

---

### Post by sandyd on 2012-06-25
Bug reported.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1017746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1017746)

---

### Post by sandyd on 2012-06-25
> **O2Blevel said:**
> I've checked my BIOS a couple of times and I don't see anything there that would be a problem. Everything is set to the default values. It's a Dell laptop, E1505.
Please run```

apport-cli -f -p linux-image-`uname -r`--save bug.apport
```
and attach the bug.apport file in your home folder.

---

### Post by philinux on 2012-06-26
> **sandyd said:**
> Please run
```

apport-collect 1017746
```
You will need a launchpad account to send the information to the bug.

Only the original bug reporter can run that I think. I've had this error in the past even though I'm subscribed to a bug.

Worth a shot though as the system might have changed.

---

### Post by sandyd on 2012-06-26
> **philinux said:**
> Only the original bug reporter can run that I think. I've had this error in the past even though I'm subscribed to a bug.

Worth a shot though as the system might have changed.
fixed.

---

### Post by philinux on 2012-06-26
> **sandyd said:**
> fixed.

Ah nice. Shame the other won't play ball.

---

### Post by sandyd on 2012-06-26
you know that this can't be fixed without the op :(

---

