---
title: "Flaw in GDM and custom xsessions."
date: 2010-05-09
forum: General Help
---

### Post by xinix on 2010-05-09
Please help confirm this before I submit a bug report.  I get the same results on two computers.

For a long time I've used a custom xsession that loads Mythtv without any sort of desktop environment.  Every time I upgrade I've just backed up and restored my xsessions entry.  I did the same when switching to 10.4 only to find that the custom xsession entry causes gdm to login WITHOUT a password.

When I select the custom xsession in GDM I get logged in immediately without a password or confirmation.  The expected behavior is that I'd select the xsession and not get logged in until after entering my password.  I've done some trial and error with this issue and it seems that it boils down to a single line in the custom xsession file.

This will fail to require a password:
In /usr/share/xsessions I have a file called "fail.desktop" with this content:
```
[Desktop Entry]
Encoding=UTF-8
Name=Fail
Exec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0
```

I looked at the way more recent xsession entries are formatted and saw that the have this line:
```

Comment= comment about what the entry loads 
```

Adding this line to the xsession entry causes GDM to behave as expected.
So, this will work properly:
```
[Desktop Entry]
Encoding=UTF-8
Name=Fail
Comment= this needs to be here?
Exec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0
```

It seems to me that things should work as expected with or without a comment line and that a malformatted xsession entry shouldn't give access to the system.

---

### Post by dino99 on 2010-05-09
few minutes ago i've got a new gdm package which fix lot of problems: 2.30.2-0ubuntu1

---

### Post by xinix on 2010-05-09
I just did the update and I'm still able to reproduce this problem.

---

### Post by mmix on 2010-05-15
Definitely, It has flaw.
Why not support xorg-x11-xinit-session (fedora) in Ubuntu?

---

### Post by xinix on 2010-05-15
If you can reproduce this, it would be good if you could confirm this in the bug report.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/578414](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/578414)

---

