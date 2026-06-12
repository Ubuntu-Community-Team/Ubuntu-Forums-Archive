---
title: "Cannot change user password"
date: 2010-01-05
forum: General Help
---

### Post by fantastic on 2010-01-05
I've tried both the GUI and the terminal to change my user's password and both are failing. I'm running 9.10 with current updates.

In the GUI, I type in the current password and it recognises it. I then type in the new password twice. Upon clicking change password it hangs.

In the terminal I use "passwd". I type in current password. I then type in the new password twice, but an error of:
```

Bad: new password must be different than the old one
Enter new UNIX password:
```

The new password is different than the old one. And I have even "su [user]" then entered the password changing me to that user and then used "passwd", but still fails.

I've even changed the new password to another something different (with NO special characters), and it still fails. 

Are there certain characters I should NOT have in a password, such as /#/ or /;/?

Any tips on resolving this?

---

### Post by nothingspecial on 2010-01-05
You certainly can`t use # or @.

You are advised to use ony letters numbers and punctuation marks.

---

### Post by drs305 on 2010-01-05
> **fantastic said:**
> 
I've even changed the new password to another something different (with NO special characters), and it still fails. 

Are there certain characters I should NOT have in a password, such as /#/ or /;/?

Any tips on resolving this?

From the *passwd* man page:
> 
Then, the password is tested for complexity. As a general guideline, passwords should consist of 6 to 8 characters including one or more characters from each of the following sets:
       ·   lower case alphabetics
       ·   digits 0 thru 9
       ·   punctuation marks

Care must be taken not to include the system default erase or kill
characters.  passwd will reject any password which is not suitably
complex.


When you first set up your password, if you use one that Ubuntu doesn't like it will complain but continue if you insist. I just tried changing my password in System, Preferences, About Me and it refused to allow me to use a password that was too simple - no override ability. This might be what is happening to you.

---

### Post by fantastic on 2010-01-05
Ah, thanks guys. I tried an alternate method pulling in a bit from what you each posted.

I needed to have a password that contains special characters- and I think that is where the problem WAS- the special characters in comparing the old with the new password.

Current password was (and I do mean was because it was resolved) 13 characters long containing upper, lower, number and special characters /./, /=/ and /$/.

What I did:
[LIST=1]
Change the password to something simple- e.g. /YEAR2010/.
[/LIST]
[LIST=2]
Change the password to the required password criteria, *which was the password I was originally trying to change it to*
[/LIST]

Now the current password contains the required upper, lower, number and special character. And it DID work using a /#/ in the password now.

All is working well now.

Thanks mates!

---

### Post by nothingspecial on 2010-01-05
> Avoid password characters which have special meaning to the tty driver, such as # (erase) and @ (kill)

It doesn`t say you can`t use them, it says you should avoid them, or who knows what dire consequences could ensue.

Of course, this is linux..... do as you will.

---

### Post by fantastic on 2010-01-05
> **nothingspecial said:**
> It doesn`t say you can`t use them, it says you should avoid them, or who knows what dire consequences could ensue.

Of course, this is linux..... do as you will.

Ahhh...

Noted and password changed already. Thanks

---

