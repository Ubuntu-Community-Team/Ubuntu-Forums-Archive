---
title: "Ubuntu 11.10 unable to login"
date: 2012-03-02
forum: General Help
---

### Post by Jellow on 2012-03-02
Today, while trying to get access as root (in order to change a file) I set a password for the root account. Unfortunately I gave it the same password as my personal account. 

Now I cannot access my personal account anymore. From the GUI or the terminal (pressing Ctrl+Alt+F7) I can only access the root account with the password I gave it. Then it says in the right corner above it is the guest-account. 

I tried deleting the .Xauthority file, as recommended several times in other threads, but it didn't work. Probably because I deleted it in the root (or guest?) account.

Anyone who knows how to regain access to my personal account?

Using ubuntu 11.10 oneiric, on an acer aspire 5520 series laptop

---

### Post by Jellow on 2012-03-05
Please, anyone?

---

### Post by raja.genupula on 2012-03-05
Hi you can reset your account password , please read this 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Jellow on 2012-03-05
> **raja.genupula said:**
> Hi you can reset your account password , please read this 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks, I just found that myself. It doesn't work though. It says: Error manupilating authentication token. (Or something like that, it's in Dutch.) So, what should I do now?

---

### Post by raja.genupula on 2012-03-05
[http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

edit:[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-password-change-error-910341/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-password-change-error-910341/)

---

### Post by Jellow on 2012-03-05
> **raja.genupula said:**
> [http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

edit:[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-password-change-error-910341/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-password-change-error-910341/)
Done that, now the password of my personal account is changed.

Still not able to log in. It keeps returning to the GUI, giving me the option to enter a username and then a password. My personal account and the guest account don't work, the root account does.
Once logged in as root, it says in the right top corner that it is in guest account. Is that normal?
How can I enable the other accounts again?

---

### Post by Jellow on 2012-03-05
O, bytheway, I just entered the 'user account' program and it puts my personal account under 'other accounts'. Not with 'my accounts'. I'm not sure whether that's right?

---

### Post by raja.genupula on 2012-03-05
you mean you're login screen showing as wrongs password or username  or its returning the login page everytime ?

---

### Post by Jellow on 2012-03-05
It's returning to login page all the time.

---

### Post by raja.genupula on 2012-03-05
[http://ubuntuforums.org/showthread.php?t=1340887](http://ubuntuforums.org/showthread.php?t=1340887)

---

### Post by Jellow on 2012-03-05
Just found this out: when I try to log in via terminal (Ctrl+Alt+F1, because F7 doesn't work anymore), it says '-bash: /etc/profile: access denied'. Then the new line says: 
I have no name!@jelle-Aspire-5520:~$
Most options in the thread you gave me assume I can actually still access the account and change files and ownerships this way, but I can't, 'cause there is this bash.

I was trying to edit the document rc.local to add some line to activate s/pdif in my soundcard when this went wrong. Should I aim to get that document fixed? Or the ownership of it?

---

### Post by Jellow on 2012-03-07
Weirdest thing ever: I managed to change the ownership of /etc somewhere during editing rc.local.

Fixed the ownership and I was able to login again!

SOLVED :)

---

### Post by Jellow on 2012-03-07
Weirdest thing ever: I managed to change the ownership of /etc somewhere during editing rc.local.

Fixed the ownership and I was able to login again!

SOLVED :)

---

