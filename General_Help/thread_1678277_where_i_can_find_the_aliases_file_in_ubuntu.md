---
title: "where i can find the aliases file in ubuntu??"
date: 2011-01-30
forum: General Help
---

### Post by kofkid on 2011-01-30
Sorry about my english but im mexican and i know a lil bit of english.

Same at the title: where i can find the aliases file in ubuntu, cause my internet is slow in firefox and ahi read thath turnning off the ipv6 , the internet rise up in velocity so, where i can find the file???

---

### Post by howefield on 2011-01-30
Moved to General Help.

---

### Post by tredegar on 2011-01-30
With modern ubuntu, IPv6 is in the kernel. So you cannot edit the aliases file, you need to tell the kernel not to use IPv6.

For a _temporary_ fix / unfix

```
ip a | grep inet6
sudo sh -c 'echo [COLOR="Red"]1[/COLOR] > /proc/sys/net/ipv6/conf/all/disable_ipv6'
ip a | grep inet6
sudo sh -c 'echo [COLOR="Red"]0[/COLOR] > /proc/sys/net/ipv6/conf/all/disable_ipv6'
ip a | grep inet6

```

For a _permanent_ fix:

```
gksudo gedit /etc/default/grub
```
Change this line
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash whatever”

```
To
```
GRUB_CMDLINE_LINUX_DEFAULT=”[COLOR="Red"]ipv6.disable=1[/COLOR] quiet splash whatever”
```
Save the change.

Then
```
sudo update-grub
```

Reboot.
IPV6 is now gone

---

### Post by kofkid on 2011-01-30
thnx i will try the solution , and then i can tell you if that results to me :)

---

### Post by AlphaLexman on 2011-01-30
I am still on 10.04 ubuntu, but the default alias file is ~/.bash_aliases which is sourced from ~/.bashrc which is sourced from ~/.bash_profile

---

### Post by SaintDanBert on 2011-01-30
There there are the "aliases" that live within /etc/hosts as alternate names for network ip-addresses...

And "aliases" that are part of sendmail to implement acceptable and alternate email target names associated with a specific email mailbox.

And ...

---

### Post by tredegar on 2011-01-31
@ AlphaLexman & SaintDanBert

True, there are "aliases" all over the place, but when mentioned in conjunction with disabling ipv6 it usually means people are referring to outdated advice like this:
> If you are using Debian/Ubuntu linux, open file /etc/modprobe.d/aliases
# vi /etc/modprobe.d/aliases
Find the line:
alias net-pf-10 ipv6

Replace with:
alias net-pf-10 off
alias ipv6 off
But **/etc/modprobe.d/aliases** no longer exists (which is why the OP cannot find it) and ipv6 is now built into the kernel. So a different solution is needed.

---

