---
title: "Super User Password!"
date: 2010-12-17
forum: General Help
---

### Post by simsym05 on 2010-12-17
Dear all,

I need you help, 
i'm using ubuntu 9.10 inside windows;
in the prompt when i type the command su  to enter the root account, it is asking me to enter the password, but the problem i never configure a password for root account, i only have a password for my session that this password is invalid for this command

How can i have the password for root account please?

Thanks in advance.
Samy

---

### Post by Dave_L on 2010-12-17
See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cgroza on 2010-12-17
If you do not have serious reasons to enable it you should not. I think this default behavior is a security mesure.

---

### Post by simsym05 on 2010-12-17
Thank you very much for your help 
i will try to set the passwd and i will post the result here,

Regarding the question if i really need a root account, i think yes, because i'm preparing the LPIC101-102 and some commands need a root account, 

Thank you again for your help :-) :)

---

### Post by simsym05 on 2010-12-18
Good evening

Thank you very much again for you help,

i found another command (My instructor informed me about this command)

to have access to root command without setting a password for this account, we may use this:

$sudo -s
Enter Password:
here i can put my password account (not root account)

and it is working.

Regards.
Samy

---

### Post by CharlesA on 2010-12-18
The prefered method is using ***sudo -i*** to log into a root shell, not setting a root password and then logging into the root account.

---

### Post by simsym05 on 2010-12-18
> **CharlesA said:**
> The prefered method is using ***sudo -i*** to log into a root shell, not setting a root password and then logging into the root account.

So what is the difference between the 2 commands, please:

$sudo -s  &  $sudo -i

---

### Post by CharlesA on 2010-12-18
> **simsym05 said:**
> So what is the difference between the 2 commands, please:

$sudo -s  &  $sudo -i
It's listed on the wiki page linked in post 2.

***sudo -s*** starts a root shell with the current envirnoment variables.

***sudo -i*** starts a root shell as if you were logging in as root.

Using sudo -s can sometimes cause permission problems.

---

### Post by simsym05 on 2010-12-18
> **CharlesA said:**
> It's listed on the wiki page linked in post 2.

***sudo -s*** starts a root shell with the current envirnoment variables.

***sudo -i*** starts a root shell as if you were logging in as root.

Using sudo -s can sometimes cause permission problems.

Thank you very much for your help :)

---

### Post by CharlesA on 2010-12-18
Don't forget to mark the thread as solved from thread tools. :)

---

### Post by simsym05 on 2010-12-18
you right, but i can't find this thread :)

---

### Post by CharlesA on 2010-12-18
It's at the top of the thread. :)

---

### Post by simsym05 on 2010-12-18
Can you give me a screen shot please?

it is my first topic, and im searching this thread without success

---

