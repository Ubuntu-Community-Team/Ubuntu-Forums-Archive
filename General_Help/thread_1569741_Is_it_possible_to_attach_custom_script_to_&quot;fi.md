---
title: "Is it possible to attach custom script to &quot;first time log in&quot; event"
date: 2010-09-07
forum: General Help
---

### Post by alikthename on 2010-09-07
When there is no user home directory and user logs in it's created using /etc/skell as a template.

Is it possible to attach custom script to that "first time log in" event?

Thanks in advance.

---

### Post by blueridgedog on 2010-09-07
Just a thought...you could put a .bashrc file in /etc/skel that performed the script action you wanted, then copied another file to be the users' default bashrc so that it only ran the one time.

---

### Post by alikthename on 2010-09-08
> **blueridgedog said:**
> Just a thought...you could put a .bashrc file in /etc/skel that performed the script action you wanted, then copied another file to be the users' default bashrc so that it only ran the one time.

Thanks a lot for your help.

Well I added following line at the end of /etc/skell/.bashrc:
FLDR=$(zenity --entry --text "Folder name" --entry-text "folder"); mkdir ~/${FLDR}
 But it does not seemto work when logging in via GDM. hense it attempts to do something when logging in via bash session.
What I want to get is the ablilty to create thunderbird profile when user first time logs into the system. User would have to provide his name and surname using graphical interface.

---

### Post by hakermania on 2010-09-08
If you create the .gnomerc file into the /etc/skell and type there what you want? (Dont forget the & at the end. otherwise your system will stack after giving your passwd)

---

### Post by alikthename on 2010-09-08
> **hakermania said:**
> If you create the .gnomerc file into the /etc/skell and type there what you want? (Dont forget the & at the end. otherwise your system will stack after giving your passwd)

Yeah it works and actually does what I need, but there are 2 nuances. It does not have window borders and looks a bit ugly. I guess it would look better if it started after window manager and gnome-settings-daemon.

---

### Post by blueridgedog on 2010-09-08
A script called "Default" can be placed in /etc/gdm/PostLogin.  You would have to put logic in the script that determined if it needed to run, but it is an option.

---

### Post by tgalati4 on 2010-09-08
You could create a desktop launcher that runs the initialization script.  Choose a big/gaudy icon that says "Click me if you want mail".  It would be placed on the new user's desktop directory so it shows up on the desktop.  Once the user works their way around the desktop, they will eventually click the icon.

---

