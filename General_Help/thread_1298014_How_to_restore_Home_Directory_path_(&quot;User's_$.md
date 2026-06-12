---
title: "How to restore Home Directory path (&quot;User's $HOME/.dmrc file is being ignored)"
date: 2009-10-22
forum: General Help
---

### Post by AsgerJorn on 2009-10-22
Hello

I accidentally changed my Home Directory in (as far as I remember) system>controlpanel>users and groups>user. I changed it to /root
 were it before was /home.
When I try to log-in I get the error: "User's $HOME/.dmrc file is being ignored"
I have tried several options through root in recovery-mode.
I have also tried to log-in with the user 'root' but I don't know the password.

Is there a way I access these settings and undo what I have done?
Or perhaps create a new user that can access these settings?

I hope you have the information you need.
Thank you very much.

Aleksander

EDIT!: I forgot to mention that when I try to logon and press OK when the "User's $HOME/.dmrc file is being ignored"-window appears, the screen goes black and I have no other option than to force shutdown.

---

### Post by undecim on 2009-10-22
Get to a terminal by pressing Ctrl+Alt+F1

Then run this command:
```
sudo usermod -d /home/username username
```(replacing username with your username)

If you are using the beta, I believe virtual terminals are disabled, however, so you will need to run this in recovery mode; but be careful in recovery mode! (btw: In recovery mode you don't need the "sudo" part)

EDIT: BTW: root has no password -- It is disabled by default to keep people from breaking their systems (even experienced people can easily accidentally break their computers when logged in as root, which I why you should only log in as root as a last resort.)

---

### Post by philinux on 2009-10-22
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by AsgerJorn on 2009-10-22
usermod -d /home/username username
Wohoo! it worked!

Lovely.. :)

---

