---
title: "How to deal with &quot;vwv101@ubuntu:~$_&quot;"
date: 2010-04-02
forum: General Help
---

### Post by Sdream on 2010-04-02
Installing Ubuntu 9.04 on Virtualbox

Host  : XP Pro. sp2
Guest: Try to install Ubuntu 9.04 by a live CD

At the end of installation, 
appears black screen with white words,
at the end of the words there are:
Ubuntu 9.04 ubuntu tty1
Ubuntu login: vwv101
Password: v331024v

Does not login but more words and at the end appears:

vwv101@ubuntu:~$_

Help Please

I am stuck here
What must I do to login?

Thanks

---

### Post by Dayofswords on 2010-04-02
first..edit out your pass from your post

restart it by ```
sudo shutdown -r now
```

should load normally after that

---

### Post by Sdream on 2010-04-02
> **Dayofswords said:**
> first..edit out your pass from your post

restart it by ```
sudo shutdown -r now
```should load normally after that
Thank you, Dayofswords!
Have just tried and the following is what comes out after pressing the Enter key:
Shutdown: illegal time value
Try `shutdown --help' for more information.

---

### Post by lisati on 2010-04-02
> **Dayofswords said:**
> first..edit out your pass from your post


+1. Not a good idea to include your password in public forums, it could help allow unscrupulous readers access to your system without your permission.

---

### Post by Sdream on 2010-04-02
> **lisati said:**
> +1. Not a good idea to include your password in public forums, it could help allow unscrupulous readers access to your system without your permission.
Thank you for the advice.

---

### Post by srs5694 on 2010-04-02
> **Sdream said:**
> Thank you, Dayofswords!
Have just tried and the following is what comes out after pressing the Enter key:
Shutdown: illegal time value
Try `shutdown --help' for more information.

Are you sure you included the "now" part? Please try again and be sure you type that. If that still doesn't work, try pressing Ctrl+Alt+Del (press all three keys simultaneously).

More fundamentally....

> At the end of installation, 
appears black screen with white words,
at the end of the words there are:
Ubuntu 9.04 ubuntu tty1
Ubuntu login: vwv101
Password: v331024v

Does not login but more words and at the end appears:

vwv101@ubuntu:~$_


Actually, you *did* log in successfully; it's just a text-mode login rather than a GUI login. It's possible that you accidentally switched to a text-mode login screen by pressing Ctrl+Alt+F1 or some similar sequence. If so, you should be able to get back to the GUI login screen by pressing Ctrl+Alt+F7. If that doesn't work, though, there's a good chance that rebooting (via the shutdown command) won't work; it could be that there's something wrong with your X configuration. (X, or the X Window System to give it its full name, is Linux's GUI environment.) Unfortunately, such problems can be difficult to diagnose via forums, so let's hope it's not that....

Oh, and change your password. You can do this from the text-mode login by typing "passwd" (note the unusual spelling).

---

