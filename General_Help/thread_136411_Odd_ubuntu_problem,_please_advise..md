---
title: "Odd ubuntu problem, please advise."
date: 2006-02-25
forum: General Help
---

### Post by jreed on 2006-02-25
I have an odd symptom in a newly installed ubuntu 5.10 system.  Gnome gui apps which required su authentication would not launch with there gnome icon.  Launching the following apps in a shell resulted in the listed errors.

synaptic:
               (synaptic:12656): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:12656): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
root@amd64:/home/zebra#

This is with su privileges, and synaptic will lauch using this method, but always with these errors.

users-admin:
                     (users-admin:12673): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Again users-admin will launch this way, but with these errors.

disks-admin:
                     (disks-admin:12857): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I appears an authentication service for either gnome or pam has not started??
opinions please.

---

### Post by dcstar on 2006-02-25
[QUOTE=jreed]I have an odd symptom in a newly installed ubuntu 5.10 system.  Gnome gui apps which required su authentication would not launch with there gnome icon.  Launching the following apps in a shell resulted in the listed errors.
......
I appears an authentication service for either gnome or pam has not started??
opinions please.[/QUOTE]
No, these are not supposed to be launched from a terminal using "su".

Try launcing them with "gksudo" and then see if there are any errors.

---

### Post by jreed on 2006-02-25
[QUOTE=dcstar]No, these are not supposed to be launched from a terminal using "su".

Try launcing them with "gksudo" and then see if there are any errors.[/QUOTE]


I am not using su to launch them, I am first logging in as root using su then launching the application.   Using gksudo however produces the exact same errors.  It doesnt appear to be my method, but rather some missing authentication mechanism.

---

### Post by taurus on 2006-02-25
Let me see if I get this right.  You first log in as a regular user and then "su" to root!!!

---

### Post by jreed on 2006-02-25
[QUOTE=taurus]Let me see if I get this right.  You first log in as a regular user and then "su" to root!!![/QUOTE]

Yes, you have it right.

---

### Post by taurus on 2006-02-25
Then you cannot display window on the desktop since X doesn't allow you too...  Therefore, whatever you need to run by root, please use sudo from a regular account,

```

sudo synaptic

```

---

### Post by jreed on 2006-02-25
[QUOTE=taurus]Then you cannot display window on the desktop since X doesn't allow you too...  Therefore, whatever you need to run by root, please use sudo from a regular account,

```

sudo synaptic

```[/QUOTE]

You are wrong, synaptic or any other X gui displays just fine when run by root.  sudo synaptic or any other package I have listed still return the exact same error as running the app as root.  To clarify the event, the application does execute correctly from the command line, but with the listed errors.

---

### Post by taurus on 2006-02-25
Okay, I am wrong and you are right then...  

Try this.  Log in as a regular user.  Then at the prompt, su to root with "su -" and once you log in as root, type xterm at the prompt and see what you get!!!  :rolleyes:

---

### Post by jreed on 2006-02-25
[QUOTE=taurus]Okay, I am wrong and you are right then...  

Try this.  Log in as a regular user.  Then at the prompt, su to root with "su -" and once you log in as root, type xterm at the prompt and see what you get!!!  :rolleyes:[/QUOTE]

Well since you seem fit to not address my original question, we can certainly discuss yours.  "su -" does nothing more than log you in as root using a login shell environment, xterm detects this and fails to start up.  This is xterm choosing not run in the root environment.  Try su without "-"(login shell) and xterm will execute just fine.

---

### Post by Siriushoward on 2006-02-26
Can you please make sure your thread title actually describes your problem.  Its very innoying to see 100+ threads all named "please help with my problem!"

---

### Post by jreed on 2006-02-26
[QUOTE=Siriushoward]Can you please make sure your thread title actually describes your problem.  Its very innoying to see 100+ threads all named "please help with my problem!"[/QUOTE]

Can you not post in my thread unless your actually going to try to help.

---

### Post by Ramses de Norre on 2006-02-26
Let's keep it friendly, will we.
We're all here to help and learn..
I'm getting exactely the same error messages when I try to run an app while being logged in as root. ```
ramses@icarus:~$ sudo su
Password:
root@icarus:/home/ramses# nautilus

(nautilus:17017): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing nautilus-open-terminal extension

```
Maybe it just have to do with X not preferring to open apps as root.
But the apps work afterall so..

---

