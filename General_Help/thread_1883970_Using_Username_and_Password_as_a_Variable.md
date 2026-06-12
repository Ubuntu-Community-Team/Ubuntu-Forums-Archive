---
title: "Using Username and Password as a Variable"
date: 2011-11-20
forum: General Help
---

### Post by UnsolvedCypher on 2011-11-20
At our organization, we are planning to switch our computers to Ubuntu. To do this, we need everyone to have a desktop icon on their account with a link to their "K Drive", which is a place on the network \\SERVERNAMEHIDDENFORSECURITY\firstinitiallastname . We want to write a script so that we use the username of the account (firstinitiallastname) as a variable, so that there is a desktop shortcut to \\SERVERNAMEHIDDENFORSECURITY\[the username] . It would also be nice if there was a way to use the password as a variable, but if there is no way to do this, that's fine.
  Thanks so much, ~UnsolvedCypher

---

### Post by CharlesA on 2011-11-20
You could have a prompt to enter their password, but other then that, I don't know of any way to get their password without them typing it.

---

### Post by UnsolvedCypher on 2011-11-20
What about the username? I'll prompt for the password, but prompting for the username would just be inconvenient. But thanks for the input!

---

### Post by CharlesA on 2011-11-20
You can get the username by running "id" or by just using $USER

The only problem I foresee is that it would be a good idea to mask the password, but without feedback to the screen, I'm not sure how you would be able to handle it if they punched it in wrong.

---

### Post by UnsolvedCypher on 2011-11-20
So my script could look like
```
nautilus smb://SERVERNAMEHIDDENFORSECURITY/$USER
``` ?

---

### Post by CharlesA on 2011-11-20
That should prompt for the password, yeah.

echo it first and make sure that the username is filled out correctly. ;)

The username in the box should be prefilled.

---

### Post by UnsolvedCypher on 2011-11-20
I'm kind of new to Ubuntu. How would I go about "echo"ing this?
Thanks so much for the responses!

---

### Post by CharlesA on 2011-11-20
Like so:

```
echo "nautilus smb://SERVERNAMEHIDDENFORSECURITY/$USER"
```

You'd only need to use that for testing.

I just ran it on my box and it worked fine. :)

---

### Post by UnsolvedCypher on 2011-11-20
What do you mean for testing?

---

### Post by raja.genupula on 2011-11-20
I have some small idea . I am not working in a big organization like this , so may be my idea will be bad , so please dont mind.

What if we gave common serial number as a password , because already in administrator system we are going to have the system log and total organization will be under Eye's of CC camera's so may be no need to worry about security .
 and passwords like 

1 XXXXXX1 & XXXXXX2

or
username-001 , username-002 

so you can know them .

EDIT : now i got the post clearly .

---

### Post by CharlesA on 2011-11-20
For when you write up the script and making sure it works as intended. :)

It should be fine the way it is written, but better safe then sorry.

> **raja.genupula said:**
> I have some small idea . I am not working in a big organization like this , so may be my idea will be bad , so please dont mind.

What if we gave common serial number as a password , because already in administrator system we are going to have the system log and total organization will be under Eye's of CC camera's so may be no need to worry about security .
 and passwords like 

1 XXXXXX1 & XXXXXX2

or
username-001 , username-002 

so you can know them .

EDIT : now i got the post clearly .

That is not a good idea since the passwords would be known by anyone who has access to that serial number. That would be a security nightmare even with CCTV and logs, since you don't know who logged into what and if they were using their own credentials or another user's credentials.

In short, everyone should have their own unique password, since they can always be reset, if needed.

---

### Post by UnsolvedCypher on 2011-11-20
Thanks. So the real script would be ```
nautilus smb://SERVERNAMEHIDDENFORSECURITY/$USER
``` ?

---

### Post by UnsolvedCypher on 2011-11-20
This is a good idea, but we already have accounts and other computers with Windows and Mac set up this way. But thanks anyways!

(this is in response to raja.genupula)

---

### Post by CharlesA on 2011-11-20
> **UnsolvedCypher said:**
> Thanks. So the real script would be ```
nautilus smb://SERVERNAMEHIDDENFORSECURITY/$USER
``` ?

Yep.

---

### Post by UnsolvedCypher on 2011-11-20
Thanks so much! I'll mark the thread as solved.

---

### Post by CharlesA on 2011-11-20
> **UnsolvedCypher said:**
> Thanks so much! I'll mark the thread as solved.
No problem. :)

---

