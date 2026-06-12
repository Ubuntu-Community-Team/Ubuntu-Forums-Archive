---
title: "mounted but cant access"
date: 2010-02-05
forum: General Help
---

### Post by Cardale on 2010-02-05
I have mounted another computer of mine and I play on doing some automated transfers, but for some reason using the mount address I can't "mv" the files in the command line.

It is unix to xp.  

```
mv /var/www/scripts/*.c  smb://cio/scripts/
```Any ideas on a simple solution?

---

### Post by Cardale on 2010-02-05
:guitar:

---

### Post by Cardale on 2010-02-05
hey

---

### Post by Morbius1 on 2010-02-05
By mount, I assume you mean you mounted it through Nautilus?

If you did, then you can't reference smb:// in a move command. You have to reference the mount point. There is one but you may not be able to see it.

When you mount through Nautilus it creates a mount point at /home/username/.gvfs ( note the "." before gvfs - it's a hidden directory )

Your move command should look something like this:

mv /var/www/scripts/*.c  /home/username/.gvfs/"scripts on cio"

[COLOR=Blue]*EDIT: To view the hidden directory you need to enable it in Nautilus: Edit > Preferences > Views > Show hidden and backup files*[/COLOR]

---

### Post by Cardale on 2010-02-05
I am getting permission denied and sharing is turned on and I am using sudo.  Any suggestions?

---

### Post by Cardale on 2010-02-05
If I mount this drive as a user and then try and automate this process over the web will the www-data group be able to access a network if I mount it as user BOB

so far it seems no...or it is another problem

---

### Post by Cardale on 2010-02-05
How do I edit permissions when I mount windows computers through my network graphically or through terminal?

---

