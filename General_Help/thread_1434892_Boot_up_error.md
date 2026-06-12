---
title: "Boot up error"
date: 2010-03-20
forum: General Help
---

### Post by Fred the Penguin on 2010-03-20
When I boot up my laptop I get an error message on Lucid alpha 3. I don't have time to read the whole thing. It is only 3 or 4 lines long. The last part is the only thing I have time to read.  It says: error probing smb2.  Could someone please help? I think it slows down my boot. It would also be nice for someone to tell me how to copy down the whole message.

---

### Post by louieb on 2010-03-20
Are you fully up-to-date? Have you checked [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") . I booted into Lucid this afternoon - no panels - its still getting bug fixes. After running update and restarting GDM panels came back. 

Check the Luicd section of  [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") - see if anyone else has reported the same problem - if there is a workaround - it will be found there.

---

### Post by Fred the Penguin on 2010-03-21
Thanks. I am fully up to date, and I will check the places you listed.

---

### Post by phen0m on 2010-03-21
You should be able to find that message in your logfiles somewhere

System->Administration->Log File Viewer
Check the *messages* or maybe *syslog*s

---

### Post by Fred the Penguin on 2010-03-21
Thanks phen0m.  I found the error in syslogs. It is: Mar 21 21:14:26 jonathan-laptop kernel: [   17.912253] nForce2_smbus 0000:00:03.2: Error probing SMB2.              
           If someone could help me fix this I would appreciate it.
                  I realized that this thread would fit better in the Lucid section of Development & Programming, so I am marking this thread as solved and reposting my problem there.

---

