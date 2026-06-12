---
title: "Can't login - can't get past name selection"
date: 2011-06-06
forum: General Help
---

### Post by njparton on 2011-06-06
I can't seem to login into ubuntu this morning.  I'm using 11.04 64 bit.

It's been working fine for a few weeks, but this morning I select my name with the mouse and it just returns to the same initial screen after a millisecond.  The password box does not come up.

The last thing I did yesterday was add another user - would that have caused any issues (or a red herring)?

I went to a terminal and deleted that user (sudo userdel -r <username>) but that hasn't helped.

Any ideas please???

---

### Post by tech-hero on 2011-06-06
have you tried loging in not using the GUI using the safe mode? I wanna know if this is a GUI problem or not.

---

### Post by njparton on 2011-06-06
> **tech-hero said:**
> have you tried loging in not using the GUI using the safe mode? I wanna know if this is a GUI problem or not.

How do I choose safe mode during boot? I can't remember the key to press, thanks

---

### Post by njparton on 2011-06-06
> **tech-hero said:**
> have you tried loging in not using the GUI using the safe mode? I wanna know if this is a GUI problem or not.

PS I can do CTRL+ALT+F1 to get a terminal up and login that way so I think it is a GUI problem.

---

### Post by sanderd17 on 2011-06-06
Maybe you could install kdm or ldm? 

just go into the tty and do a 

```
sudo apt-get install kdm
```

---

### Post by Bucky Ball on 2011-06-06
> **sanderd17 said:**
> Maybe you could install kdm or ldm? 



Why?

Did you do any other updates before you shutdown the computer? Seems likely it has something to do with that or the new user ...

---

### Post by njparton on 2011-06-06
My wireless connection isn't live until I get into gnome so I don't have a network connection.

I've removed the new user and their home directory.

I've also changed my password in a tty console no problem.  Still can't login.

I hope I don't have to do a re-install :-(

---

### Post by njparton on 2011-06-06
Can anyone help?  I'm about 2 hours away from a complete re-install :-(

---

### Post by lifestreammm on 2011-06-06
Does it give this message?:

Install problem!
The configuration defaults for GNOME Power 
Manager have not been installed correctly
Please contact your administrator.

That's the problem I had, couldn't log on either
Maybe your problem is the same or different...
[http://ubuntuforums.org/showthread.php?p=10908419#post10908419](http://ubuntuforums.org/showthread.php?p=10908419#post10908419)

Life

---

### Post by njparton on 2011-06-06
No. It's not an install problem I've had it up and running for 2 weeks.

When I click my username on the login screen I get nothing.  It tries to do something but I don't even get a password box.

I can go to a tty terminal and login, this must be a problem with gdm, gnome etc...

---

### Post by SteveLee on 2011-07-31
Bump

Did you resolve this? I've just got exactly the same problem after adding a user and turning off auto login in. I have a clean Natty install and applied all updates.

I did turn assistive tech on but turned it off again.

---

### Post by SteveLee on 2011-08-01
the gdm logs indicated something wrong with pam keyring. A upgrade from natty to natty using the liveCD did the trick and kept my docs + packages too - makes a neat repair facility.

---

### Post by njparton on 2011-08-01
No, I had to resort to a re-install :(

---

