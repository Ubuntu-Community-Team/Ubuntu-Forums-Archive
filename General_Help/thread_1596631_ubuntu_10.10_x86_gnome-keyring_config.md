---
title: "ubuntu 10.10 x86 gnome-keyring config"
date: 2010-10-14
forum: General Help
---

### Post by ac14112 on 2010-10-14
just installed Ubuntu 10.10 x86 Desktop and I'm having issues finding the configuration for gnome-keyring. Basically, I don't want the keyring to remember my ssh key passphrase.

In 10.04, I ran the gconf-editor tool as root (sudo), and under apps>gnome-keyring>daemon-components, I unchecked the ssh option. This stopped the keyring from asking for the passphrase and instead I was asked each time in the terminal. 

In 10.10, for some reason, there is no longer a gnome-keyring option anywhere in gconf-editor, nor an ssh option relating to the keyring. If anyone knows where the configuration for gnome-keyring has moved or any other way of disabling the keyring from remembering my ssh key passphrase, please let me know.

I appreciate the help.

---

### Post by ac14112 on 2010-10-15
Can anyone help? Or know a better forum where I could ask this question?

---

### Post by thomasboleyn on 2010-10-15
I'm waiting for a response too buddy, though in my case it is for the gmail docky notifier :confused:

---

### Post by ac14112 on 2010-10-15
Well, I guess I answered my own question.

Go to System > Preferences > Startup Applications and uncheck "SSH Key Agent"

Found here: [http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

thomasboleyn - You can check out more about Gnome Keyring here:
[http://live.gnome.org/GnomeKeyring](http://live.gnome.org/GnomeKeyring)

Also, when looking through the startup apps in the list, there was something about migrating settings from gconf to dconf.

Apparently, there is some other gnome config tool called dconf. I had to install a package called dconf-tools to get the command dconf-editor, but there was still no configuration for gnome-keyring that I could see. 

Good luck in your search.

---

### Post by thomasboleyn on 2010-10-16
Thanks for updating me. I had a look at that link but couldn't really understand any of it, I tend to need Dummies illustrated guides to these things on linux.

---

