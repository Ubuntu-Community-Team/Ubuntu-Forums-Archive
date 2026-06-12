---
title: "Deleted keyrings folder : ("
date: 2010-02-16
forum: General Help
---

### Post by unxposed on 2010-02-16
Okay so I'm completely new to Ubuntu and have just installed 9.10 which I'm really liking... until I messed things up a bit.

I was trying to get rid of the keyring password popping up on each restart, so I stupidly deleted the gnome2/keyrings folder (which I really regret)... the first problem this caused was tweetdeck stopped working. But other things like FTP are also not saving passwords... unsurprisingly.

I've tried uninstalling and reinstalling gnome-keyring through synaptic package manager a few times without any luck, and now nmapplet has disappeared also. The only file I have in gnome2/keyrings is login.keyring. I'd happily go back to entering if I can get back tweetdeck and FTP and other things that rely on this.

Any help would be amazing!

---

### Post by crlang13 on 2010-02-16
In the keyring app, have you simply tried making a new keyring folder, right clicking on it, and saying "make default"? 

If you want to avoid giving permission everytime, simply leave the kingring password blank.  Although this does leave you a little open... If there are some applications that you want instant access, make one keyring without a password, and then another kingring with a password for applications you're concerned about.

---

### Post by unxposed on 2010-02-16
Yeah I've done that and I get nothing!

nmapplet is back btw as it had become unchecked in synaptic package manager.

Thanks!

---

### Post by crlang13 on 2010-02-16
The only idea I would have would to re-install the programs that use the keyring.  However, I'm sure there is probably a better way the the delete and try again approach (unless you only have a couple applications that use the keyring).

Maybe try it with one application first and see if that works.

---

### Post by unxposed on 2010-02-17
Unfortunately I've also tried reinstalling tweetdeck numerous times without any luck.

What files should be in gnome2/keyrings folder?

Is this the only folder that's required for keyrings to be functioning properly?

Thanks

---

### Post by crlang13 on 2010-02-17
> **unxposed said:**
> Unfortunately I've also tried reinstalling tweetdeck numerous times without any luck.
Thanks

How did you go about uninstalling and re-installing the keyring and the other programs?

If you're removing programs through the synaptic package manager (system > administration > synaptic package manager) you have the option to "remove" or "completely remove" a program.  if you say remove, alot of the configuration files are kept on the computer just in case you want to re-install.  Completely remove removes every bit of the program.

You want complete remove because something has gone wrong with the configuration of the program.

---

### Post by unxposed on 2010-02-18
Originally I removed keyrings something like:

```
rm ~/.gnome2/keyrings/*
```

But have since tried all the options in synaptics package manager of re-installing, remove, completely remove etc.. Same with tweetdeck, I've tried completely removing that and re-installing too without any luck!

---

### Post by unxposed on 2010-02-19
Okay so who would be surprised to learn that there were some leftover adobe air and tweetdeck files in .appdata, I deleted them, reinstalled air and tweetdeck and all back to normal.

Keyring manager does now come up at startup since I installed gmail for docky to ask for authentication for docky, however nmapplet is not asking for it!?

The only problem to do with is I now appear to be left with is connecting to FTP. Places > Connect to server > FTP (with login) > Enter password (remember forever) - all correct, but on pressing 'connect' the Enter password box comes back up and entering password again keeps doing this.

Any ideas?

Thanks

---

### Post by crlang13 on 2010-02-19
Totally not sure...  I'm completely out of ideas.  It seems like you deleted everything and tried to re-install so I don't understand why it's still not working.

sorry buddy

---

### Post by hallu on 2010-02-25
maybe you have to name your keyring 'login' (that's the default name)

---

### Post by unxposed on 2010-02-26
I'm not sure, there is a login keyring there already as it's created automatically if it's deleted. It's not my default though, but it doesn't seem to make any difference if I do make it default.

My default I have called default and it has a dropdown next to it with 'docky/Password' - Key ID 1 and 'Adobe AIR ELS Key' Key ID 2 under, presumably the passwords it's storing. login keyring has nothing under.

Still haven't got the FTP remembering passwords, even temporarily.

Thanks

---

