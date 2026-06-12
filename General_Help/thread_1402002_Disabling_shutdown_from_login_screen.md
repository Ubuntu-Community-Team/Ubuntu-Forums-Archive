---
title: "Disabling shutdown from login screen"
date: 2010-02-08
forum: General Help
---

### Post by Oatworm on 2010-02-08
I have a computer running Xubuntu 9.10 and, on the login screen, there's a button in the lower right-hand corner that allows someone to shutdown or restart the machine.  I'd like that button to either disappear or, alternatively, require me to log in before using it, that way someone can't just walk up and shut the machine down without me knowing who did it.

Is there a way to turn it off?  I've tried turning the SystemMenu option in /etc/gdm/custom.conf to 0 (found that option [here]("http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/x135.html")) but that doesn't seem to do anything.

Thanks in advance!

---

### Post by Oatworm on 2010-02-08
UPDATE:  Turns out that documentation I was looking at was deprecated.  The documentation on valid custom.conf values I needed was [here]("http://library.gnome.org/admin/gdm/2.28/configuration.html.en#daemonconfig").  However, I'm still spinning my wheels a bit.  The following command should do the trick, but doesn't:

```
sudo -u gdm gconftool-2 -t bool -s /apps/gdm/simple-greeter/disable_restart_buttons true
```

The documentation states that, if the $HOME directory for the gdm user is writable, a *gdm-simple-greeter.schemas* file is created in there that stores the value.  Checking */etc/passwd*, I found that the home directory for the gdm user is */var/lib/gdm* - when I went in there, I found there were files owned by gdm in the directory, which would suggest that it's writable by the gdm user, but there was *gdm-simple-greeter.schemas* file.  However, curiously enough, asking for the value of that key using *gconftool-2* showed that the value had been changed for the gdm user, even after a reboot.  In other words, this happened:

```
# sudo -u gdm gconftool-2 -g /apps/gdm/simple-greeter/disable_restart_buttons
true
```

I then ran *gconftool-2* as root; it showed the original value of the key (false).  So, I tried changing it as root and restarting the gdm service, but that didn't change anything.  On a lark, I tried using *find / -name 'gdm-simple-greeter.schemas'* to find if one of those files was created anywhere - instead, I found the default one in */usr/share/gconf/schemas*.  I tried changing that - still nothing.  The restart/shutdown button is still there before I log in.

Anybody have any suggestions?

---

### Post by Oatworm on 2010-02-08
ANOTHER UPDATE:  No, this isn't a shameless attempt to bump the thread.  It is actually quite shameful.  ;)

Just for kicks, I broke down and installed gconf-editor and used the *export DISPLAY=:0.0* hack listed [here]("http://ubuntugenius.wordpress.com/2009/12/25/customise-the-gdmxsplash-login-screen-in-ubuntu-9-10/").  I set the "disable_user_list" value under the same simple-greeter section to "true" and confirmed that the "disable_restart_buttons" value is also "true".  After rebooting, I still had a restart button but no more user list.  This tells me that gconf-editor is editing the GDM configuration correctly; GDM just isn't recognizing it for whatever reason.

More Googling will now commence...

---

