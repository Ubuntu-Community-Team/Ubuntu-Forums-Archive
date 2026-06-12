---
title: "edit motd"
date: 2011-05-01
forum: General Help
---

### Post by JBtje on 2011-05-01
Greetings,
 
I've changed my motd files (like 00-header) etc. so i get the info I want to see when i login. These files where found in /etc/update-motd.d
 
Now in /etc/ssh/sshd_conf I uncommented "Banner /etc/issue.net" and also that works as i like it to work.
 
Now there still is some weird problem :|
Each time i login on the server via SSH, I get this message:
 
```
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have mail.
Last login: Sun May  1 16:03:35 2011 from hostname...

```
 
Beside the "Last login" I dont wanna see the rest of the info... My question would be: where do i find the file that is responsable for printing that information?
 
Currently i got:
- banner (issue.net file)
- Asks for username
- Asks for password
- if password correct
- Show files from /etc/update-motd.d
- Show the message above (between de [ CODE ] tags) of which I dont know the file location!
 
 
I know I can turn of the "Last login" in the sshd_config file, but I have no clue where to turn off the rest of the info....
 
Thanx!
Jeffrey

---

