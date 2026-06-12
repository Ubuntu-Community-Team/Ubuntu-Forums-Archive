---
title: "ssh into my accout elsewhere, copy files to it"
date: 2009-08-22
forum: General Help
---

### Post by iochinome on 2009-08-22
hey guys, so i have this text file that i wrote on my home computer that needs to be transferred to my account on a lab computer that i can ssh into. how do i copy this text file and put it in my account that i sshed into? thanks!

---

### Post by Zack McCool on 2009-08-22
The easiest way is to use an SFTP client like FileZilla, but Nautilus can do it as well.  Just click Places...   Connect to Server...   Change the service type to SSH, and enter your information.

You can also do it all from the command line, but I'd imagine you'd find this easier...

---

### Post by kjohri on 2009-08-22
You can use sftp ffrom command line,

sftp user-name@host-name

The remote machine will ask for password. Once you give password, a SFTP session will start. You can then use the the SFTP commands,

put filename
bye

---

### Post by geirha on 2009-08-22
You can also use the scp command, or even the ssh command.
```

scp localfile user@host:path   # If you omit path (i.e. user@host:) it will upload 
                               # it to the homedir. Do not omit the colon.

# Piping the file over
ssh user@host "cat >filename" < localfile

```

---

