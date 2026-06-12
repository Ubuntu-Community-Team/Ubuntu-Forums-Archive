---
title: "likewise-open and active directory logins working, but no motd anymore"
date: 2011-02-01
forum: General Help
---

### Post by stephanhughson on 2011-02-01
Hi,

I've installed likewise-open and can now login to some Ubuntu 10.04 servers, authenticating against a Microsoft Active Directory server.

I use landscape-common which gives me a nice motd each time I login, showing the load, memory and disk usage etc.

When I login with a local user account, that shows up, but when I login to the domain, it doesn't.

Does anyone know where to start looking on this one?

Has this happened to anyone else?

The auth.log looks ok when I login:

Feb  1 17:38:19 servername sshd[2498]: Accepted keyboard-interactive/pam for DOMAIN\\myusername from 10.11.12.13 port 61589 ssh2
Feb  1 17:38:19 servername sshd[2498]: pam_unix(sshd:session): session opened for user DOMAIN\myusername by (uid=0)

whoami
DOMAIN\myusername

Thanks for any help. If anyone has likewise-open set up and could confirm that it does or doesn't happen to them, that would be pretty useful for me. I'd like to know if I've made a mistake somewhere.

---

### Post by stephanhughson on 2011-03-21
I've found out how to do this, it was obvious :(


"14.7.6. Display an MOTD

You can set Likewise to display a message of the day. It appears after a user logs on but before the logon script executes to give users information about a computer. The message can, for instance, remind users of the next scheduled maintenance window.

With Likewise Enterprise, you can manage this setting by using a Likewise group policy; see Display a Message of the Day at Logon in the Likewise Enterprise guide.

Location in registry:

[HKEY_THIS_MACHINE\Services\lsass\Parameters\PAM]

Value Entry

DisplayMotd

Example with the value set to 1, or true, to display a message:

"DisplayMotd"=dword:00000001"



So just lw-edit-reg , change that, login again and that's it!

---

