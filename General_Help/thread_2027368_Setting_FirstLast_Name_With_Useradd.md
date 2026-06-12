---
title: "Setting First\Last Name With Useradd"
date: 2012-07-16
forum: General Help
---

### Post by Kirk Schnable on 2012-07-16
I am currently managing a deployment where computers are imaged via CloneZilla, and a script which is planted to run at first-boot adds a specified username with a specified password to the netbook.

I am currently adding the users via a script with a command like this:

```
/usr/sbin/useradd --shell /bin/bash --home /home/$username --skel /etc/skel --create-home --password `/usr/bin/openssl passwd -1 $password` $username
```

In the tutorials I'm handing out to my users, I walk them through the GUI method of changing their password.

However, I have not found a way with useradd to set their First or Last name.  Thus in the "change password" area it shows up as "(null)" being their user's full name.

Anyone have any ideas as far as how I can script the name change?

Thanks,
Kirk

---

### Post by Vaphell on 2012-07-16
[http://manpages.ubuntu.com/manpages/intrepid/man1/chfn.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/chfn.1.html)

---

### Post by Cheesemill on 2012-07-16
From 'man useradd', add the the following to your command:
```
--comment "Full Name"
```

---

### Post by Kirk Schnable on 2012-07-16
Oh, I saw comment, but I didn't read the description.  Didn't think it was what I was looking for, but you're correct.  Thanks.

Kirk

---

