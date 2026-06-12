---
title: "xubuntu splash screen"
date: 2010-02-22
forum: General Help
---

### Post by thraxsa on 2010-02-22
I just installed xubuntu-desktop on my Ubuntu 9.10 desktop, just to have the option of using xfce ( I did the same with Kubuntu - kde).

I have noticed that the Xubuntu splash screen now comes up rather the the Ubuntu default splash screen.

I tried to use Start-Up Manager to changed back to Ubuntu but Xubuntu xsplash screen ( one with the fire flies ) still comes up.

Is their any way to change this back to the Ubuntu Splash Screen without the Xubuntu screne coming up at all ??

Thanks : )

---

### Post by NCLI on 2010-02-22
[Here you go.]("http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/") Outdated, but it should still work.

---

### Post by thraxsa on 2010-02-22
> **NCLI said:**
> [Here you go.]("http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/") Outdated, but it should still work.

gave it a shot ... no different, still using Xubuntu as the splash screen.  It's no real problem, but just prefer the original Ubuntu screen I had prior to insalling xfce-desktop.

Any other suggestions ?

---

### Post by thraxsa on 2010-02-22
I actually found out how to do this, but I thought I would pass this on to anyone else who was experiencing the same issue.  You just need to re-install the ubuntu xsplash theme as per below :
    udo apt-get install --reinstall ubuntu-xsplash-artwork

To show the X-splash arrguments:

    sudo -u gdm xsplash --help


Then go into startup manager and select ubuntu as the default theme.

Hope this is useful ...

---

