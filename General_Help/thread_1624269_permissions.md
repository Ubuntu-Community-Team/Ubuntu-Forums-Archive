---
title: "permissions"
date: 2010-11-17
forum: General Help
---

### Post by PsyclonJohn on 2010-11-17
Sorry if this is the wrong place to post. I'm new to the forums.

I'm trying to install a script and I need to change the permissions of a file within the script, but I am being denied from doing so. I know that I could change the password of ROOT, but I don't really feel like going through that again when I can just use 'gksudo nautilus' in Terminal.  

How can I change the permission without being on Root?

Thanks in advance!

---

### Post by nothingspecial on 2010-11-17
sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by gyre007 on 2010-11-17
> **PsyclonJohn said:**
> Sorry if this is the wrong place to post. I'm new to the forums.

I'm trying to install a script and I need to change the permissions of a file within the script, but I am being denied from doing so. I know that I could change the password of ROOT, but I don't really feel like going through that again when I can just use 'gksudo nautilus' in Terminal.  

How can I change the permission without being on Root?

Thanks in advance!

If you own the file you don't need to use sudo to run chmod on some file...however if you don't own it sudo is required - you can't have every user changing permissions to each other - that's a security risk. However there is a workaround - editing the /etc/sudoers files and setting nopasswd for certain user(s) like you are (I know you can even select the commands you want to have no passwd access to run them)...however I would strongly discourage you to do this because a) it's a security risk - you are giving a user unlimited access to certain set of commands
b) you might regret it later when you mess up something accidentally and you;ll be wondering what went wrong and why :)
Don't know if that answers your question though...

---

### Post by PsyclonJohn on 2010-11-17
Thank you, it worked :)

---

