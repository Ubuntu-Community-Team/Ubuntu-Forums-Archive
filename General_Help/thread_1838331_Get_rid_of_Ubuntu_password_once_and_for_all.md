---
title: "Get rid of Ubuntu password once and for all"
date: 2011-09-03
forum: General Help
---

### Post by Wozza365 on 2011-09-03
Hi there, i have tried so hard over recent days to get rid of the password completely and everytime i change something, it changes back to its original 

i have tried majority of things that have come up including ways of doing it via terminal 'password and encription keys app', 'users and groups' and other things and none of it works

can anyone give me a final solution on how to sort this, its driving me crazy! i have tried ever so hard to like ubuntu but everytime a new problem comes up and it seems there is never a way of fixing it

64 bit Ubuntu 11.04 << any other info please feel free to ask

---

### Post by gandaran on 2011-09-03
which password do you want to remove, administrator root, login or just the keyring password, getting rid of the keyring password is easy and there are a lot of threads on how to do it, type keyring in the forum search box.

---

### Post by Wozza365 on 2011-09-03
all of them, i dont want any passwords, i have tried getting rid of the keyring password via multiple roots and none have worked

---

### Post by haqking on 2011-09-03
> **Wozza365 said:**
> all of them, i dont want any passwords, i have tried getting rid of the keyring password via multiple roots and none have worked

if you disable or remove your password you leave yourself open to allsorts of potential issues.

It is not about attackers from outside only, it is also about services and scripts running under admin privelege.

which is why sudo exists.

it is possible to have a blank password but the canonical model of using sudo is supported here.

see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for information sudoers file where things may be changed see here [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

The information required to remove your password or set it to blank is contained in those files, like i said not recommened

If it is the keyring password that bothers you then try here [http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/)

or it is because you have your system to automatically login which is why it asks.  If you dont have autologin then the keyring shouldnt bother you.

I also suggest you read the following stickies

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by kiddykoff on 2011-09-03
Maybe if you told us why you don't want a password we could offer some alternatives. Most people will tell you that having a good strong password is highly recommended.

---

### Post by Wozza365 on 2011-09-03
i suppose i could live with the sudo password as long as its only the one in the terminal (i dont use it much)

every other password i want removed
i have a pretty slow system and im removing the passwords to speed up load times etc

i think i turned on auto login on although i dont turn off the system every time, so everytime i close my laptop lid and open it, i still get a request for my password

---

### Post by haqking on 2011-09-03
> **Wozza365 said:**
> i suppose i could live with the sudo password as long as its only the one in the terminal (i dont use it much)

every other password i want removed
i have a pretty slow system and im removing the passwords to speed up load times etc

i think i turned on auto login on although i dont turn off the system every time, so everytime i close my laptop lid and open it, i still get a request for my password


Like i said remove auto login then.

Go to system>admin> login screen

or adjust to suit your version and turn off automatic login.

This way when you login to your system it automatically unlocks your keyring.

The only password you should ever be asked for in the system is your login password (if you are in sudo group) to carry out admin tasks such as when in terminal or making system changes etc.

Make sure you read the links i posted so you fully understand the use of sudo and the sudoers file.

Like i said it is possible to enable no password but that circumvents the canonical security model and will lead to supports problems down the line i am sure ;-)

peace

---

