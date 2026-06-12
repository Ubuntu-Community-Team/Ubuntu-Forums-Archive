---
title: "Creating new account via terminal."
date: 2012-01-25
forum: General Help
---

### Post by MarkoHF on 2012-01-25
So basically my school has Edubuntu 7.04 and with the help of my live cd i was able to use terminal as root. Since for some unknown reasons I can not enter users-admin. All i can do is change password to current users but I need my own user with admin privileges.
So how do I add a new user with admin privileges from root@edubuntu:
I am new so I am a noob with linux.

---

### Post by gsgleason on 2012-01-25
You can create a new user with 'useradd'

Specify an additional group that allows sudo to do everything.

---

### Post by sanderd17 on 2012-01-25
does this help?

[https://wiki.archlinux.org/index.php/Users_and_Groups#User_management](https://wiki.archlinux.org/index.php/Users_and_Groups#User_management)

---

### Post by Lars Noodén on 2012-01-25
```

sudo adduser *foo*
sudo gpasswd --add *foo* sudo

```

---

### Post by MarkoHF on 2012-01-25
> **gsgleason said:**
> You can create a new user with 'useradd'

Specify an additional group that allows sudo to do everything.

Can you write me the full code that I need to enter at terminal to have a new account with admin privileges.
As I said before I am very new with ubuntu.
EDIT: Wow fast replays. I'll check them out.

---

### Post by MarkoHF on 2012-01-25
So I read the article and all I need to type in terminal is
# useradd -m -g users -G root -s /bin/bash haier2
The group is root and my username is haier2.
Then I should write passwd haier2
to setup my password.
Right ?

---

### Post by Lars Noodén on 2012-01-25
[gpasswd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gpasswd.1.html) is an easier way to manage group membership.  See post #4 above.

---

### Post by MarkoHF on 2012-01-25
> **Lars Noodén said:**
> [gpasswd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gpasswd.1.html) is an easier way to manage group membership.  See post #4 above.

Ok so by the look of your post
I assume I am suppost to write this
sudo adduser haier2
sudo gpasswd --add haier2 sudo
And then write passwd haier2
Right or am I wrong ?

---

### Post by Lars Noodén on 2012-01-25
That's correct.

---

### Post by gordintoronto on 2012-01-25
If you booted from a LiveCD and added a user, as soon as you shut down, that user will disappear.

---

### Post by MarkoHF on 2012-01-25
> **gordintoronto said:**
> If you booted from a LiveCD and added a user, as soon as you shut down, that user will disappear.

Then you have any ideas on how do I create my own user without Live CD. Terminal is blocked.

---

### Post by gordintoronto on 2012-01-25
Yes, talk to the sysadmin and ask for an account.

---

### Post by CharlesA on 2012-01-26
> **gordintoronto said:**
> Yes, talk to the sysadmin and ask for an account.
+1.

This thread is also closed.

@OP: If you continue to ask about getting unauthorized access, you may be put on moderation. Ask your sysadmin to allow you access if you need it.

---

