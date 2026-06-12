---
title: "SSH &amp; create users"
date: 2009-11-20
forum: General Help
---

### Post by Gordonisnz on 2009-11-20
hello, I have SSH installed on my Linux box :-
secure shell client and server (metapackage)

i think SSH is going - as i can SSH into it & it asks me my username / password. 

HOWEVER, I enter my linux admin / (only) account name / password & it doesn't go.

i'll assume you need to set up SSH users seperately. 

Q1 :- How do we set up SSH users - I've Googled & it gives me information as to things a user can do, But i can't find anywhere to tell me how to create / admin a user in the first place.

Q2 :- Is there a tutorial (easy) on how to use SSH to get / retrieve files off the other machine & save to the one you're on.. ?

---

### Post by XCan on 2009-11-20
When you use ssh, you should use the user you created when you installed your linux box. For adding new users, you can simply use the "adduser" command.

Retrieving files can be achieved through tons of various programs. For one, Nautilus can connect to sshd and mount it. You could also use an FTP app support SFTP, for example, gftp, simply select SFTP as the protocol and connect!

---

