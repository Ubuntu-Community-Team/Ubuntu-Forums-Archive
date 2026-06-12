---
title: "Postfix Restrictions"
date: 2012-05-02
forum: General Help
---

### Post by obatron on 2012-05-02
I've searched and am possibly blind to the answer...

I have a server with postfix installed only because I want to forward root mail to another address.   The problem is, the users of this system commonly use hacked windows boxes and their passwords are stolen.   The spammers use their passwords to make tunneled ssh connections to the server and start pumping spam through.

I have Tunneling disabled in sshd_config now (AllowTcpForwarding and PermitTunnel set to no).  I'm guessing the users will eventually complain that they can not tunnel VNC and other things...

Thus, I'm wondering if there would be a way to prevent all but root to send email from this system.  I've looked at the various POSTFIX about restricting access, however, they don't seem to do quite what I'm looking for.   I want all root mail to forward to an external email address, no local mail, and no user allowed to send mail via this system, and no relaying by any user.

I've tried various settings in the main.cf, however, I'm missing something important...any pointers would be appreciated...

---

