---
title: "Remote Desktop help"
date: 2009-08-02
forum: General Help
---

### Post by t4ggs on 2009-08-02
its a stupid question but, Im using the "terminal server client" to control remotely a computer, but i also want to copy files from the remote computer to my computer, how do i do that?? hehe thanks

---

### Post by Meson on 2009-08-02
Check out filesystem forwarding in the 'Local Resources' tab. When set up, your local filesystem will appear on the Windows computer you've connected to.

---

### Post by t4ggs on 2009-08-03
i did and it appear, but when trying to copy or paste something, it wont let me, the drive disconnects himself, is that normal??

---

### Post by Meson on 2009-08-03
Where are you trying to paste to? You should only be able to write to your home directory.

---

### Post by t4ggs on 2009-08-03
to the home directory, but im not able to do so, or to copy from home to the windows pc

---

### Post by Meson on 2009-08-03
To be honest, I really don't like tsclient. It's just a wrapper for the **rdesktop** command. You might be more sucessful if you check out the manpage for rdesktop and build the command yourself.

Here is an example of the command I use. The manpage warns about using the -p/password option from the command line because it will show up in ps, however I've noticed that in my distribution the command is sanitized and my password is replaced with 'xxxxxxx' in ps.

```
rdesktop -u matt -p XXXXX -g 90% -x lan -P -r disk:linux=/home/matt -r sound:off -r clipboard:CLIPBOARD -5 myloc.homelinux.net:33089
```

---

### Post by andw on 2009-10-14
> **Meson said:**
> To be honest, I really don't like tsclient. It's just a wrapper for the **rdesktop** command. You might be more sucessful if you check out the manpage for rdesktop and build the command yourself.

Here is an example of the command I use. The manpage warns about using the -p/password option from the command line because it will show up in ps, however I've noticed that in my distribution the command is sanitized and my password is replaced with 'xxxxxxx' in ps.

```
rdesktop -u matt -p XXXXX -g 90% -x lan -P -r disk:linux=/home/matt -r sound:off -r clipboard:CLIPBOARD -5 myloc.homelinux.net:33089
```

I am running the 9.10 beta, and have found that if you don't include
  -r clipboard:CLIPBOARD
The local machine just about dies when you use the clipboard on the remote machine.
(top shows Nautilus going up to 80+% and the local machine is very painful to use)
So... thanks for that command line.

---

### Post by stinger30au on 2009-10-14
freeNX might do the trick

[http://freenx.berlios.de/](http://freenx.berlios.de/)

---

