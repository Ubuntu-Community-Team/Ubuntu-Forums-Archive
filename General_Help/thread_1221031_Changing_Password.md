---
title: "Changing Password"
date: 2009-07-23
forum: General Help
---

### Post by Psycho.mario on 2009-07-23
By setting up an 'expect' script, would i be able to change my password every boot?
For example:
```
password230709
```
That is, the word password with the date tagged on the end. So could i have my system set up so that when i log on, my password is unique to the date, with, like, a salt on the front? So my question is, is it possible to change my password during boot?

Thanks

---

### Post by michy99 on 2009-07-23
I don't know, but I am beginning to believe your nickname.

---

### Post by Psycho.mario on 2009-07-23
What do you mean?

---

### Post by lykwydchykyn on 2009-07-23
I don't see why not.  Give it a shot.

Worst case scenario, you have boot to recovery mode, drop to a root shell, fix your password and remove the script.

---

### Post by c0mput3r_n3rD on 2009-07-23
No you cannot change your password during startup.  The only way to change the password on your computer is after you have logged in, and then with the passwd command:
```

passwd

```

You could I suppose make a script to do that, how ever you still have to put in your original password, and enter your new password twice.

Basically, you will have change the password every day manually... Linux is to secure for that.

---

### Post by Psycho.mario on 2009-07-23
Heres the script i have wrote. (You will need a user called 'test' and 'expect' to be installed)
```
#!/usr/bin/expect -f
set user test
set pass password
set date [exec date +%d%m%y]
spawn passwd $user
expect "Enter new UNIX password:"
send "$pass$date\r"
expect "Retype new UNIX password:"
send "$pass$date\r"
expect eof
```

Would this work if run from /etc/rc.local?

Thanks

---

### Post by c0mput3r_n3rD on 2009-07-23
Try it.
I really don't think it's possible though.

---

### Post by Psycho.mario on 2009-07-23
Ran some tests, And it worked!! :D
c0mput3r_n3rd, it seems linux isn't *that* secure

---

### Post by c0mput3r_n3rD on 2009-07-23
Hey good for you! I'm surprised it worked.  Did you try changing the date and rebooting and seeing what happens?

---

### Post by Psycho.mario on 2009-07-23
Yep, Still works. Now, how do i mark this thread as solved?

---

### Post by lykwydchykyn on 2009-07-23
Never say "can't be done" on Linux.  If you're willing to dig deep enough, it usually can.

---

