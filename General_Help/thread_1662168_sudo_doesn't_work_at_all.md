---
title: "sudo doesn't work at all"
date: 2011-01-07
forum: General Help
---

### Post by ZebaSz on 2011-01-07
Ok, I'm honestly baffled by this. I don't know what I might have touched, added or removed, but it broke sudo.
Literally, sudo doesn't do anything at all. Nor does gksu. After being requested my password, the command exists and returns a prompt. I can't install or configure practically anything within my session. I can go to recovery mode and log in as root, though. Any ideas?

---

### Post by TeoBigusGeekus on 2011-01-07
Log in as root and type in terminal
```
EDITOR=nano visudo
```
to edit your sudoers file.
Look if there is a line there that reads
```
yourusername ALL=(ALL) ALL
```
If not, add it and save (ctrl+x).
Reboot and post us what happened.

---

### Post by sisco311 on 2011-01-07
> **ZebaSz said:**
> Ok, I'm honestly baffled by this. I don't know what I might have touched, added or removed, but it broke sudo.
Literally, sudo doesn't do anything at all. Nor does gksu. After being requested my password, the command exists and returns a prompt. I can't install or configure practically anything within my session. I can go to recovery mode and log in as root, though. Any ideas?

Do you get any error messages? Is your user in the admin group? Did you edit the sudoers file?

Check out: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by ZebaSz on 2011-01-07
No error, it just exits.
visudo doesn't fix it

---

### Post by ZebaSz on 2011-01-07
Bump
Nothing works so far. Again, there's no error message, simply nothing. And when the Software Center asks for my pasword, gksu hangs there. The password box disappears, but the dialog remains open.

---

### Post by hawkmage on 2011-01-07
What do you get is you run the command:
```
which sudo
```

Also try:
```
ls -l `which sudo`
```

And what about:
```
sudo -l
```

---

### Post by NoBugs! on 2011-01-07
Recovery Mode may help, it should give you root console...
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html)

---

### Post by ZebaSz on 2011-01-08
```
$ which sudo
/usr/bin/sudo
$ ls -l `which sudo`
-rwsr-xr-x 2 root root 127560 2010-08-31 17:38 /usr/bin/sudo
$ sudo -l
[sudo] password for seba: 
$ (just a prompt, returns nothing)
```

---

### Post by Sirius B on 2011-01-08
i had problems, but sorted it this way

boot pc up into recovery mode. then select "drop to root shell promt" then type in adduser *your name* admin then restart pc into normal and check terminal sudo command

---

### Post by Sirius B on 2011-01-08
However if that didn't work this webpag e[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo) has some usefull help

---

### Post by ZebaSz on 2011-01-08
Thanks, but please read before posting. All of that has already been tried, and hasn't worked.

---

### Post by Sirius B on 2011-01-08
> **ZebaSz said:**
> Thanks, but please read before posting. All of that has already been tried, and hasn't worked.
i had read before posting, i cant see anyone else sugesting the ```
adduser *your name* admin
```

---

### Post by ZebaSz on 2011-01-08
> **Sirius B said:**
> i had read before posting, i cant see anyone else sugesting the ```
adduser *your name* admin
```
With all due respect:
1) that is in the psychocats link I had already been provided
2) I added my user directly into /etc/sudoers
3) the issue is not related to user priviliges (apparently, since there is no related error message)
All this info is in the thread. I don't mean to be rude, but do pay a little more attention.

---

### Post by Krytarik on 2011-01-08
If all that didn't help, you might try to re-configure
```
mv /etc/sudoers /etc/sudoers.backup-09.01.2011
dpkg --configure sudo
```or re-install the package "sudo".
```
apt-get purge sudo
apt-get install sudo
```EDIT: from the "root shell prompt" of course, assumed that.

---

### Post by ZebaSz on 2011-01-08
dpkg --configure says the package is already configured. I looked at the man page, and tried with dpkg-reconfigure. Nothing.
I don't know if I should purge sudo. apt-get says many other packages would also be removed: gksu, update-notifier, gdebi, and ubuntu-minimal, among others. Should I just go ahead and do it (and reinstall everything afterwards) or is there another preferable approach?

---

### Post by Krytarik on 2011-01-08
"dpkg-reconfigure", right, I couldn't remember that, judging from the man of dpkg I thought it would do it too. Sorry, should have googled it before.

Then just try to
```
apt-get install --reinstall sudo
```

---

### Post by ZebaSz on 2011-01-08
Nope, nothing. However, I bring some exciting news:
I have my session set so it auto-logins. Now, just for the sake of argumment, I decided to logout and re-login, but GDM hangs immediately after I enter my password. Now THAT'S weird. There must be something wrong when it comes to checking whether the passwords match. I tried to change my password ("passwd username"), but it didn't work. Any ideas about this?
EDIT: tty also shows some funny behaviour. It completely ignores my login info and asks for a username and password again.
Locking the screen, though, doesn't seem to have that problem (prompts for password and unlocks without problems)

---

### Post by Krytarik on 2011-01-08
That narrows down the issue to GDM, apparently.

Did you change your password recently?

After a short web search, I found this bug report:
[https://bugzilla.redhat.com/show_bug.cgi?id=495924](https://bugzilla.redhat.com/show_bug.cgi?id=495924)

Just try this, from root shell prompt:
```
authconfig --updateall
```

---

### Post by Krytarik on 2011-01-09
After searching a bit further in that matter, I've got another idea, if the previous one doesn't work:

Boot to the "root shell prompt" and change the password of your user from there, this should work, and it would update the file "/etc/shadow", where the passwords are stored, maybe it's damaged.

Good luck!

---

### Post by ZebaSz on 2011-01-09
No luck so far. I already tried changing my password, that didn't work. And now I'm getting "authconfig: command not found". Maybe this is good news, cause we're narrowing it down, but I don't know what to do now.

---

### Post by ZebaSz on 2011-01-09
B u m p

---

### Post by Krytarik on 2011-01-09
> **ZebaSz said:**
> I already tried changing my password, that didn't work.You did that from the "root shell prompt", right?!
> **ZebaSz said:**
> And now I'm getting "authconfig: command not found".
I've checked this at my machine now, it isn't installed there either.

Did you already try to create a new user and login with those?:
```
useradd NEW_USER
passwd NEW_USER
```

---

### Post by ZebaSz on 2011-01-09
I created a new user, added it to admin, and it works just great. My guess is I deleted some important config file or something in my own session. I'll move all my stuff to my new user, seems more practical. Thanks!

---

### Post by Krytarik on 2011-01-09
> **ZebaSz said:**
> I created a new user, added it to admin, and it works just great. My guess is I deleted some important config file or something in my own session. I'll move all my stuff to my new user, seems more practical. Thanks!
Great! I forgot about the admin thing, sorry.

---

### Post by Sirius B on 2011-01-09
> **ZebaSz said:**
> I created a new user, added it to admin, and it works just great. My guess is I deleted some important config file or something in my own session. I'll move all my stuff to my new user, seems more practical. Thanks!
great

im happy you have it sorted out

---

