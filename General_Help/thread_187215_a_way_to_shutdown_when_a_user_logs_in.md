---
title: "a way to shutdown when a user logs in"
date: 2006-06-02
forum: General Help
---

### Post by nbx909 on 2006-06-02
I run a server that sits at home all day and all night, sometimes my family needs to shut it down when i am not around and i don't want to explain to them how to log in, sudo then do the shutdown command (let alone give them the password). So is there a way to create a user that when ever it logs in they computer will shutdown?

---

### Post by schilcha on 2006-06-02
method 1 (don't know if that really works): set the user's shell to "/sbin/poweroff". You can do this somewhere in the advanced properties of the user-and-groups-configuration.

method 2 (this should work): add the shutdown-command to the ~/.bashrc file. It'll be executed as soon as the user logs in.

In both cases you might have to allow the user to shutdown without pwd. You can configure sudo to allow that. Try something like:
```

username  hostname = NOPASSWD: /sbin/poweroff

```
Make sure to use "visudo" to edit the sudo-settings. Substitute "username" and "hostname" with what you need.

Good Luck!

---

### Post by seth0x2b on 2006-06-02
Isn't ~/.bashrc being executed only on textmode login?! I'm asking, not being sarcastic in any way...
If you want to execute a command on Gnome login, go to 
System > Preferences > Sessions > Startup Programs, and add there "sudo /sbin/poweroff".
Do this after you follow schilcha's indications on setting sudo privileges (edit "/etc/sudoers" and add the line he gave you, with proper replacement of user/hostname)
I don't use Kde so anyone else point to a KDE login method.

Cheers

---

### Post by nbx909 on 2006-06-02
there is no x on my server so it should work

---

### Post by seth0x2b on 2006-06-02
You can use ~/.bashrc as schilcha instructed then.

Cheers and good luck

---

### Post by professor_chaos on 2006-06-02
On my box, pressing the power button starts the shutdown procedure. Only pressing once does this, holding it in, causes an instant poweroff. :(

---

