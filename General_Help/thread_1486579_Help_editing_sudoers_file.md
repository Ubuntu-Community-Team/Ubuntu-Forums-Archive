---
title: "Help editing sudoers file"
date: 2010-05-18
forum: General Help
---

### Post by satish_j on 2010-05-18
Need help editing sudoers file...
I get syntax error everytime i try to save changes to sudoers file..iam pretty sure syntax is OK..
Basically,iam entering foll:
_User_Alias<tab>PowerUsers=satish_
Tried entering space instead of tab between useralias and name,with no success.If i comment this line(putting #),file is saved without any issues.
Moreover syntax error is at line 15,whereas the above user alias entered by me is at line16..
Any help seriously appreciated..
:confused::confused:

---

### Post by satish_j on 2010-05-18
:mad::mad::mad:Regrettable Bump..

---

### Post by gmargo on 2010-05-18
Show the entire /etc/sudoers file.

---

### Post by gmargo on 2010-05-18
> **gmargo said:**
> Show the entire /etc/sudoers file.
Never mind that.

The "PowerUsers" string is invalid.  An alias name may consist of uppercase letters, numbers, and underscores; the lowercase letters are invalid. See the **sudoers(5)** man page for full info.

---

### Post by satish_j on 2010-05-19
> **gmargo said:**
> Never mind that.

The "PowerUsers" string is invalid.  An alias name may consist of uppercase letters, numbers, and underscores; the lowercase letters are invalid. See the **sudoers(5)** man page for full info.

I cannot believe i commited such a silly mistake...I think i just focussed on first letter of name(to be in capital)
Thanks anyway...:)

---

### Post by satish_j on 2010-05-20
Synaptic still asks for password for user 'satish' even though i entered foll rule in sudoers:
POWERUSERS ALL=NOPASSWD: /usr/sbin/synaptic
user 'satish' belongs to POWRUSERS alias
Does the system needs to be rebooted after changes to sudoers file???

---

### Post by satish_j on 2010-05-20
synaptic still asks for password..even after restarting the system..
Isn't there any way to start synaptic without asking password????
desperately seeking help...
:(:(:(

---

### Post by satish_j on 2010-05-21
Done...

---

