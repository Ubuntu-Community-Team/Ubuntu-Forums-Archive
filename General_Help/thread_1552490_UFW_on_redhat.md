---
title: "UFW on redhat?"
date: 2010-08-13
forum: General Help
---

### Post by bone2006 on 2010-08-13
I started to use ufw instead of iptables on the terminal, but was wondering if ufw could be installed on a redhat based system?  I'm asking, because my office has a mix systems and would prefer to use ufw on these rpm based systems.

---

### Post by Bachstelze on 2010-08-13
It is certainly possible. If ufw is not in your repositories, you might have to compile it from source, though. The source is here: [https://launchpad.net/ufw](https://launchpad.net/ufw)

---

### Post by Iowan on 2010-08-13
Unless I'm mistaken (certainly wouldn't be the first - or last - time), **ufw** is just a front-end  (not a replacement) for **iptables.**

---

### Post by wojox on 2010-08-13
> **Iowan said:**
> Unless I'm mistaken (certainly wouldn't be the first - or last - time), **ufw** is just a front-end  (not a replacement) for **iptables.**

Your right and the Firewall program on RedHat/Fedora is easier than Ubuntu's IMHO.

---

### Post by bone2006 on 2010-08-13
> **wojox said:**
> Your right and the Firewall program on RedHat/Fedora is easier than Ubuntu's IMHO.  

which frontend is on fedora that's easier than ufw?  Because I've only used iptables via the command line and I'm not aware of anything else that's easier than ufw.  I can't see anything being easier, but if it's as easy I'm happy.

Can't be gui, only command line also.

---

### Post by wojox on 2010-08-14
> **bone2006 said:**
> which frontend is on fedora that's easier than ufw?  Because I've only used iptables via the command line and I'm not aware of anything else that's easier than ufw.  I can't see anything being easier, but if it's as easy I'm happy.

Can't be gui, only command line also.

If that's the case then I'm wrong. I keep thinking ufw is a gui. I just use my router as a firewall.

The Fedora front end is a gui I'm talking about. So now your back to ip tables in .rpm land on a default install.

If you can't get ufw to work on your .rpm machine try [Shorewall]("http://www.shorewall.net/")

---

