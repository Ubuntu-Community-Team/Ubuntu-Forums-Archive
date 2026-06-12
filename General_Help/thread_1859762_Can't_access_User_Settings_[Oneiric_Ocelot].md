---
title: "Can't access User Settings [Oneiric Ocelot]"
date: 2011-10-14
forum: General Help
---

### Post by Angus77 on 2011-10-14
I've just installed 11.10 (I've been a user since 7.04, but haven't upgraded since 10.04).

Everything was going fine until I added my wife as a second user.  After rebooting, I wanted to edit her User Settings (from my account), but when I click on System Settings->User Accounts, the System Settings window simply closes.

I installed gnome-system-tools and tried to edit the user settings using users-admin.  A window opens up, but it's all greyed out, and the mouse cursor stays in wait mode, and I'm never able to access it.  The terminal doesn't give any helpful information (just "(users-admin:2595): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",").  I can't close it without doing ctrl-c.

I tried removing my wife's account from /etc/passwd to see if that would help, but it didn't.  I was still successfully able to add accounts for my children user useradd.

Can anyone help?  I'd really rather not reinstall, especially if I'm not sure if this will happen again!

---

### Post by 23dornot23d on 2011-10-14
Check this thread out .... it may hold the solution for the pixbuf ......

[http://ubuntuforums.org/showthread.php?t=1859213](http://ubuntuforums.org/showthread.php?t=1859213)

There also seems to be a Xauthourity problem being raised as people are upgrading
Lightdm refuses to accept passwords ......

see my links below for some of the problems being encounterd .....

---

### Post by Angus77 on 2011-10-14
I installed gtk2-engines-pixbuf as suggested in the thread you linked to.

Now the Gtk-WARNINGs have disappeared, but I still can't open System Settings->User Accounts, and users-admin still acts the same as before (perpetually starting up and has to be killed with ctrl-c).

My wife is Japanese, and I want to set her locale to Japanese.  In Ubuntu before, you would just choose your locale from the login screen, but that's not given as an option any more---it's in System Settings->User Accounts.  This is really frustrating!

---

### Post by vbulash on 2011-10-14
The same for me!
```
gnome-control-center users-account
```
(equivalent of System Settings -> User Accounts) reports "Segmentation fault" and nothing else. pixbuf already present in system.

---

### Post by mc4man on 2011-10-14
> **Angus77 said:**
> I installed gtk2-engines-pixbuf as suggested in the thread you linked to.

Now the Gtk-WARNINGs have disappeared, but I still can't open System Settings->User Accounts, and users-admin still acts the same as before (perpetually starting up and has to be killed with ctrl-c).

My wife is Japanese, and I want to set her locale to Japanese.  In Ubuntu before, you would just choose your locale from the login screen, but that's not given as an option any more---it's in System Settings->User Accounts.  This is really frustrating!

What session are you using?, sounds from some of what you've mentioned the gnome-session-fallback

Can you open it directly from /user/share/applications or from the command
gnome-control-center user-accounts

---

### Post by vbulash on 2011-10-14
> **mc4man said:**
> What session are you using?, sounds from some of what you've mentioned the gnome-session-fallback

Can you open it directly from /user/share/applications or from the command
gnome-control-center user-accounts

I'm using unity session, no fallback.
"gnome-control-center user-accounts" produces segmentation fault - I wrote previous message by hands, so command line was the same you propose

---

### Post by vbulash on 2011-10-14
Is it possible to get some debug information?
"Segmentation fault" is about nothing...

---

### Post by mc4man on 2011-10-14
> **vbulash said:**
> Is it possible to get some debug information?
"Segmentation fault" is about nothing...

You can look in /var/crash & see if a .crash is there for this.
Also take a look in ~/.xsession.errors right after the crash.

Is there anything else you can't do that you should be able to & is this an upgrade from 11.04?

---

### Post by vbulash on 2011-10-14
> **mc4man said:**
> You can look in /var/crash & see if a .crash is there for this.
Also take a look in ~/.xsession.errors right after the crash.

Is there anything else you can't do that you should be able to & is this an upgrade from 11.04?

/var/crash - empty
~/.xsession.errors doesn't contain entries referring to user accounts crash.
Ubuntu 11.10 installed on clean machine.

---

### Post by Angus77 on 2011-10-14
For me, /var/crash is empty, but after clicking System Settings -> User Accounts, in ~/.xsession-errors I get

```
WARN  2011-10-15 07:31:59 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-10-15 07:31:59 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
```

I've managed to do what I wanted with my system without System Settings -> User Accounts now (my wife's account is in Japanese now, and I've got my children's accounts set up), so it's not a big deal now, but it's frustrating.

I really dislike the fact that Ubuntu's taken away functionality that I'd grown to depend on, though (easy language switching at the login screen).

---

### Post by Redwol on 2011-10-14
Well I seem to have the exact same problem. I really need this fixed ASAP, I made this thread: [http://ubuntuforums.org/showthread.php?t=1860431](http://ubuntuforums.org/showthread.php?t=1860431)

I guess mods can delete it now

edit:
this is what i get:
```

redwol@redwol:~$ gnome-control-center users-account

** (gnome-control-center:3015): WARNING **: Could not find settings panel "users-account"

** (gnome-control-center:3015): WARNING **: Could not load setting panel "users-account": Unknown error

(gnome-control-center:3015): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3015): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed



```

edit2:
if seems that the user settings loads fine on guest account, but crashes after I enter my password to unlock it or click anywhere on the dialog.

---

### Post by rlmcclain on 2011-10-17
Experiencing the same issue on a brand new 11.10 Edubuntu installation using the default Unity login. gnome-control-center does a segmentation fault whenever I click on the user accounts option. .xsession-errors shows this:
```
WARN  2011-10-17 18:55:12 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

```

---

### Post by jcoles on 2011-11-04
I can get into User Accounts and unlock the dialog. But only the most basic settings are available: Account Type, Language, etc. Where is the rest of it? (user privileges, groups, etc.)

---

### Post by cairtaker on 2011-12-30
I'm having same problem, how did you manage to setup your user accounts without  without System Settings -> User Accounts?  Your help is appreciated as I cannot create user accounts right now.
Thank you!

---

### Post by cairtaker on 2011-12-31
Ahhh silly me, broke the first rule of newly loaded operating systems.  Installed all available updates and then the user settings worked fine...:lolflag:

---

