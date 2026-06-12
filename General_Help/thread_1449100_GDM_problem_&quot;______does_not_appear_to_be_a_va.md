---
title: "GDM problem: &quot;_____ does not appear to be a valid theme.&quot;"
date: 2010-04-07
forum: General Help
---

### Post by SnickerSnack on 2010-04-07
After looking at art.gnome.org, I found a gdm theme that I like, but I can't seem to use it.

I've used

```
~$ sudo -u gdm dbus-launch gnome-appearance-properties
```

so I can modify the gdm theme, and that works.  But, I don't know how to install a whole theme.  When I try to install the .gz file, I get this error:

> There was an error installing the selected file
"sharp" does not appear to be a valid theme.

So, I unpacked it, and these are the files in sharp:

```
bg.png
button_inactive.png
GdmGreeterTheme.desktop
screenshot.jpg
button_active.png
button_prelight.png
loginbox.png
sharp.xml
```

I've tried installing the GdmGreeterTheme.desktop and sharp.xml, but both give the same error.  Nothing in the download appears to be a "theme package", aside from the .gz.

Help?

---

### Post by SnickerSnack on 2010-04-08
bump

---

### Post by SnickerSnack on 2010-04-12
another bump

---

### Post by SnickerSnack on 2010-04-24
Pretty please?

---

### Post by allstar1960 on 2010-04-24
Why Why Why?

I feel Ubuntu is one of the bext Linux distros out there with a huge community to support it. If freedom is the keyword in Ubuntu, why have we lost the ability to change the GDM theme? Even Kubuntu's KDE 4 allows you to do it. PCLinusOS Gnome was recently released and you can cahnge the GDM theme there.

Why has it gotten so difficult? I feel this is the first step in losing control over making changes to my distro.

I, too have had problems trying to change the GDM theme.

I am pretty darned sure that I am not the only one with this issue.

I have tried downloading the GDM2Setup, but now it does not work. I have tried changing the theme by using sudo and I only have a little control.

We need the GDM changer BACK!

---

### Post by allstar1960 on 2010-04-24
Type in

gksudo -u gdm dbus-launch gnome-appearance-properties

That should let you make changes.

Then to get rid of the wheelchair icon in the panel,

go to "system-preferences-keyboard-accessibility" and uncheck the "Accessibility features can be toggled with keyboard shortcuts"

---

### Post by SnickerSnack on 2010-04-27
Hmmmm, I thought I had already replied....

> **allstar1960 said:**
> Type in

gksudo -u gdm dbus-launch gnome-appearance-properties

That should let you make changes.

I've done that, as per the first post.

> **allstar1960 said:**
> Then to get rid of the wheelchair icon in the panel,

go to "system-preferences-keyboard-accessibility" and uncheck the "Accessibility features can be toggled with keyboard shortcuts"

Thanks, that was helpful.

---

### Post by towheedm on 2010-04-28
Check out the link at the beginning of this post if you really want to customize GDM beyond what's possible with gnome-appearance-properties:

[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by SnickerSnack on 2010-05-01
> **towheedm said:**
> Check out the link at the beginning of this post if you really want to customize GDM beyond what's possible with gnome-appearance-properties:

[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

Oh boy, I'll have to find some time to go through that. :)

Thanks!

---

### Post by Vaphell on 2010-05-01
the problem is that gnome devs cut a lot of login screen functionality to speed things up and regrettably gdm themes are obsolete now. Installing themes doesn't work anymore.

---

### Post by SnickerSnack on 2010-05-30
> **Vaphell said:**
> the problem is that gnome devs cut a lot of login screen functionality to speed things up and regrettably gdm themes are obsolete now. Installing themes doesn't work anymore.

Thanks.

---

