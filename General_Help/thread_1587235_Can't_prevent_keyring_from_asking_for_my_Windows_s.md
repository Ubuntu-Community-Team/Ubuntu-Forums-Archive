---
title: "Can't prevent keyring from asking for my Windows share password when accessing"
date: 2010-10-03
forum: General Help
---

### Post by calande on 2010-10-03
Hello,

I have a Windows share on my network and I protected it with a password. I access it with my Ubuntu desktop, and I saved my password the first time I accessed it. The password is saved in Seahorse (the keyring), but each time I try to access my Windows share, I have to type in my keyring password :(
Despite [trying]("http://ubuntuforums.org/showthread.php?t=187874") [several]("http://ubuntuforums.org/showthread.php?t=192281") [tutos]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/"), I haven't been able to prevent keyring from asking for my keyring password. Could you help me please?
Thanks,

---

### Post by searchfgold6789 on 2010-10-03
I thought this was kinda the point of a keyring in the first place...

---

### Post by calande on 2010-10-03
I just want to get rid of this annoyance, with Ubuntu still remembering my password.

---

### Post by calande on 2010-10-05
Any idea? Thanks....

---

### Post by calande on 2010-10-09
I just want to save my password once for all, like in Windows 7...

---

### Post by sendblink23 on 2010-10-09
well at all honesty... since you have already even tested removing the password on keyring *seeing the links you posted that you have tried... and its not working for you

I would suggest... well remove the password on the *Windows access thing... unless you are scared of someone to access it :P

---

### Post by calande on 2010-10-09
> unless you are scared of someone to access it
That's the problem! :)

---

### Post by sendblink23 on 2010-10-09
> **calande said:**
> That's the problem! :)

hehehe :lolflag:

well lets hope some keyring guru appears today or tomorrow to help you out

---

### Post by luvshines on 2010-10-09
See if this helps:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=remove+keyring+password](http://ubuntuforums.org/showthread.php?t=192281&highlight=remove+keyring+password)

Comment #8 says it worked for samba share :D

If you don't want to run into troubles, better wait for the Gurus to comment :lolflag:

---

### Post by sendblink23 on 2010-10-09
> **luvshines said:**
> See if this helps:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=remove+keyring+password](http://ubuntuforums.org/showthread.php?t=192281&highlight=remove+keyring+password)

Comment #8 says it worked for samba share :D

If you don't want to run into troubles, better wait for the Gurus to comment :lolflag:

hahaha  dude, did you check the LAST PAGE?
He already tried it out.. the OP is the last comment on that thread 5 days ago :P

---

### Post by luvshines on 2010-10-09
:lolflag: He did ??

By the power vested in me by somebody(can't remember who), I hearby declare that I am JackA** :P

Plz wait for Keyring Gurus to comment

---

### Post by calande on 2010-11-27
It seems that it's impossible to have autologin enabled and not having to enter the keyring password at the same time. You have to enter a password either to log in or to open a samba share. Can you confirm?

---

