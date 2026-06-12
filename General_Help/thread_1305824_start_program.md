---
title: "start program"
date: 2009-10-30
forum: General Help
---

### Post by James Dee on 2009-10-30
Hello everybody,

I installed AbaqusCae in this location /opt/abaqus675.
If I want to start the program I should write in terminal: ```
/opt/abaqus675/6.7-5/exec/abq675.exe cae
``` or if I want to start a job: ```
/opt/abaqus675/6.7-5/exec/abq675.exe job=*"job name"*
```

Is it possible to write some code or something else that I can start progam from different location (/media/DATA or $HOME or ...) with command ```
abq675 cae
``` or start job with command ```
abq675 job=*"jobname"*
```

Thnx...

---

### Post by phillw on 2009-10-30
Polymers, eh ?? that was a while back for me !!!

Anyways, there's a forum for them & a thread for abaqus and 9.10 :-D

[http://polymerfem.com/](http://polymerfem.com/)

That should answer your questions.

Regards,

Phill.

---

### Post by P4man on 2009-10-30
Add /opt/abaqus675/6.7-5/exec/  to your path:
[http://opencheese.com/2009/05/11/ubuntu-how-to-add-a-path-to-your-path-list-in-terminal-bashrc-file/](http://opencheese.com/2009/05/11/ubuntu-how-to-add-a-path-to-your-path-list-in-terminal-bashrc-file/)

Or you could create an alias:
[http://ss64.com/bash/alias.html](http://ss64.com/bash/alias.html)

---

### Post by James Dee on 2009-10-30
> Or you could create an alias:
[http://ss64.com/bash/alias.html](http://ss64.com/bash/alias.html)

alias rules!!!

Thnx P4man...
:popcorn:

---

