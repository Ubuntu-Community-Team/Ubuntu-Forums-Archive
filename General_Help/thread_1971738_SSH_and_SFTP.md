---
title: "SSH and SFTP"
date: 2012-05-02
forum: General Help
---

### Post by dsmo223 on 2012-05-02
Is there a way that I can transfer files from my local machine to a machine that I am currently connected to via ssh? I often remote into my university's server useing a command similar to ssh [email]server@university.edu[/email], but if I want to transfer files, I either have to run filezilla, open another terminal, or close the ssh connection and run a command such as sftp [email]server@university.edu[/email]. I would like to be remotely connected to the server via ssh and get or put files at the same time. 

Thank you for any help.

---

### Post by agillator on 2012-05-02
If I understand your question correctly, there should be no reason you cannot have ssh and scp sessions running simultaneously (or sftp or whatever). This is assuming, of course, that the machine you are logging into does not specifically block this for some reason.

---

### Post by sj1410 on 2012-05-02
you cannot transfer files on a open ssh connection, you have open a new scp or sftp session.

---

### Post by dsmo223 on 2012-05-03
OK, Thank you.

---

