---
title: "How to change login name and user name?"
date: 2011-06-29
forum: General Help
---

### Post by KennyGJE on 2011-06-29
I want to change my login and user name.
How do i do this? I've tried
```
usermod -l login-name old-name
```
but then I get the message:
```
usermod: user ekkabreke is currently logged in
```

I also want to change my own name, because I'm giving this computer to my step-mother :)

---

### Post by pqwoerituytrueiwoq on 2011-06-29
```
usermod -l newname -m -d /home/newname oldname
```
[http://ubuntuforums.org/showthread.php?t=877246](http://ubuntuforums.org/showthread.php?t=877246)

---

### Post by furtypajohn on 2011-06-29
You'll have to log out of the user you want to change (ekkabreke) and log in as another user.

You can create a temporary user to use to do this and use sudo when running usermod.

System -> Administration -> Users and Groups

To create the user, and also the change the user's actual name.

Or you can open a terminal using Ctrl+Alt+F1 and log in as root and use usermod that way.

First you'll have to set a password for root: sudo passwd root

---

### Post by KennyGJE on 2011-06-29
> **furtypajohn said:**
> You'll have to log out of the user you want to change (ekkabreke) and log in as another user.

You can create a temporary user to use to do this and use sudo when running usermod.

System -> Administration -> Users and Groups

To create the user, and also the change the user's actual name.

Or you can open a terminal using Ctrl+Alt+F1 and log in as root and use usermod that way.

First you'll have to set a password for root: sudo passwd root

Oh god.. I did Ctrl+Alt+F1.. How do i get out of it? :p

---

### Post by Th3Blaze on 2011-06-29
Haha, I have the exact same problem, however, I have no administrative rights.

---

### Post by KennyGJE on 2011-06-29
Okok, I did it now! Great, thanks everyone!

What I did:
1. ```
useradd temp
```
to make a new fella :)
2. logged out of my main account (ekkabreke)
3. Logged in to temp
4. Ctrl+Alt+F1
5. Logged into ekkabreke in console mode
6. ```
sudo passwd root
```
7. ```
exit
```
8. logged into root
9. ```
usermod -l newname -m -d /home/newname oldname
```
10. Ctrl+Alt+F7

Hope this helps anyone else attempting this.. And thanks again! :D

---

### Post by Th3Blaze on 2011-06-29
Doesn't help me , just keeps saying unable to lock password file

---

### Post by KennyGJE on 2011-06-29
Told me that when I tried to change pw on temp as well.
It's probably because you're not admin(?)

---

### Post by furtypajohn on 2011-06-29
Guess I should have mentioned to use Ctrl+Alt+F7 to get back to the GUI :)

---

### Post by Dave_L on 2011-06-29
> **furtypajohn said:**
> First you'll have to set a password for root: sudo passwd root

That's not necessarily a good thing to do. See: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

