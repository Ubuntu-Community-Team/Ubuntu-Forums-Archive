---
title: "how to lock a a folder/Directory..?"
date: 2010-10-28
forum: General Help
---

### Post by tajiknomi on 2010-10-28
[SIZE=2]hi,
its look like ordinary question..i want to know how to** lock a directory** in such a way that it **require password** for unlocking(by entering to that directory)

how can i do this...

thats all...


thankx
[/SIZE]

---

### Post by matt_symes on 2010-10-28
Hi

Here is one solution

[http://www.liberiangeek.net/2010/08/create-hidden-password-protected-folders-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/08/create-hidden-password-protected-folders-ubuntu-10-04-lucid-lynx/)

Kind regards

---

### Post by SecretCode on 2010-10-28
encfs (encrypted file system) is probably what you need, and cryptkeeper is a handy front end to it. [Read]("http://tuxtweaks.com/2009/03/create-an-encrypted-folder-in-ubuntu-with-cryptkeeper/") [about]("http://www.ubuntu-unleashed.com/2007/08/howto-encrypt-your-private-files-with.html") it. Install from the repositories.

eta: same as suggested by matt_symes

---

### Post by tajiknomi on 2010-10-28
[SIZE=2][I]thanks 4 help..

I Got it :P.
[/I][/SIZE]

---

### Post by vaskark on 2010-10-28
Cryptkeeper works great, except it puts 2 icons on my desktop - a folder and a drive. And it won't let me unmount them or delete them. Any advice?

---

### Post by vaskark on 2010-10-28
Nevermind. I see how to delete them now :)

---

### Post by tajiknomi on 2010-10-29
[SIZE=2]*Right Click on its icon and their you will see delete option along that Drive....*[/SIZE]

---

### Post by satish_j on 2010-10-29
I have some questions..
1. If i do 'ls' from command to the encrypted directory,will it show the contents of it?
2. Will the cyptkeeper ask for password if the encrypted directory is accessed from Live CD??

---

### Post by tajiknomi on 2010-10-29
[SIZE=2][I]Lets try it...create a folder and check it out from live-Cd ..thats all:P

I hope it should ask you for Password...

moreover, i have a single question and that is, 

"Any 1 can delete my Encrypt-folder by just click delete from the icon,without **authentication.!!!**....isn't that a bug..?"
[/I][/SIZE]

---

### Post by satish_j on 2010-10-29
> **tajiknomi said:**
> [SIZE=2][I]
"Any 1 can delete my Encrypt-folder by just click delete from the icon,without **authentication.!!!**....isn't that a bug..?"
[/I][/SIZE]

I think the answer to this question is to create the encrypted folder at some wierd location(like /bin or /etc)**--assuming you have(Sudo) rights to those paths--**where the chances of deletion by other users are minimal.

---

### Post by tajiknomi on 2010-10-29
[SIZE=2][I]Other user can simply right-click on Cryptkeeper and can delete it simply by pressing delete option without **authentication of Password**,

Moreover,One can also trace the location...by right-clicking cryptkeeper icon and select **Information** option...isn't that strange..?
[/I][/SIZE]

---

### Post by satish_j on 2010-10-29
iam going to try it later today when i get home..

---

### Post by tajiknomi on 2010-10-29
[SIZE=2]*ok..then let me know :P*[/SIZE]

---

