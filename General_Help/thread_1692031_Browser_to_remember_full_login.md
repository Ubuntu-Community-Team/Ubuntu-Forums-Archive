---
title: "Browser to remember full login?"
date: 2011-02-20
forum: General Help
---

### Post by Mariane on 2011-02-20
It's a minor annoyance but my browsers now don't seem to be able to remember a login and password unless I give them a hint by typing the first letter of the login name. An example is this site, if I type 'M' in the username field the rest fills in automatically. 

Browsers: seamonkey and firefox. 

How can I set them up so that when I access the site the username and password are written automatically, immediately? 

Mariane

---

### Post by Old *ix Geek on 2011-02-20
Have a look at your stored passwords. It's possible there are multiple entries--different, multiple entries--for some sites, therefore you're having to give part of the info before it recognizes the right one.

In SeaMonkey:
```
Tools | Password Manager | Manage Stored Passwords | Show passwords
```

and look for duplicates.

---

### Post by Mariane on 2011-02-20
Done. No duplicates.

---

### Post by Habitual on 2011-02-20
[https://lastpass.com](https://lastpass.com) has a great addon for full logins.

---

### Post by Mariane on 2011-02-21
lastpass wants me to create an account and to store my passwords away from my computer! So much for privacy... No thanks. What if they get cracked, the crackers will get everyone's passwords, including bank account passwords etc... 

Mariane

---

### Post by Mariane on 2011-06-03
Any other ideas? And for Firefox? 

Mariane

---

### Post by Habitual on 2011-06-04
> **Mariane said:**
> lastpass wants me to create an account and to store my passwords away from my computer! 
Yes, you need an account. 

Did you even goto their website and read anything?
Ignorance is Bliss, I guess. Good Luck.

[https://lastpass.com/whylastpass_technology.php](https://lastpass.com/whylastpass_technology.php)

---

### Post by pqwoerituytrueiwoq on 2011-06-04
you could use greasemonkey and make a simple script but the logins will not be encrypted on your computer in the script but that is were a encrypted file system come in handy
```
documet.getElementById('username').value="my name";
```
or you can ask someone to make it and then fill your login info into it

---

### Post by Mariane on 2011-06-05
> **Habitual said:**
> 
Did you even goto their website and read anything?
Ignorance is Bliss, I guess. Good Luck.


So much for me, I glanced at their website and thought it was some site like one I had seen before which stores your passwords for you. It isn't. It offers a plugin for firefox (and other browsers) to give them the equivalent of Konqueror's wallet. Konqueror can store all the passwords you want in a single wallet which you open with a master password. There are probably open-source Firefox plugins which can do this also. 

It is still not what I wanted.

> **pqwoerituytrueiwoq said:**
> you could use greasemonkey and make a simple script but the logins will not be encrypted on your computer in the script but that is were a encrypted file system come in handy
```
documet.getElementById('username').value="my name";
```
or you can ask someone to make it and then fill your login info into it

This looks more promising if I can pull it off. Hum, big "if". 

Actually I was hoping someone would tell me to type "about:config" in the url bar and to change the value of some a variable there. The problem is there are very many variables that can be changed in this way and changing the wrong one can cause problems, so it is better to ask first. 

Mariane

---

