---
title: "Forgotten Password (?) Can sign in!"
date: 2012-05-09
forum: General Help
---

### Post by tito-dutta on 2012-05-09
It seems I have forgotten password of Ubuntu 11.10 computer*
I can sign in automatically. I selected "disable sign in using password" 
But, I'll need the password when I'll upgrade to 1.04
So, I need to change password before I upgrade!

How can I reset password?


*Not very sure if I have forgotten password, since I have tried the two common passwords I use everywhere!

---

### Post by wojox on 2012-05-09
This works here [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by tito-dutta on 2012-05-10
See the screenshot. I have "no password" now, so, I can go to the option- "Change password" but, the "Change" password button is disabled, since the current password is not working(?)

---

### Post by Peter09 on 2012-05-10
Keep the shift key held down while you are booting, once you get to the grub menu select the recovery mode option. When the system boots to a menu select the root terminal option.
 
in there do
 
```
passwd <username>
```
 
it will then ask for a new password, enter it and then reboot.

---

### Post by silbar on 2012-09-14
Unfortunately, when I do all that, I get this response:

"authentication token manipulation error"

Now what does that mean and how can I get past it?

Rico Silbar

---

### Post by silbar on 2012-09-14
I found the way somewhere on this forum by searching on "authentication...error".
Basically, one has to make / read-write to be able to write to /etc.  What worked for me was (at a root prompt in recovery mode)

   [INDENT]mount -o remount,rw /[/INDENT]

before the

   [INDENT]passwd USERNAME[/INDENT]

command.

   Rico Silbar

---

### Post by newb85 on 2012-09-14
> **silbar said:**
> I found the way somewhere on this forum by searching on "authentication...error".
Basically, one has to make / read-write to be able to write to /etc.  What worked for me was (at a root prompt in recovery mode)

   [INDENT]mount -o remount,rw /[/INDENT]

before the

   [INDENT]passwd USERNAME[/INDENT]

command.

   Rico Silbar

If you had paid attention to the link in Post #2, you wouldn't have had to search for that info.  It's in psychocat's howto.

---

### Post by critin on 2012-09-15
> **tito-dutta said:**
> It seems I have forgotten password of Ubuntu 11.10 computer*
I can sign in automatically. I selected "disable sign in using password" 
But, I'll need the password when I'll upgrade to 1.04
So, I need to change password before I upgrade!

How can I reset password?


*Not very sure if I have forgotten password, since I have tried the two common passwords I use everywhere!

You have to enter the password whenever you update and install something.  Didn't you ever update?  You should.  I suggest you login with a password,  for one thing,  it gives you the options if you ever want to use a different desktop environment sometime.

---

