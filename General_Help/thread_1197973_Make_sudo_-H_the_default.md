---
title: "Make sudo -H the default?"
date: 2009-06-26
forum: General Help
---

### Post by bwooster47 on 2009-06-26
I am moving over from Fedora to Kubuntu, and ran into the problem of sudo clobbering the $HOME/.viminfo file - which is not yet solved, as far as I can tell (other than "don't do it" advice on the web, and arguments whether this is a vim issue or a ubuntu issue etc).

It seems quite dangerous to allow sudo to run with $HOME of a regular user, but run as root. 

I can't imagine that regular admin tasks need this - so, am thinking of making an alias
alias sudo="sudo -H"

This will protect against an inadvertent
sudo vim /etc/....
or any other sudo command that ends up writing to some file in $HOME

Does anyone see any issues with always running "sudo -H" instead of sudo for regular admin tasks?

---

### Post by jimv on 2009-06-26
Nevermind.

---

### Post by x22 on 2009-06-26
welcome to the forum

> sudo...

using "passwd root" we make root logons possible.
Then with suitable attention to working directory,
such problems disappear.

---

### Post by bwooster47 on 2009-06-27
> **x22 said:**
> 
using "passwd root" we make root logons possible. Then with suitable attention to working directory, such problems disappear.

Well, even if a root password is created, using sudo may still create files in $HOME, so that still requires using "sudo -H"

So far so good, I've aliased sudo to sudo -H, and apt-get seems to be working fine, editing config files works great (no more root-owned files in my home dir).

---

