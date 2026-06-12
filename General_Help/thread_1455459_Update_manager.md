---
title: "Update manager?"
date: 2010-04-16
forum: General Help
---

### Post by willchurch on 2010-04-16
[LIST]
[/LIST]Long story short, there is a red icon in the info bar at the top of the screen; when clicked it says:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'Read' is not known on line 24 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


What to do?

---

### Post by marshmallow1304 on 2010-04-16
Have a look at /etc/apt/sources.list .  Hint: Look at line 24.  If you are unsure about what it all means, post the file here.

---

### Post by oldos2er on 2010-04-16
Start by fixing /etc/apt/sources.list ```
gksu gedit /etc/apt/sources.list
```
All lines should begin with deb or deb-src

---

### Post by willchurch on 2010-04-16
When I enter "gksu gedit /etc/apt/sources.list" I get this:

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free



Read more: [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/#ixzz0kNfVj13R](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/#ixzz0kNfVj13R)

---

### Post by sandyd on 2010-04-16
um... why are you using dapper? it has already reached EOL.

---

### Post by marshmallow1304 on 2010-04-16
The problem is the line starting with "Read more:".  Remove that line.  Also, it would be a good idea to upgrade to or install a newer version, as Dapper is no longer supported and no longer receives security updates.

---

### Post by willchurch on 2010-04-16
how do i update?

---

### Post by willchurch on 2010-04-16
disregard my last post
i tried to update, and was given this:
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

---

### Post by oldos2er on 2010-04-17
You'll need to do a fresh install of 8.04, 9.04 or 9.10. I can't recommend 8.10 because it's going to reach its EOL in a couple weeks, when 10.04 is released.

---

