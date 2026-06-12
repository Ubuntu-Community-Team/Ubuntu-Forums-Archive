---
title: "used command"
date: 2010-05-08
forum: General Help
---

### Post by mahsa2010 on 2010-05-08
Hello everyone,
I want to see all of the commands that I have used in a specified date, and between for example 8am to 10am. Is there any command for this?
Thanks
Mahsa

---

### Post by P4man on 2010-05-08
the command is 

```
history
```

but by default it shows no timestamps. To enable those:

[http://www.rootdev.com/tech/timestamps-in-bash-history](http://www.rootdev.com/tech/timestamps-in-bash-history)

---

### Post by mahsa2010 on 2010-05-16
Thank you for your reply.
What a great command history is!!!!
I am the administrator of an ubuntu system, I want to know which commands the other user have used, is it possible by history or something else?
Thanks
Mahsa

---

### Post by Ozymandias_117 on 2010-05-16
> **mahsa2010 said:**
> Thank you for your reply.
What a great command history is!!!!
I am the administrator of an ubuntu system, I want to know which commands the other user have used, is it possible by history or something else?
Thanks
Mahsa

Do they log in as root? Or do you have them using sudo? If they log in as root, it will just be jumbled in that history, if they use sudo, you can check their accounts history files.


Also: History defaults to something like the last 500 commands then starts deleting.

---

### Post by mahsa2010 on 2010-05-22
No, they are not root. I have created some accounts for them which does not own administrative rights. For example a user named "guest". when I type 
> history guest
nothing comes out. Did you mean this? Or someone logged in as "guest" can see this?
Thank you!

---

