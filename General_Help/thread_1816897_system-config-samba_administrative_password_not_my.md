---
title: "system-config-samba administrative password?? not my login password?"
date: 2011-08-02
forum: General Help
---

### Post by xekon on 2011-08-02
I have installed samba and system-config-samba

When I try to launch system-config-samba it asks for an administrative password?? I try the password that I use to login and run sudo commands or the synaptic package manager. It is not that password. When I use that password it waits a couple secconds and then just asks for the password again.

"incorrect password... try again"

What could I possibly be doing wrong, any help is GREATLY APPRECIATED.

EDIT: Ive tried it over and over, tried after a reboot, tried after an uninstall and reinstall through the synaptic package manager, then a reboot as well. It just wont accept my password.

---

### Post by skinnyquiver on 2011-08-02
> **xekon said:**
> I have installed samba and system-config-samba

When I try to launch system-config-samba it asks for an administrative password?? I try the password that I use to login and run sudo commands or the synaptic package manager. It is not that password. When I use that password it waits a couple secconds and then just asks for the password again.

"incorrect password... try again"

What could I possibly be doing wrong, any help is GREATLY APPRECIATED.

EDIT: Ive tried it over and over, tried after a reboot, tried after an uninstall and reinstall through the synaptic package manager, then a reboot as well. It just wont accept my password.

it may be looking for the policykit users password. is your user a member of the admin group? you can find this out by running
sudo grep ^admin:.*youruesername /etc/group
this replace the yourusername with the user you are using.

A workaround for this problem would be to lauch it as root using something like gksudo try running
gksudo system-config-samba

---

### Post by xekon on 2011-08-02
I am actually launching "system-config-samba" from the KDE Applications>settings menu system.

when I launch it on the application window list on my panel, it shows "gksu" at the popup that asks for my password.

here is what it shows:
```
xekon@xekon-desktop:~$ sudo grep ^admin:.*xekon /etc/group
[sudo] password for xekon: 
admin:x:109:xekon
xekon@xekon-desktop:~$ 
```


running this from the terminal: gksudo system-config-samba
it shows the bouncing samba config icon next to my cursor (kde behavior for launching an app) and it shows "gksudo" application appear on my panel in the window list, but no window or application ever opens, it acts like its going to for 4 seconds or so and then closes from the panel/window list and drops me back to prompt in terminal.

---

### Post by Morbius1 on 2011-08-03
And what happens when you run it with the KDE equivalent of gksu ( if I remember correctly - it's been a while ) :
```
kdesu system-config-samba
```

---

### Post by xekon on 2011-08-03
```
xekon@xekon-desktop:~$ kdesu system-config-samba
kdesu: command not found
xekon@xekon-desktop:~$ 
```

---

### Post by skinnyquiver on 2011-08-03
since you are in kde try
alt+f2
in the popup box that appears type
kdesudo system-config-samba

---

### Post by xekon on 2011-08-03
```
xekon@xekon-desktop:~$ kdesudo system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade
xekon@xekon-desktop:~$
```


EDIT: Installing glade from package manager now.

EDIT: now running "kdesudo system-config-samba" works like a charm.

but if I run it from the menu it still dont accept the password. I'm happy its working now though.

Thanks guys.

---

### Post by skinnyquiver on 2011-08-03
try installing glade and libglade2-0
sudo apt-get install glade libglade2-0

---

### Post by xekon on 2011-08-03
> **skinnyquiver said:**
> try installing glade and libglade2-0
sudo apt-get install glade libglade2-0

both are installed now.


As I added a share in the gui... this error showed up in the konsole/terminal:

```
invoke-rc.d: unknown initscript, /etc/init.d/samba not found.
```

when I change allow access to: everyone/specific users, it shows the same error. Also trying to access the share from my windows pc, it sees the share but cannot access it, the user name/password fails.

It seems like I need this initscript that I am missing.

EDIT: even with that error it is working, I just had to adjust the permissions on the parent folder and the folder that I am trying to share for group xekon and group sambashare.

---

### Post by xekon on 2011-08-03
Everything seems to be working now regardless of that error.

THANK YOU SO MUCH!

---

### Post by skinnyquiver on 2011-08-03
> **xekon said:**
> Everything seems to be working now regardless of that error.

THANK YOU SO MUCH!

you could link your /etc/init.d/smbd to /etc/init.d/samba that should fix the error

---

### Post by xekon on 2011-08-03
oh really? i've never linked something before. what commands would I run to do that?

---

### Post by skinnyquiver on 2011-08-03
sudo ln /etc/init.d/smbd /etc/init.d/samba -s

---

