---
title: "Deleted nvidia-glx files"
date: 2009-07-09
forum: General Help
---

### Post by nzuri on 2009-07-09
hi.

i accidantly deleted the package nvidia-glx-180.deb and some other things with the "computer-janitor".
somehow i ignored the warning: "it might destroy your system"....

now i cant activate the nvidia gfx-driver and i cant install any new gfx-driver.
my screen runs very slow and i cant even watch tv. :(

when i look in synaptic there is no discription or version name behind the packagenames nvidia-glx-*.

when i try to install with apt-get, it returns the following:
```
user@computer:~$ sudo apt-get install nvidia-glx-180
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-180 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-180-libvdpau nvidia-glx-180 nvidia-glx-177
E: Package nvidia-glx-180 has no installation candidate
```can someone tell me, how i can get the driver to run?

or if there is no possibility, which diractory i have to restore to have the running system from the day before.

gz & thx nzuri

---

### Post by hangfire on 2009-07-09
Welcome to the forums.

You'll be fixing this with either dpkg or apt-get commands.

Try:

sudo apt-get -d install nvidia-glx-180
sudo apt-get --fix-broken nvidia-glx-180
sudo apt-get --reinstall nvidia-glx-180

---

### Post by nzuri on 2009-07-09
sry, but 

apt-get -d

is an invalid option. i dont know which option u mean

---

### Post by hangfire on 2009-07-09
> **nzuri said:**
> 
apt-get -d

is an invalid option.

Sorry, try my updated edit.

---

### Post by nzuri on 2009-07-09
> sudo apt-get -d install nvidia-glx-180

returns the same message as it does without -d

---

### Post by hangfire on 2009-07-09
> **nzuri said:**
> returns the same message as it does without -d

What version of Ubuntu are you using?


```

cat /etc/lsb-release

```

---

### Post by nzuri on 2009-07-09
jaunty 9.04

---

### Post by hangfire on 2009-07-09
> **nzuri said:**
> jaunty 9.04

I'm currently on 8.04 so some options may differ. 

Did you try the other commands?

---

### Post by nzuri on 2009-07-09
what other commands? tell me what "apt-get install -d" would do, so i can look in the help which command may be the same.

---

### Post by hangfire on 2009-07-09
> **nzuri said:**
> what other commands? tell me what "apt-get install -d" would do, so i can look in the help which command may be the same.

The **-d** means download only, don't install. This should replace the package. The long form on 8.04 is **--download-only**

The other commands are:

```

sudo apt-get --fix-broken nvidia-glx-180
sudo apt-get --reinstall nvidia-glx-180

```

---

### Post by nzuri on 2009-07-09
sry, but the apt-get syntax isnt possible with just an option.

it needs

apt-get -d "command" 
if nvidia-glx-180 is the command, so it retrurns

```
E: Package nvidia-glx-180 has no installat
```


EDIT:
its done.

the driver files were deleted, but i found them in the repositories.

dont know why, but somehow they are not in the sources.lst...

thx

---

### Post by hangfire on 2009-07-09
> **nzuri said:**
> sry, but the apt-get syntax isnt possible with just an option.

That's why I edited my initial reply and added the option "install".


> **nzuri said:**
> 
EDIT:
its done.

the driver files were deleted, but i found them in the repositories.

dont know why, but somehow they are not in the sources.lst...

thx

I'm glad you worked it out.

---

