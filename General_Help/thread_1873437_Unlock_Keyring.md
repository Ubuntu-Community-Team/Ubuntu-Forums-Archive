---
title: "Unlock Keyring"
date: 2011-11-01
forum: General Help
---

### Post by xubuhemmo on 2011-11-01
I'm running on xubuntu 11.10. This applet appears when I open internet page as mail.com. I'd like to get rid of it. I've used two days in internet to search right solution. Can somebody help me?

[http://ubuntuforums.org/attachment.php?attachmentid=206059&stc=1&d=1320160990](http://ubuntuforums.org/attachment.php?attachmentid=206059&stc=1&d=1320160990)

---

### Post by Gatemaze on 2011-11-01
Yes this rings a bell... Your login password should be the same as the unlock keyring. There is also somewhere a file you can delete to reset the keyring unlock. I can't remember from the top of my head but there is definitely plenty of information if you search for this.

---

### Post by Jose Catre-Vandis on 2011-11-01
Something like this:

[http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/](http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/)

I had to fix this problem and seem to remember I just deleted default.keyring. Just try renaming it to something else, logout and login.

---

### Post by xubuhemmo on 2011-11-02
Didn't work in xubuntu 11.10. There is no such file:

sudo gedit /etc/pam.d/_**gdm**_

If I make it I think it not help.

---

### Post by Jose Catre-Vandis on 2011-11-03
> **xubuhemmo said:**
> Didn't work in xubuntu 11.10. There is no such file:

sudo gedit /etc/pam.d/_**gdm**_

If I make it I think it not help.

No gedit in xubuntu, and no gdm in 11.10 either, its lightdm now, so:

```
sudo leafpad /etc/pam.d/lightdm
```

or in terminal

```
sudo nano /etc/pam.d/lightdm
```

---

### Post by xubuhemmo on 2011-11-04
I used leafpad.

But there is **_not_** /etc/pam.d/lightdm file in my xubuntu.

I'm running  on xubuntu 11.10.

---

### Post by Jose Catre-Vandis on 2011-11-04
Try (in terminal)
```
ls /etc/pam.d | grep dm
```

and report output

---

### Post by xubuhemmo on 2011-11-04
hara@Fuji:~$ ls /etc/pam.d | grep dm
lightdm
lightdm-autologin
hara@Fuji:~$

---

### Post by Jose Catre-Vandis on 2011-11-04
So you do have a /etc/pam.d/lightdm file on your system :)

Open it up with sudo and you can edit the line related to the keyring accordingly

```
sudo leafpad /etc/pam.d/lightdm
```

---

### Post by xubuhemmo on 2011-11-05
Sorry I didn't read carefully. So I add the line in the end of lightdm file but it did'n help.

[http://ubuntuforums.org/attachment.php?attachmentid=206395&stc=1&d=1320480972](http://ubuntuforums.org/attachment.php?attachmentid=206395&stc=1&d=1320480972)


I rebooted also but no help.


Edit. Added lightdm.png

---

### Post by Jose Catre-Vandis on 2011-11-05
Just re-read that post I pointed to (and the comments!) Doing Step 2 doesn't appear to be a good idea, so undo the changes you made to /etc/pam.d/lightdm and just makes sure that default.keyring is deleted/renamed in ~/.gnome2/keyrings/. That should be enough to sort your problem.

---

### Post by xubuhemmo on 2011-11-07
I installed xubuntu again. When open internet browser first time applet came: Choose password for new keyring
     
 [I]An application wants to create new keyring called "Default". Choose 
      the password you want to use for it.[/I]

I gave my root password. Now everythings working.

I'll be back with next problem. 

Thanx.

---

### Post by tulipán on 2011-11-09
> **Jose Catre-Vandis said:**
> Something like this:

[http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/](http://www.noob2geek.com/how-to/how-to-disable-gnome-keyring-in-ubuntu-10-04/)

I had to fix this problem and seem to remember I just deleted default.keyring. Just try renaming it to something else, logout and login.

it worked like a charm for me, huge huge thanks!

---

