---
title: "Authentication failed"
date: 2012-02-03
forum: General Help
---

### Post by MadPoet on 2012-02-03
Hi guys! I think I have created a big problem with my root password. It started when I decided to create a new user account for my girlfriend. Since mine was the only account, I had Ubuntu log in automatically. I removed it and, to cut short my log in time, decided to remove my user password as well. And this, I think, generated the problem. Now, every time I try to install something from the software center or change something that requires admin authentication, I get an authentication failed error. I tried to leave a blank space (it seemed the logical thing to do, since I don't have a password) or use the old password, both to no avail. I have access to the option "change password" in the user account menu, but the change button in it is always greyed out, no matter what I do. I didn't want to have to reset the password; I'd much prefer to remove the need of authentication completely. Is that possible? Is there any other way to solve this?

---

### Post by Yazolight on 2012-02-04
Hello guys! I have exactly the same problem as mentionned above, apart that I didn't wanted to create a new user, just to remove the password. Now I cannot change it anymore, neither install new program. I tried to change the password (esc when booting, then "passwd username", didn't work. Any idea? :)

---

### Post by raja.genupula on 2012-02-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

reset the password by  using that .

---

### Post by Yazolight on 2012-02-04
Thanks for your reply!

Unfortunately when I do this I get a

passwd: Authentication token manipulation error passwd: password unchanged

Which make me really sad :o

---

### Post by MadPoet on 2012-02-05
That solution didn't work for me either, I had the same error. Curiosly, I managed to solve the problem simply by using the passwd username command in the terminal. I'll leave the thread open since Yazolight still hasn't managed to solve it.

---

### Post by bfckarlos on 2012-02-06
Thanks MadPoet

Just been trying to reset mine, didn't work through recovery mode, but did in terminal.

---

### Post by wsalopek on 2012-04-09
> **MadPoet said:**
> That solution didn't work for me either, I had the same error. Curiosly, I managed to solve the problem simply by using the passwd username command in the terminal. I'll leave the thread open since Yazolight still hasn't managed to solve it.

Madpoet...could you explain in detail what you did?  

I'm a Linux/ubuntu newbie and don't know what the "passwd username command" is.

Thanks...

---

### Post by yanes on 2012-05-05
please explain , 
i have the same problem

---

### Post by rangeeli on 2012-05-05
just type "passwd" in the terminal and it will ask for a new UNIX password. Try this.

---

### Post by yanes on 2012-05-05
>> Open a terminal :
>> enter : > passwd <YourUserNames>
you'ii be asked for NEW password 
>> Then enter a new password 
>> re-enter this password to confirm 
And it's done ! 

GOOD LUCK !

---

