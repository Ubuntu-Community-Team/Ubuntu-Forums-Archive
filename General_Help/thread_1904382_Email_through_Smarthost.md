---
title: "Email through Smarthost"
date: 2012-01-04
forum: General Help
---

### Post by mistaWAC on 2012-01-04
So I'm posting because I honestly don't really know what I'm looking for.  I've got Icinga Monitoring setup and need it to send notifications to a support email address on our email server whenever something goes wrong.  I'm having trouble trying to get it to do just that.  Can someone point me in the right direction to get this working?  I want to use the smarthost I was given by my boss (it's an IP address rather than domain name like I see everywhere), but I just don't have a clue right now.  I've never setup mailing on *nix before.  If any other information is needed ask and ye shall receive..

---

### Post by dcstar on 2012-01-05
> **mistaWAC said:**
> So I'm posting because I honestly don't really know what I'm looking for.  I've got Icinga Monitoring setup and need it to send notifications to a support email address on our email server whenever something goes wrong.  I'm having trouble trying to get it to do just that.  Can someone point me in the right direction to get this working?  I want to use the smarthost I was given by my boss (it's an IP address rather than domain name like I see everywhere), but I just don't have a clue right now.  I've never setup mailing on *nix before.  If any other information is needed ask and ye shall receive..

```
sudo dpkg-reconfigure debconf
```And select the Gnome option, then install the **postfix** package and answer the appropriate questions.

---

