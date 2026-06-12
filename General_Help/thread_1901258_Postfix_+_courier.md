---
title: "Postfix + courier"
date: 2011-12-28
forum: General Help
---

### Post by s031886 on 2011-12-28
Hello everyone,

I'm quiet new here and I'm still a beginner with linux but I hope someone here can help me out with my little problem.

For school we have to configure our own linux server with Bind9, Postfix, OTRS and drupal. 

Everything is quit OK now I think but there are 2 things I would like to know.

1. To see if a user has mail I now use the command: "mail"
Then I installed courier pop3/imap and changed Mboxes to Maildir but when I want to check for new email I always have to this first: MAIL=/home/username/Maildir
How can I solve this?


2. Is it possible to sent emails from my server to external domains like gmail or hotmail?


Thanks in advance for the help.

---

### Post by Paddy Landau on 2011-12-28
Question 1:

You can set permanent environment variables for the terminal in your file [FONT=Fixedsys]~/.bashrc[/FONT]. Open that file (e.g. with Text Editor) and, at the end of the file, add the following command:
```
 export MAIL="/home/${USER}/Maildir"
```If you need to set this environment variable for the entire session, not just in the terminal, add that line instead to the file [FONT=Fixedsys]~/.profile[/FONT].

If you need to set this environment variable for every user, not just yourself, add that line instead to the file [FONT=Fixedsys]/etc/profile[/FONT].

Question 2:

See this post:
[http://ubuntuforums.org/showthread.php?t=1698634](http://ubuntuforums.org/showthread.php?t=1698634)

---

### Post by s031886 on 2011-12-29
Thank you very much Paddy Landau,

My first problem is solved.


For my other question I will read the topic from the link you gave me and see if I can work it out.


Thanks and enjoy the holidays.

---

