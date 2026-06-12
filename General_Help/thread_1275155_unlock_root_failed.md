---
title: "unlock root failed"
date: 2009-09-25
forum: General Help
---

### Post by morio.kalani on 2009-09-25
hi,

This is the first time that I encountered this problem.
When I installed ubuntu or eeebuntu on my pc's and laptop I always have one user (myself) and root... Where I always used the same password for both of them.

Now I installed Ubuntu Jaunty on a friends pc and gave him a password and wanted to unlock the root and give it another password.

So he wouldn't mess up his system and had to ask me before he had to install something.
But when I went to System>Administration>users and groups ... and i wanted to unlock root. it was very weird but it always locked again without a password.
So everytime he simple got to give his password to do administrative tasks.
Not very safe, cause he doesn't know linux and isn't gonna learn... he just want to be the end-user.

So THE QUESTION!!!!

How do I unlock root????
Does it always have the same password of the first user????

thanks....

---

### Post by Liolikas on 2009-09-25
Just manually add password encrypted hash into shadow file then.

Read article for details:
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

I hope you will manage to crypt password manually yourself with some kind of toolz.

---

### Post by AeroCross on 2009-09-25
If I understood correctly, you want to enable root privileges at ANY time to the user who created an account?

If that's the case, you might also want to try editing the Sudoers File
[http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

It manages the permissions for the users and aplications.

Very VERY careful with this tho. You might lock yourself out of your own system if you "do it wrong".

If it's not the case... well... I might have to read again.

---

### Post by morio.kalani on 2009-09-25
> **AeroCross said:**
> If I understood correctly, you want to enable root privileges at ANY time to the user who created an account?

If it's not the case... well... I might have to read again.

No i'm sorry, but you misunderstood...

I installed a fresh ubuntu... with my friend as only user.
I want to be the root... but I can only unlock root through his account.
when i try to unlock it doesn't seem to work...
every time i give root a different password, it keeps on erasing the password and locking root.

I've never noticed on my computers cause I always used the same password as my account.
But even on my ubuntu and eeebuntu it keeps locking root, and erasing the password.

I'm gonna try the command line to change the password... It can't be true that root has to have the same password as the first user.

---

### Post by cgroza on 2009-09-25
Dont unlock root he will mess everything in 2 days...

---

### Post by morio.kalani on 2009-09-25
somehow it is solved...

first I SSH onto his pc with his name and wanted to SU with his password... surprisingly it didn't work, so i tried the password I wanted to give root.
And BINGO!!! I don't know how or why but it seemed that root changed the password where he didn't want to change it last time.
Even when I SSH with root it took the new password.

thanks for the replies anyway...

---

