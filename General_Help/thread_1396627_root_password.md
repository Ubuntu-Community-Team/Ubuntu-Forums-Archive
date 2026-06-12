---
title: "root password"
date: 2010-02-02
forum: General Help
---

### Post by cyrilfred on 2010-02-02
I need a root password to install a printer driver. I have just upgraded to Ubuntu 9.10 

have used the usual sudo command in the terminal window BUT when I try to type in a new root password the text entry is locked , so can't type anything.

What now???

---

### Post by nothingspecial on 2010-02-02
You don`t need a root password to install a printer just use sudo.

Are you following any instructions, if so what are they.

---

### Post by lindsay7 on 2010-02-02
When you type a command that starts with"sudo", you will be asked for a password.  When you type that in the terminal, you will not see anything, that is the way it works,  just type in your password and hit enter.  You should see something happen for there even if the command line just comes back. It there is something wrong you will get an error message.

---

### Post by cyrilfred on 2010-02-02
Thanks, but attempting to install printer driver through self exec download. Root password needed for that.

Attempted typing in new password in terminal window by get error message 'sorry, try again'

---

### Post by undecim on 2010-02-02
What printer are you installing? the drivers may exist in the repositories.

If you need to run an executable file to install it though, you should be able to use your own password. Open a terminal, and type this:
```
sudo /path/to/executable/file
```where /path/to/executable/file is the full pathname of the file. If the file is in your home directory, you can just use```
sudo ~/file
```where file is the filename of the executable. If it's in your downloads directory, use ```
sudo ~/Downloads/file
```again, where file is the filename of the executable.

Any of these commands will ask for your password. Type it in (the password is completely invisible as you type it)

---

### Post by cdenley on 2010-02-02
There is no root password by default. It is strongly suggested you don't set a root password. It is also strongly suggested you don't execute anything you downloaded from a website.

If there is no driver for your printer available out-of-the-box (what printer?), and you insist on executing some binary as root which is supposed to install a print driver:
```

sudo /path/to/binary

```

No root password needed. Just enter your own password.

---

### Post by Silvertones on 2010-02-02
Why not just go to:
sys/admin/print

---

### Post by Iowan on 2010-02-02
> **cyrilfred said:**
> ... BUT when I try to type in a [COLOR="Red"]new[/COLOR] root password... After sudo <commandname> the requested password is your user password. Perhaps [this]("https://help.ubuntu.com/community/RootSudo") page will help.

---

