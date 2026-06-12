---
title: "mail command broken, no /etc/postfix/main.cf ?"
date: 2010-10-25
forum: General Help
---

### Post by d3v1150m471c on 2010-10-25
```

mail -s "cli test" myname@yahoo.com < file
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75

```

i have had postfix installed and i recently reinstalled it with no results. any help would be appreciated.

---

### Post by gmargo on 2010-10-25
Your postfix seems installed but not configured. Run "dpkg-reconfigure postfix" from the command line to configure it.

---

### Post by d3v1150m471c on 2010-10-25
go figure. it seems like i spend forever researching a problem and when i finally break down and make a post i find the answer 5 seconds later. anyways, i've found loads of people with this problem online with no solutions so i'll post mine here. 

i used synaptic and completely removed postfix and then reinstalled. when it asks you to configure it choose "internet site" and you should probably leave the next question for your hostname as the default. it's already written in the text field btw. next install mailx and bsd-mailx. after that your mail command should work perfectly.

---

### Post by polarise on 2012-07-30
I ran 'dpkg-reconfigure postfix' and that solved it for me. I now remember skipping this step when I installed Ubuntu.

Thank you.

PK

---

### Post by wildmanne39 on 2012-07-30
Hi, please do not create duplicate threads it dilutes the communities efforts.
Thanks

---

