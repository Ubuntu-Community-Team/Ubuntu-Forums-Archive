---
title: "clearing nautilus/connect to server password"
date: 2010-01-21
forum: General Help
---

### Post by jmexia on 2010-01-21
Hi,

I recently changed my password for our school's network drive.  I have been using secure WebDav to access my files on the server via Nautilus (Connect to Server).  My problem is that I must have clicked to "always remember password" when I first setup the WebDav.  Now, I cannot log into the server because it is remembering the old password.  How do you clear the old password from the cache?

Thanks,
Jeff

---

### Post by jamesisin on 2010-01-21
Doesn't it return a password prompt to you when it fails?  You ought to be able to change your password using that prompt, no?

---

### Post by jmexia on 2010-01-21
It prompts for a password, however, the new password fails.  I suspect it's Nautilus (or the method in which the password is cached) because I did not use the "remember password forever" (or whatever it says) on another box, and it connects fine using the new password.

Thanks for the reply.
Jeff

---

### Post by jamesisin on 2010-01-21
Try using a definitely wrong password to see if that helps reset the cache.

---

### Post by jmexia on 2010-01-21
Thanks again...however, no luck.  Apparently, Nautilus must be saving the password in a config file or profile somewhere.  The option says "Remember forever," and I guess they really mean it.  All kidding aside, there must be a *simple* way of removing or changing it.

Jeff

---

### Post by jamesisin on 2010-01-21
Sure, we just need to sort out where N stores that password and delete the file or remove the hash or whatever is appropriate.  What kind of share?  Samba?

---

### Post by jmexia on 2010-01-21
You know?  I'm not sure.  Does Samba handle WebDav?  Sorry, still a NOOB.

Jeff

---

### Post by jamesisin on 2010-01-21
Nope.  That's HTTP.  Sorry I overlooked that you said WebDav above.

Have a look in:

Applications --> Accessories --> Passwords and Encryption Keys

---

### Post by jmexia on 2010-01-21
You're the man.  That did the trick.  I was being lame...I kept looking in System > Preference > Encryption and Keyrings, and couldn't figure out where the passwords were saved.

Now, how do I officially thank you on the message board?

Jeff

---

### Post by jamesisin on 2010-01-21
You already have.

(Mark your thread as SOLVED in Thread Tools above.)

---

