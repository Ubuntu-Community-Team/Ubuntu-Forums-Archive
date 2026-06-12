---
title: "When is closed the gedit I got errors. Does someone know ?"
date: 2012-02-10
forum: General Help
---

### Post by CProgramming on 2012-02-10
Hello
I've try to fix the suspend problem and when is finished second step from [_this_]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") guide, I've got those errors:

------------------------------------

(gedit:5551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NH5G9V': No such file or directory

(gedit:5551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5551): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VMSE9V': No such file or directory

(gedit:5551): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

------------------------------------

I used as super user, of course.

Does someone know what is the problem and how can I fix it?

Thanks ;]

---

### Post by Thorsen V on 2012-02-10
recently-used.xbel is used to store a list of recent files for GTK apps to share.

So perhaps it doesn't matter?

(You would definitely need to be running sudo gedit to be able to write this file of course)

---

### Post by CProgramming on 2012-02-10
thank for the fast reply.
I see that file doesn't exist ..
why? should I create blank one?

---

### Post by Thorsen V on 2012-02-10
> **CProgramming said:**
> thank for the fast reply.
I see that file doesn't exist ..
why? should I create blank one?
If this had been successful I believe all it would amount to would be that subsequently running as root, if you were to use say  gedit again (or some other GTK app that supports the idea), then in the file dialogue you might see a list of files "recently opened" that included the file you were writing and that then could be opened with one click.

I can't explain why as root it failed to write this file, but I'm not sure, by itself this is anything to be too worried about.

AFTR, I've just tried editing a file with "sudo gedit" from a terminal, and while I don't see the messages you got, neither do I get the recently-used.xbel file created :)

---

### Post by Derek Karpinski on 2012-02-10
The problem is the directory does not exist, so gedit cannot make the file.

Here is the fix:
[http://ubuntuforums.org/showpost.php?p=11616152&postcount=13](http://ubuntuforums.org/showpost.php?p=11616152&postcount=13)

BTW, always use gksudo NOT sudo when using graphical programs (gedit, nautilus)

---

### Post by CProgramming on 2012-02-11
> **Derek Karpinski said:**
> The problem is the directory does not exist, so gedit cannot make the file.

Here is the fix:
[http://ubuntuforums.org/showpost.php?p=11616152&postcount=13](http://ubuntuforums.org/showpost.php?p=11616152&postcount=13)

BTW, always use gksudo NOT sudo when using graphical programs (gedit, nautilus)

Thank you friend .
I try latter (because I'm working right now about project at eclipse , and if the suspend fail I will have to force restart my computer).

P.S , what are the diffidents between sudo and gksudo?

---

### Post by mcduck on 2012-02-11
> **CProgramming said:**
> Thank you friend .
I try latter (because I'm working right now about project at eclipse , and if the suspend fail I will have to force restart my computer).

P.S , what are the diffidents between sudo and gksudo?

Gksudo works correctly for graphical appications, always loading the target user's (in this case root's) profile and environment variables correctly.

Sudo is only made for command-line use, and depending on the program in question using it with graphical applications might result in the application overwriting some of your normal user's setting files with root's permissions, making you unable to change the settings any more, or in worst case completely stopping you from even logging in at all as your normal user.

While some apps (Gedit, for example) usually work with sudo without causing problems, there is no way to make a reliable list of what apps work fine and what cause problems, and in the end remembering such list would be impossible as well. So it's best to just learn the habit of always using gksudo with graphical applications, that way you can be sure to avoid any problems.

(There's a similar reason to why you should always use "sudo -i" to start a root session in command line, "sudo su -" and "sudo -s" both fail to load root's environment correctly and you end using the normal user's environment instead)

---

### Post by CProgramming on 2012-02-11
> **mcduck said:**
> Gksudo works correctly for graphical appications, always loading the target user's (in this case root's) profile and environment variables correctly.

Sudo is only made for command-line use, and depending on the program in question using it with graphical applications might result in the application overwriting some of your normal user's setting files with root's permissions, making you unable to change the settings any more, or in worst case completely stopping you from even logging in at all as your normal user.

While some apps (Gedit, for example) usually work with sudo without causing problems, there is no way to make a reliable list of what apps work fine and what cause problems, and in the end remembering such list would be impossible as well. So it's best to just learn the habit of always using gksudo with graphical applications, that way you can be sure to avoid any problems.

(There's a similar reason to why you should always use "sudo -i" to start a root session in command line, "sudo su -" and "sudo -s" both fail to load root's environment correctly and you end using the normal user's environment instead)

Ok , thanks you
for some reason the fix doesn't works on my desktop,
Just on my laptop. When I suspend my desktop, I freezing on black screen. ._.

---

### Post by WorMzy on 2012-02-11
These are warnings, not errors. They can be ignored.

However, if you want to stop seeing them, try creating the .local/share folder in root's home.

```
sudo mkdir -p /root/.local/share/
```

---

### Post by CProgramming on 2012-02-12
> **CProgramming said:**
> Ok , thanks you
for some reason the fix doesn't works on my desktop,
Just on my laptop. When I suspend my desktop, I freezing on black screen. ._.

Do someone know why its unable to suspend my desktop?

OK the laptop that works great!

---

### Post by mcduck on 2012-02-13
> **CProgramming said:**
> Do someone know why its unable to suspend my desktop?

OK the laptop that works great!

That fix is intended for a specific hardware, so it sure isn't even supposed to work on every computer. Anyway, have you tried the other guide linked in that post? Or done as it suggests, and checked /var/log/pm-suspend.log for any information why the suspend is failing?

If you haven't, then do that now. And if that's not enough to point you to right direction, then post the log and detailed information about the hardware on your desktop machine here so people will have at least some information they can use to figure out what might be the problem...

---

