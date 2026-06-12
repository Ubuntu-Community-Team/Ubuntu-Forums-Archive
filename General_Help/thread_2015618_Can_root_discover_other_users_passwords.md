---
title: "Can root discover other users passwords"
date: 2012-07-03
forum: General Help
---

### Post by techbrainless on 2012-07-03
I am non-root user in ubuntu machine , I have noticed that password and encryption keys contains all my entered password.
Which shoked me !!!!!!!!!!!!!!!!!!!!!!!!!!!

My questions are :

1 . I have found in my search that password and encryption keys are stored in the files login.keyring , user.keystore (/home/myusername/.gnome2/keyrings) , it seems that they are encrypted .
is there any way to view the contents of this two files , is there any way to view the passowrds inside above 2 files

2 . Is there any way or security whole in which the root user can access (system menu --> preferences --> passowrd and encryption keys) of other users (other root users , non-root users,....etc) . of course for the the same machine?

3 . Is there any way or security whole in which the root user can discover the passwords like ubuntu login passowrd , keyring password , browsing sites passwords (taking in consideration never remember passwords for all sites , and  clearning browsing history) entered by other users(other root users,non-root users,,,,etc). of course for the same machine?

I really do need your detailed reply for my questions , all advises and feedbacks are most welcome

---

### Post by ofnuts on 2012-07-03
> **techbrainless said:**
> I am non-root user in ubuntu machine , I have noticed that password and encryption keys contains all my entered password.
Which shoked me !!!!!!!!!!!!!!!!!!!!!!!!!!!

My questions are :

1 . I have found in my search that password and encryption keys are stored in the files login.keyring , user.keystore (/home/myusername/.gnome2/keyrings) , it seems that they are encrypted .
is there any way to view the contents of this two files , is there any way to view the passowrds inside above 2 files

2 . Is there any way or security whole in which the root user can access (system menu --> preferences --> passowrd and encryption keys) of other users (other root users , non-root users,....etc) . of course for the the same machine?

3 . Is there any way or security whole in which the root user can discover the passwords like ubuntu login passowrd , keyring password , browsing sites passwords (taking in consideration never remember passwords for all sites , and  clearning browsing history) entered by other users(other root users,non-root users,,,,etc). of course for the same machine?

I really do need your detailed reply for my questions , all advises and feedbacks are most welcome
If it's the same PC that you share with others, a root user can likely install a keylogger to record all your keyboard interactions. Passwords for sites not using HTTPS are also likely sent in the clear and can be captured by anyone with access to your local network. A root user can also set up a transparent proxy and record all your web traffic, even HTTPS stuff by faking certificates (man-in-the-middle attack).

You aren't going to sleep well tonight :)

---

### Post by techbrainless on 2012-07-03
Thanks ofnuts for your reply , 

> If it's the same PC that you share with others, a root user can likely install a keylogger to record all your keyboard interactions. Passwords for sites not using HTTPS are also likely sent in the clear and can be captured by anyone with access to your local network. A root user can also set up a transparent proxy and record all your web traffic, even HTTPS stuff by faking certificates (man-in-the-middle attack).
great answer for question 3.

I will be grateful if you could provide answers for q1 & q2 also.

---

### Post by Spudd on 2012-07-03
Q3: Linux passwords are stored in whats called a hash meaning that its mathematically impossible for root to get it. However with the hash one could brute force the hash meaning they go through the many combinations of ascii text hashing each and comparing it against the hash in the shadow file. Secondly if you never remember passwords then it shouldn't be a problem other than how ofnuts described.

---

### Post by stderr on 2012-07-03
Generally speaking, wherever passwords are stored these days, they are encrypted before storage. The idea is that it should take an inordinately long length of time to "break" the encryption, assuming the algorithm to be strong enough. 

If you can get your hands on a password hash, as you certainly can with root access, then you can try a variety of common approaches to cracking the hash. Rainbow tables, dictionary attacks and brute force attacks are the usual barrage of solutions. However, if the algorithm is chosen well (or just applied enough times), and the password long enough with a good charset, then the basic answer is no. You're stumped.

---

### Post by efflandt on 2012-07-03
Main system passwords use a one-way encryption.  In other words the system can encrypt a password you give it and see if it matches the encrypted password, but you cannot decrypt the encrypted password.  With a good encryption hash, the only way to really find a password of a user is to keep guessing until there is a match. 

So don't use normal dictionary words or something easy to guess and mix it up with numbers and upper and lower case letters.

I do keep some passwords for web sites in an OpenOffice/LibreOffice document.  Not sure how that is stored or how secure it is, but it is password protected and a password or phrase is used to encrypt and decrypt the file.

---

### Post by dcstar on 2012-07-04
> **techbrainless said:**
> I am non-root user in ubuntu machine , I have noticed that password and encryption keys contains all my entered password.
Which shoked me !!!!!!!!!!!!!!!!!!!!!!!!!!!
..........

Why?, they are **your** passwords and **you** should have access to them.

---

