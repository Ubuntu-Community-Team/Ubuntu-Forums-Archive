---
title: "[HELP] Can't login in visual login System"
date: 2010-07-31
forum: General Help
---

### Post by astarring on 2010-07-31
I was a user from China. 
I login Ubuntu 10.04 used gdm and kdm can't login. The login system just fash some times and go back to login sytem.

I can only use [FONT=Comic Sans MS]startx[/FONT] to login system.
And I see system Log, I find those log:

ul 22 23:02:04 owen-desktop gdm-session-worker[4623]: pam_unix(gdm:auth): conversation failed
Jul 22 23:02:04 owen-desktop gdm-session-worker[4623]: pam_unix(gdm:auth): auth could not identify password for [zou]
Jul 22 23:02:04 owen-desktop gdm-session-worker[4623]: pam_winbind(gdm:auth): getting password (0x00000388)
Jul 22 23:02:04 owen-desktop gdm-session-worker[4623]: pam_winbind(gdm:auth): Could not retrieve user's password
Jul 22 23:02:05 owen-desktop gdm-session-worker[4626]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "owen"


Anyone help me? I have request help in China Ubuntu forum but no reply. I didn't use Ubuntu for a long time for this issue. I really hope I can't used Ubuntu because I love it.

---

### Post by bodhi.zazen on 2010-07-31
Does that user exist or is the account locked ?

---

### Post by astarring on 2010-08-01
Of course, This account exist. It is my usually login account. I used startx login to Xorg. And see my account wasn't locked. Any more information needed?

---

