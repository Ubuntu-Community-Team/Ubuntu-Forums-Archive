---
title: "Default groups for main user"
date: 2006-05-06
forum: General Help
---

### Post by Magnum818 on 2006-05-06
I did "#usermod -G users herman".
I was trying to add herman, that main superuser aka the first created user, to the users group, but the command ended up adding to users and only users, so I was degrouped from the other groups that I was in. I don't know what groups they were, but it was a fresh install. Could somebody tell me which groups the main user should be a members of other than admin. 

Thanks Herman

---

### Post by tonyr on 2006-05-06
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by kzutter on 2006-05-06
besides the the group that is my username, I am in

 I am in:
adm tty lp dialout cdrom floppy audio dip video plugdev users lpadmin scanner admin saned


I am not sure if users was a default group - I think I created it

---

### Post by tonyr on 2006-05-06
...and you probably want to use **gpasswd** from the command line,
or the user/groups management utility from the System menu...

---

### Post by Magnum818 on 2006-05-06
Thanks everyone, i'm back to the way I was before.

---

