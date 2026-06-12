---
title: "Annoying passwords"
date: 2011-03-14
forum: General Help
---

### Post by Beowolf64 on 2011-03-14
Is there any way not to type password each time I use synaptic or sudo? Thank you.

---

### Post by jerome1232 on 2011-03-14
Yes

[https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo](https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo)

edit: User beware though, I believe if nothing else it's nice to get prompted when a program is requesting access to system files.

Think what malicious scripts/add-on's can do to your system when they don't have to ask you for permission to access any system file. Just my 2 cents thrown in.

---

### Post by kanikilu on 2011-03-14
I don't mean to be rude, but I have a feeling that people who can't find easily accessible documentation like this ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)), probably shouldn't be running as root or changing the sudo config to NOPASSWD...

As always, read the disclaimers, and be sure you **need** to do this, and can make the changes without breaking your system.

---

### Post by jerome1232 on 2011-03-14
There is a good reason there is a big, fat, yellow disclaimer at the beginning of that how to.

Perhaps a better route would be to allow nopasswd to a few specific applications which you use often.

That would be the best option if you really can't be bothered with typing your password in for frequently done system tasks.

---

### Post by Beowolf64 on 2011-03-15
It is my home PC. Nobody but me uses it. I like the idea of sudo instead of root, but don't want to type password every time I use synaptic or anything from administrative toolkit.

Maybe there is a way to extend 15 min time-out until the session end. As I said, it is home PC and I never let it on overnight.

---

### Post by TBABill on 2011-03-15
The point isn't that someone has to physically be in the same location as your computer to create functions that can be malicious. By removing the password, anyone remotely can still obtain access to the machine if they write code that you download and enable because your password protection step was removed out of "inconvenience". Living alone is no protection against something in the form of malware or other malicious code from becoming active on your machine and accessing those items you normally need to be root to do. It's like locking the door, but leaving it open. You have a password to protect you and the machine from accidentally taking dangerous steps, but then don't want to be bothered with using it so you bypass it.
 
Not trying to be rude, just expressing that it's not difficult to access an unprotected machine. And if any of your logins and passwords are held by your browser or some other file.....well, you know the rest.  Just like you shouldn't operate as root unless necessary, nor should you bypass root protection without specific need to do so and full understanding of the ramifications of those actions. "Don't like to enter the password" would not, in my book, be a justifiable reason to remove system protection, but to each his/her own.

---

### Post by oldos2er on 2011-03-15
> **Beowolf64 said:**
> Maybe there is a way to extend 15 min time-out until the session end. As I said, it is home PC and I never let it on overnight.

Sudo timeout is configurable, [http://ubuntuforums.org/showthread.php?t=851828](http://ubuntuforums.org/showthread.php?t=851828)

---

