---
title: "sudo date &gt;&gt; serverup.txt"
date: 2012-07-11
forum: General Help
---

### Post by Mr.Dee on 2012-07-11
sudo date >> serverup.txt
-bash: serverup.txt: Permission denied

 
I know this works, but it doesn't work specifically for the file serverup.txt.  I ran a test sudo date >> test.txt  and it worked fine.  Can someone shed some light on this?  I did some googling and forum searches, but I get too many results for "permission denied" that are not related.
 
I'm setting up crontab to run a script with ssmtp to email me that my server is up.
 
Thanks in advance!

---

### Post by spjackson on 2012-07-11
It's the shell running the command that does the redirection. That shell is running as you, without root privileges. So...
```

sudo bash -c "date  >> serverup.txt"

```

---

### Post by Mr.Dee on 2012-07-12
i at some point edited the text file as sudo, so now it requires sudo... I deleted the file and created another without sudo. Problem solved!

---

