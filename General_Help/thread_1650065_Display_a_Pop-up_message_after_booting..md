---
title: "Display a Pop-up message after booting."
date: 2010-12-21
forum: General Help
---

### Post by arunsasidhar on 2010-12-21
Hi,
  
    I am working in a company with 30 employees. I am sys admin here. We have Ubuntu in all desktops. 
     I need someones help to implement a requirement. The requirement is After booting up the PC (Before or After user login) display an "Acceptable Usage agreement" with a OK button. The User must press OK to proceed. The Acceptable Usage agreement shows our companies System network policy.  It can be easily done in a windows PC (Look [Here]("http://blogs.technet.com/b/askds/archive/2008/02/08/deploying-legal-notices-to-domain-computers-using-group-policy.aspx")). But I don't know how it is configure in ubuntu . Please help me in implementing this.

Thanking you in Anticipation.

Arun S

---

### Post by dcstar on 2010-12-22
> **arunsasidhar said:**
> Hi,
  
    I am working in a company with 30 employees. I am sys admin here. We have Ubuntu in all desktops. 
     I need someones help to implement a requirement. The requirement is After booting up the PC (Before or After user login) display an "Acceptable Usage agreement" with a OK button. The User must press OK to proceed. The Acceptable Usage agreement shows our companies System network policy.  It can be easily done in a windows PC (Look [Here]("http://blogs.technet.com/b/askds/archive/2008/02/08/deploying-legal-notices-to-domain-computers-using-group-policy.aspx")). But I don't know how it is configure in ubuntu . Please help me in implementing this.

Thanking you in Anticipation.

Arun S

[http://www.linuxforums.org/forum/red-hat-fedora-linux/37743-gui-login-motd.html#post201183](http://www.linuxforums.org/forum/red-hat-fedora-linux/37743-gui-login-motd.html#post201183)

---

### Post by arunsasidhar on 2010-12-28
> **dcstar said:**
> [http://www.linuxforums.org/forum/red-hat-fedora-linux/37743-gui-login-motd.html#post201183](http://www.linuxforums.org/forum/red-hat-fedora-linux/37743-gui-login-motd.html#post201183)
Hi,
  Thanks David for your reply. I tried the settings provided in the link with some changes for Ubuntu 9.10. But there is no result!. 

What i modified is 
1. There is no xdm directory in /etc/X11. So i edited /etc/X11/Xsession file.
2. Modified the xmessage path. 

Now the file Xsession file looks like [This]("http://pastie.org/1410779").

Is there any way to work this in Ubuntu??

Thanks,
Arun S

---

