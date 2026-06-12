---
title: "Keyboard inputs go to tty7 and tty1 at the same time!"
date: 2010-05-13
forum: General Help
---

### Post by vivien` on 2010-05-13
Hello,

I installed Ubuntu with the netboot. I only installed the packages I needed. Concerning X, I installed xdm as login manager and fluxbox as window manager. All is working fine except that whatever I type under X (under xdm or, after logging in, under fluxbox) appears in tty1! The keyboard inputs appear under X and under tty1 (so usually after "login:", or hidden after "password:").

Let me provide you with more details. Starting from xdm, I cannot access to the other ttys. "ctrl+alt+F[1-6]" do not work. Actually, this is not entirely true: after I type "ctrl+alt+F2", all my keyboard inputs under X will be appear in tty2 (and not anymore in tty1). I can see that from /var/log/auth.log which has a lot of lines like this:
> May 13 10:15:45 data login[2182]: pam_unix(login:auth): check pass; user unknown
May 13 10:15:45 data login[2182]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=
May 13 10:15:48 data login[2182]: FAILED LOGIN (2) on '/dev/tty1' FOR 'UNKNOWN', Authentication failure
These errors are due to the fact that tty1 receives a wrong login (something I typed under X, before pressing RET). BTW: If I connect to xdm using my password (instead of my passphrase, thanks to pam_ssh), then I login into tty1 at the same time.

I checked that X is running under tty7. "ck-list-sessions" returns:
> Session1:
(...)
    x11-display = ':0'
    x11-display-device = '/dev/tty7'
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
(...)
Under X, if I type "ctrl+alt+F7" and "RET", then X crashes and it is launched again. After this, all is working fine: the tty[1-6] can be accessed and the keyboard inputs do not go anymore to them when I am under X.

I face the same problem on two different computers (a desktop computer and a laptop). Notice that I face the problem  even with pam_ssh not installed (I mentioned pam_ssh earlier).

The problem is really strange. I do not know where to start!

Thank you for any help you could provide!

---

### Post by vivien` on 2010-05-13
As a workaround, I removed XDM from rc scripts, using sysv-rc-conf. At the same time, I added a /etc/init/xdm.conf that actually launches "/etc/init.d/xdm start". Now all seems to be working properly.

Maybe there is a bug related to SysVinit.

---

