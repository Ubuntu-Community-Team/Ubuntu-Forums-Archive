---
title: "Dependency Issues"
date: 2009-08-04
forum: General Help
---

### Post by Raddy13 on 2009-08-04
This originally began with me trying to install L7 protocols on my eBox router as such:

```
Floodgate:~$ sudo apt-get install ebox-l7-protocols
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ebox-l7-protocols: Depends: ebox (>= 1.1~svn) but 1.0.1-0ubuntu1~ppa1~hardy1 is to be installed
E: Broken packages
```I've gone through a number of other attempts to install various modules, and two errors seem to keep popping up:

```
The following packages have unmet dependencies:
  ebox: Depends: libyaml-tiny-perl but it is not installable
E: Broken packages
```And:

```
Removing jabber-muc ...
invoke-rc.d: unknown initscript, /etc/init.d/jabberd2 not found.
dpkg: error processing jabber-muc (--remove):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 jabber-muc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```I've been beating my head against a wall working with this, so any help is desperately needed and greatly appreciated!

2.6.24-24 Server
Ubuntu Hardy

---

### Post by Raddy13 on 2009-08-04
Bump

---

### Post by jocampo on 2009-08-04
did you try using apt-get command with check and -f options?

---

### Post by Raddy13 on 2009-08-04
I tried with -f switch and got the same results, and running check produced this output:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
```

Which I take to mean the packages are fine.

---

### Post by mc4man on 2009-08-04
It looks like you've added a third pary repo for ebox but the version of ebox you have isn't working with the module you're trying to install.

Are you basically using this?
[http://trac.ebox-platform.com/wiki/Document/Documentation/InstallationGuide](http://trac.ebox-platform.com/wiki/Document/Documentation/InstallationGuide)

There seems to be 2 versions (not counting 1.3) 1.0-1 and 1.2

Or are you using a different ppa?, or does the 'cd' factor into your install

---

### Post by Raddy13 on 2009-08-04
I was using the repositories listed in the "Perfect Ebox Setup," but as I was installing new packages my system crashed.  I'm approximately 800 miles from my router and was fixing it via ssh, so I'm kind of SOL until I get back home to reboot it.

---

