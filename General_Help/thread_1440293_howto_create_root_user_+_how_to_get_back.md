---
title: "howto create root user + how to get back"
date: 2010-03-27
forum: General Help
---

### Post by ken poy on 2010-03-27
Hi today i have 2 questions:
1: after entering this question and and come back later for response how do i get back to it with the response.
i did enter a question before and with great difficulty gotten back not sure how.
since i am not sure i'll get back  please email response to
[EMAIL="kpoyneer@gmail.com"]kpoyneer@gmail.com[/EMAIL]                            thanks ken 

question 2:  i can get the response to this once question 1 is resolved. 

i have Linux (ubuntu) installed and am using it 100%.  it is fast compared to windows and has only hung once requiring a power off/on.  i do use QBasic which will not run in Linux.  i did find through a previous question, a howto QBasic on Ubuntu.  i followed the procedure and all went well until the following command.

mount c /home/ken/QBasic          ken = userid
                                                QBasic is a folder in home directory

the response is "only root can do this cmd"

this is when the system hung.  i had the dos window and the terminal window and tried
commands in both.  not sure what i did but it hung.

my problem: how do i get  create/logon to root??   
i have tried Users and Groups and cannot get  a PW entered for root which does show in the list of users.
i have tried various ways and nothing seems to work.

thanks  ken

---

### Post by snowpine on 2010-03-27
You do not need to create a root account:

```
sudo mount c /home/ken/QBasic ken = userid
```

More info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ken poy on 2010-03-27
Hi  from ken poy,  i did find my queries by using "New Posts"  and search on userid.

so i am okay now and thanks for the previous response about SUDO.  i makes sense for 
system security.             thanks ken

---

