---
title: "I am LOCKED out of my server. HELP!"
date: 2009-07-11
forum: General Help
---

### Post by antdgar on 2009-07-11
A user on here told me to delete the SSH keys. I deleted the files called something like SSH_Host* .pub and without extension.

Well now my NX connection just died and I cannot get back in (connected -> connection closed)

And I just tried getting in via SSH (connection closed)

Is it because I deleted those files? I can confirm that the server is still running and has not crashed... I can ftp etc...

Is there anything I can do? Or is the only option to reinstall the OS on the server? (having the server owner log in is out of the question, I have private files on there etc)

---

### Post by andrewc6l on 2009-07-12
Those files are used by ssh as the key - I'm pretty sure sshd will not let you log in without those.

You could try copying the keys from a different machine's /etc/ssh directory. If you can FTP as root, you'll be able to put them in /etc/ssh. If not, you've got trouble. You might try a different way to login - I think vnc-server (if you have it installed) might not use ssh keys if you're lucky. 

In short, without physical access to the box, fixing this kind of thing is hard. You're basically looking for holes in Linux to exploit to let you log in.

---

### Post by Warren Watts on 2009-07-12
Is your server headless?  

If not, can you log in locally, directly on the server itself?  From there you could uninstall and then reinstall SSH using apt and just build new keys.

---

### Post by Frugoo Scape on 2009-07-12
> **Warren Watts said:**
> Is your server headless?  

If not, can you log in locally, directly on the server itself?  From there you could uninstall and then reinstall SSH using apt and just build new keys.

Yeah, I agree. Those steps need to be taken if only he has remote access.

If it's at a data center, your going to have to get a tech to do the work. :/

---

