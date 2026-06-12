---
title: "Unable to login with LXDE desktop"
date: 2012-08-14
forum: General Help
---

### Post by chrissound on 2012-08-14
Hello everyone.

I'm running ubuntu 11.04 and I installed the LXDE desktop environment. Today strangely I'm unable to boot into the LXDE DE, it seems to 'freeze' for a second and then take me back to the login screen. Gnome however works.

What can I do to fix this? 

Much appreciated.

---

### Post by 2F4U on 2012-08-14
Start by looking into .xsession-errors. I am assuming that the desktop crashes due to some reason and this file might tell you why.

---

### Post by chrissound on 2012-08-20
Thank you for your input.

Here is the contents of .xsession-errors, I did login with openbox session once I was unable to login with LXDE.
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_ZA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"

```

contents of .xsession-errors.old
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_ZA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (gnome-session:2029): WARNING **: Unknown option --default-session-key

```

---

### Post by jvilla93 on 2013-03-11
I am having the same log in problem, but I am not allowed to log in to my username at all, in any of the desktop environments. I am only able to log in as a guest.

Furthermore, neither "su" nor "sudo" will work. For su, I get the error "su: Authentication Failure", and for sudo, I get the error "sudo: unable to change to sudoers gid: Operation not permitted". How exactly did you fix this?

---

