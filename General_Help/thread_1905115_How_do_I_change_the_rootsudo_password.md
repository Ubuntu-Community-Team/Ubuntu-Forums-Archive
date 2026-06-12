---
title: "How do I change the root/sudo password?"
date: 2012-01-06
forum: General Help
---

### Post by mikeee99 on 2012-01-06
This may be a stupid question, but I have been trying to find where I change the root password. I'm sure it's somewhere obvious, but I've searched and can't find an answer anywhere. If someone could explain how to change it, that would be great! 

I am running Ubuntu 11.04 in classic display mode. 

Thanks in advance!

---

### Post by Catharsis on 2012-01-06
Become the superuser```
sudo su
```and then run```
passwd
```After you've changed it, just enter 'exit' until the terminal closes.

---

### Post by raja.genupula on 2012-01-06
open your terminal and change to root mode by typing

**sudo -i**

and then type **passwd **
it will prompt for new password type there what is the new password you want to give . 
that will be the new password .


all the best.

---

### Post by jwbrase on 2012-01-06
The password for sudo is simply the password for the account you're trying to invoke sudo with (as long as that account has the appropriate administration priveleges).

You can change your own account's password under System -> Administration -> User's and Groups (with Gnome 2. I don't know how you'd do it under Unity), or with the command "passwd" in a terminal.

Ubuntu by default does not have a root password (because using sudo is more secure than logging in as root directly, for various reasons), and the forum rules forbid telling how to set a root password (on the theory that those who can't figure out how to do it themselves are likely to do themselves more harm than good by setting a root password).

---

### Post by magodfrey on 2012-02-21
This post is the closest I can find to my own problem (other than a post answering how I can be so incredibly stupid in the first place).

When messing about in System Settings > User Accounts, I very stupidly made my own account a Standard Account Type, taking away my own administration priviledges I now find myself unable to 'Administer'. I have no logical way to change my priviledge status back to what it should be. As the only administrator on my small home network I have effectively killed the system.

Now without the administration ability I am amazed at the frequency of its need during the day. Is there any way to get my sudo priveledge back onto my account?

If you are able to answer this, my thanks and opologies in equal measure.

---

