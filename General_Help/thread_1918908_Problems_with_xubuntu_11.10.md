---
title: "Problems with xubuntu 11.10"
date: 2012-02-01
forum: General Help
---

### Post by NilPointer on 2012-02-01
Yesterday, I decided to install Xubuntu 11.10 as second distro (I already had Ubuntu 10.04 LTS). I had separate home partition, so I told installer to use it as /home. In Xubuntu, I defined same account name/pass as I use in Ubuntu.

So, main problem is that Xubuntu doesn't want to boot after installing. It's just failing somewhere and splash screen changes to console. I tried switching to tty1 and logging into it, but it fails, too. It says "cd: can't cd to /home/nilpointer".

---

### Post by NilPointer on 2012-02-02
Still can't boot into 11.10... It's problem with home partition, yes?

---

### Post by mike555 on 2012-02-02
It's not a good idea to use same /home for different versions, because /home has hidden conf. files that might mess things up........ but that said, I don't think it would stop it from starting.

---

### Post by LewisTM on 2012-02-02
One possibility is that although you have set the same user names, they don't have the same UIDs. Permissions in Linux are set per UID and usernames are just nicknames.

Run 'id nilpointer' in a 10.04 terminal and write down the numbers, repeat for other users. Then log on to a recovery console in Xubuntu and do the same. 

If they don't match you can refer to this [page]("http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/") which shows how to change usernames and IDs.

Comparing and syncing the /etc/passwd and /etc/group files from both OSes would also work.

---

### Post by NilPointer on 2012-02-02
Well, I've fixed it by reinstalling Xubuntu 11.10 with separate home folder for it. Now it boots without any problems. So, problem is solved.

Thanks for your replies.

---

