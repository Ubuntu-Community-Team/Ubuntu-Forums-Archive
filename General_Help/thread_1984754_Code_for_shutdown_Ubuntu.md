---
title: "Code for shutdown Ubuntu"
date: 2012-05-22
forum: General Help
---

### Post by albertone74 on 2012-05-22
Dear All,
I don't know if this is the right session in the forum so I apologize for that.
I would like to shutdown the system by using a launcher (is it called like that?) on my desktop so that when I click on it Ubuntu will shut down automatically. Would you please be so kind as to let me know the code for it? 
Many thanks in advance for your kind help

---

### Post by sudodus on 2012-05-22
There is already such a button. It looks different in different versions and flavours of Ubuntu. It probably looks like the typical power-off symbol of electronic equipment, and is probably situated at one of the corners of the screen.

You can make a launcher yourself, but it will probably require that you enter the password. You can use the command

```
sudo poweroff
```

---

### Post by Lynceus on 2012-05-22
If the code above me doesn't work try

sudo shutdown -h now

---

### Post by albertone74 on 2012-05-22
Hi guys,
thanks for the propmt response. Unfortunately I cannot try right now.
Sorry I am not too familiar with this sort of things. What would it be the complete code so that I can copy and paste it in he filename.sh?
Also I would like to avoid to be asked for the password. Ideally I would like to click on the file and that's it. Thanks for being patient with me:)

---

### Post by DingusFett on 2012-05-22
As others have said, sudo shutdown -h now or sudo poweroff

---

### Post by wojox on 2012-05-22
> **albertone74 said:**
> 
Also I would like to avoid to be asked for the password. Ideally I would like to click on the file and that's it.


Pretty self explanatory [Shutting Down From The Console Without A Password]("https://help.ubuntu.com/community/Sudoers#Shutting_Down_From_The_Console_Without_A_Password")

---

