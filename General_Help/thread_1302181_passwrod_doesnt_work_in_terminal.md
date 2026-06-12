---
title: "passwrod doesnt work in terminal"
date: 2009-10-26
forum: General Help
---

### Post by kmrs75 on 2009-10-26
hi im kinda new about a year and i havent ever had this problem 

i just loaded the 64 bit ubuntu. 

i was trying to get flash to work but i have been struggling but that is its own issue. 

this just started and the first time when i saw it was tonight. in the terminal i type su and then it asks for a password and i get an error 

ken@ken-desktop:~/Desktop$ su
Password: 
su: Authentication failure
ken@ken-desktop:~/Desktop$ 

i know the password is correct. i even changed it in users and groups and i have checked cap locks i dont have a clue and now im worried that i cant turn off my comp can i get back into it

---

### Post by abyrne on 2009-10-26
I assume you are changing to root.  You must run 
```
sudo su
```
because the real root password is just some random hash code created on installation.

---

### Post by m_duck on 2009-10-26
The root account is disabled in Ubuntu by default as mentioned above. See [the Ubuntu Docs: Root Sudo](https://help.ubuntu.com/community/RootSudo) for more details.

Use sudo to temporarily gain root privalidges.

---

### Post by sisco311 on 2009-10-26
> **abyrne said:**
> 
```
sudo su
```
because the real root password is just some random hash code created on installation.

i would recommend:
```
sudo -i
```
to simulate a root shell.

the root password is not a random hash, it's  locked (!)
```
man passwd | less --pattern\="-l, --lock"
```

> **m_duck said:**
> The root account is disabled in Ubuntu by default as mentioned above. See [the Ubuntu Docs: Root Sudo](https://help.ubuntu.com/community/RootSudo) for more details.

Use sudo to temporarily gain root privalidges.

the root account is not disabled, the root account password is locked.

+1 for the link and +1 for sudo

---

### Post by m_duck on 2009-10-26
Thanks for clarifying. :D

---

### Post by kmrs75 on 2009-10-26
thanks everyone 

i feel stupid i knew that i was just going to fast. 

thanks again everyone

---

