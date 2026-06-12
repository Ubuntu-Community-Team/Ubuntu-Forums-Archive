---
title: "ubuntu auto boot"
date: 2010-08-06
forum: General Help
---

### Post by jfr34k on 2010-08-06
Greetings, I installed Ubuntu 10.04 desktop and want to know if it is at all possible to let ubuntu start up with a username and password... but do not ask for the username and password at startup...also start the remote desktop application at the same time

Thx

---

### Post by sikander3786 on 2010-08-06
Hi.

You can set up ubuntu to auto login without the user name and password. But for remote management you need to at least login once using your user name and password and then you will be able to login remotely.

I have a thought. I haven't tried it but it might be possible. Configure ubuntu for auto-login and set the screen saver + screen lock for the minimum possible time, for instance 1 min and then try remote login. Does that work?

Regards.

---

### Post by jfr34k on 2010-08-06
sorry for the supid question but how do you setup auto login without username and password?

---

### Post by sikander3786 on 2010-08-06
Go to System >>> Administration >>> Login Screen and select Log in as XXXXX automatically.

---

### Post by jfr34k on 2010-08-06
thx, thats what i was looking for, now the next question is: how to let me log in using remote desktop connection over lan without typing password to unlock your login keyring?

---

### Post by sikander3786 on 2010-08-06
> **jfr34k said:**
> thx, thats what i was looking for, now the next question is: how to let me log in using remote desktop connection over lan without typing password to unlock your login keyring?

That is not possible I think. You need to unlock the keyring on the server to use it remotely. I gave you a hint in my first post above. Did you try it?

---

### Post by jfr34k on 2010-08-06
yes i did, screensaver activates, when i want to login remotely i still have to put password for screen saver and password to unlock keyring... funny thing though, i do not need to put in a password, just hit escape and i can log in remotely

---

### Post by jfr34k on 2010-08-06
found a solution... hopefully not a permenant one for security reasons.... if you remove password from "remote desktop" it does not ask you for keyring password. Luckily where this pc going, the people think that linux is some exotic food...:-k
thx for all the help

---

### Post by jfr34k on 2010-08-06
WAIT WAIT !!!! Found a different solution, [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)
and it works with password in remote desktop.... Hoera!!!

---

### Post by sikander3786 on 2010-08-07
> **jfr34k said:**
> WAIT WAIT !!!! Found a different solution, [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)
and it works with password in remote desktop.... Hoera!!!

Nice to hear but this is also mentioned on the link.

> 
WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.


"Proceed with caution." Thats what I have to say to you.

Regards.

---

### Post by jfr34k on 2010-08-07
thx i saw that, but this pc will not have a monitor, keyb or mouse connected just for remote purposes wich has a password... thx for sending me in the right direction....

---

