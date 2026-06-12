---
title: "Installed Virtualbox and broke root login"
date: 2009-09-29
forum: General Help
---

### Post by Steve00 on 2009-09-29
I installed virtualbox 3.0.2 according to the instructions I found at:

[http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/]("http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/")

Virtualbox installed as advertised and appears to run o.k. Haven't tried to create a vm yet.

However, I now cannot drop to root. Sudo doesn't work. Nor can I run any programs that require admin privileges. For example, I tried to run Partition Editor from System | Administrator and when I key in my password I get 

"Failed to run /usr/sbin/gparted as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Trying to drop to root from terminal using su results in:

"Authentication failure" after typing in my password.

I did double-check to ensure that I had my caplocks OFF.

Suggestions?

Thanks.

--Steve

---

### Post by jkysam on 2009-09-29
Are you sure that sudo is not working at all? From the command line have you tried to reset your root password:
[code]
sudo passwd root
[code]

---

### Post by Steve00 on 2009-09-29
No, but I tried su as well as sudo users-admin and got the same response. However, after more nosing about on the forums I found:

boot into recovery mode and drop to root and then run

gpasswd -a username admin 

that took care of the problem.

The big question remains: what'd I do to cause this to happen?

---

