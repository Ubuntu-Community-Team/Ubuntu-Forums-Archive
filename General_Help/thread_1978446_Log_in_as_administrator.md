---
title: "Log in as administrator"
date: 2012-05-11
forum: General Help
---

### Post by Noah Diaz on 2012-05-11
I installed Ubuntu 12.04 along with Windows X P and I cannot log in as an administrator in Ubuntu.System is asking for password.I cannot find what the password is. I can log in as a guest. As a guest I cannot get connected to internet. Please help me.Thanks in advance.

---

### Post by CharlesA on 2012-05-11
It is the password you chose when you installed.

---

### Post by Miykel on 2012-05-11
G'Day; When you installed you would have been asked for  "Your name", Computer Name" and "User Name", at the same time you would have been asked for a pass word and then confirm password, whatever you entered as you password you enter in at the logon screen and hit enter.
 Regards Miykel

---

### Post by Noah Diaz on 2012-05-11
Thanks for the reply.I entered the same password .but that didn't work.

---

### Post by Monotoko on 2012-05-11
This is going to a recovery job then, when you boot up and see the grub menu (keep hitting esc if you don't usually see the menu - and it should appear)

Choose the "Ubuntu With Linux {blah blah} (Recovery Mode)" option, it's the one below the usual. You will then get a menu, choose "root - Drop to root shell" then type "passwd username" (replacing username with your own, and removing the quotes) It should prompt you for a new password, enter a new one twice, reboot and go through it normally again, logging in with your new password :)

---

### Post by Noah Diaz on 2012-05-11
The same I typed on the welcome screen.Something has gone wrong...any chance of changing the password? Please...

---

### Post by Miykel on 2012-05-11
G'Day, Just a thought, did you make sure the caps lock is off, a simple thing but I have walked into that a few times  :lolflag:  
  The other question is did it ever work or is this a fresh install
Regards Miykel

---

### Post by Noah Diaz on 2012-05-11
Thanks so much to everybody.

---

### Post by Noah Diaz on 2012-05-11
@ Miykel, Thanks for reminding me of cap locks.I checked that. I think I have messed up with the password.

@ Monotoko, Thanks my friend, I typed "passwd username" and some options appeared and tell me please how to proceed from there?

---

### Post by Monotoko on 2012-05-11
not passwd username, you need the actual username... for example
passwd john
passwd dave
passwd noah

It should then allow you to reset it by asking you for the new password twice.

---

### Post by Noah Diaz on 2012-05-11
I did that correct. and then appeared some options like "changing password....." so on.There I can not understand what to do.

---

### Post by Monotoko on 2012-05-11
Hmm... can you get me a picture? On a camera or something?

---

### Post by Noah Diaz on 2012-05-11
It goes like this...

-a,  all  ..................                                             Report password status.....
-d,  delete ..................                                  Delete the password........

       ...that way 14 options.How to select that? Sorry that I have no way to attach a photo or something...

---

### Post by lisati on 2012-05-11
> **Noah Diaz said:**
> It goes like this...

-a,  all  ..................                                             Report password status.....
-d,  delete ..................                                  Delete the password........

       ...that way 14 options.How to select that? Sorry that I have no way to attach a photo or something...

That can sometimes happen if the passwd command isn't sure what to make of what you've typed on the command line.
The usual format is something like this, where you replace "USERNAME" with the username whose password you're trying to change:
```

passwd USERNAME

```
Does your username have spaces in it by any chance?

---

### Post by Monotoko on 2012-05-11
Hmmm, either you're typing the username in wrong, or haven't typed the command correctly. The user may not have added correctly, which might be why you can't login...

Either way, let's try another approach. We are going to add a new user which you should be able to login to upon reboot.

Run "adduser john" (replace john with whatever username you want) and it'll take you through adding a password and setting the account up.

The run "usermod -a -G sudo john" (again replace john with the username chosen earlier) - this will add the user to the sudo group so you can run your system.

Mono

---

### Post by Noah Diaz on 2012-05-11
Oh God yes ! I typed the user name with a space...Thanks so much.

---

### Post by Noah Diaz on 2012-05-12
Thanks you all great friends helped me.I got it done.Wonderful...Yes.Thanks SOOOOOOOOOOOOO MUCH Mono and all friends here.Thanks Ubuntu Forums too.I love Ubuntu and people who are with.Thanks again.

---

