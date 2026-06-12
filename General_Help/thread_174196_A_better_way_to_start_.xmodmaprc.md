---
title: "A better way to start .xmodmaprc?"
date: 2006-05-11
forum: General Help
---

### Post by tsb on 2006-05-11
I added an executable in command form 'xmodmap ~/home/user/.xmodmaprc' in the Autostart folder so my volume keys would work.  It works fine, but it takes forever to disappear when it runs.  Is there a better way?

thanks

---

### Post by Luke on 2006-05-11
i thought KDE would automatically run xmodmap on the file named ".Xmodmap" in the user's home directory. i don't think you need to call xmodmap explicitly. just make sure your customized xmodmap is named correctly and located in ~:   [COLOR="Red"].Xmodmap[/COLOR] (note the capital 'X')

---

### Post by tsb on 2006-05-11
Not sure what you mean by "~: .Xmodmap", but I tried it in my /home/user/ directory with both big and small "x"  but it never works.

---

### Post by asimon on 2006-05-12
No, KDE will not start it automatically. Gnome's login manager gdm calls xmodmap it in it's Xsession script but kdm doesn't.

So either put it into KDE's Autostart folder, an executable script into ~/.kde/env/, or a script into /etc/X11/Xsession.d/, or modify /etc/kde3/kdm/Xsession. Many possibilities.

EDIT:
see [bug 27839](https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27839).

---

### Post by Luke on 2006-05-12
[QUOTE=asimon]No, KDE will not start it automatically. Gnome's login manager gdm calls xmodmap it in it's Xsession script but kdm doesn't.

So either put it into KDE's Autostart folder, an executable script into ~/.kde/env/, or a script into /etc/X11/Xsession.d/, or modify /etc/kde3/kdm/Xsession. Many possibilities.

EDIT:
see [bug 27839](https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27839).[/QUOTE]

OK. sorry 'bout that. it works that way in SUSE 10.0 but i guess they must have changed something in KDM. i thought it was just a generic KDE/KDM thing. thanks for clearing that up.

---

### Post by tsb on 2006-05-12
[QUOTE=asimon]No, KDE will not start it automatically. Gnome's login manager gdm calls xmodmap it in it's Xsession script but kdm doesn't.

So either put it into KDE's Autostart folder, an executable script into ~/.kde/env/, or a script into /etc/X11/Xsession.d/, or modify /etc/kde3/kdm/Xsession. Many possibilities.

EDIT:
see [bug 27839](https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27839).[/QUOTE]

So the only way to do it is to start a launcher from Autostart like I am doing now?  Can someone help me set up a terminal command script?  Maybe that would work faster.

Thanks.

---

### Post by tsb on 2006-05-12
[QUOTE=asimon]No, KDE will not start it automatically. Gnome's login manager gdm calls xmodmap it in it's Xsession script but kdm doesn't.

So either put it into KDE's Autostart folder, an executable script into ~/.kde/env/, or a script into /etc/X11/Xsession.d/, or modify /etc/kde3/kdm/Xsession. Many possibilities.

EDIT:
see [bug 27839](https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27839).[/QUOTE]

So the only way to do it is to start a launcher from Autostart like I am doing now?  Can someone help me set up a terminal command script?  Maybe that would work faster.

Thanks.

---

### Post by tsb on 2006-05-12
so the only solution is what I'm doing now?  how can I run the command in konsole on startup?  maybe that would be faster.

---

### Post by tsb on 2006-05-12
so the only solution is what I'm doing now?  how can I run the command in konsole on startup?  maybe that would be faster.

---

### Post by asimon on 2006-05-12
This should work:
```

mkdir -p ~/.kde/env
echo 'test -r ~/.Xmodmap && xmodmap .Xmodmap' > ~/.kde/env/xmodmap.sh

```

All *.sh files in ~/.kde/env will get executed when the KDE session starts.

---

### Post by tsb on 2006-05-12
sorry about my newbness

do I now write the commands to label the keys in the xmodmap.sh file in /env?

I have 

keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume


or is this a command to link to another xmodmap file?

**Nevermind I figured it out.  It links to the .Xmodmap file in my home folder and works perfectly.  No slow running like before.  Thanks a lot!

---

### Post by asimon on 2006-05-12
[QUOTE=tsb]sorry about my newbness

do I now write the commands to label the keys in the xmodmap.sh file in /env?
[/quote]
No, the xmodmap.sh only calls the xmodmap program which modifies the keymap according to the content of ~/.Xmodmap.

[QUOTE=tsb]
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
[/QUOTE]
You put those keycodes into ~/.Xmodmap

[QUOTE=tsb]
**Nevermind I figured it out.  It links to the .Xmodmap file in my home folder and works perfectly.  No slow running like before.  Thanks a lot![/QUOTE]
Damn! I should really read the whole message before replying. ](*,)

---

### Post by wasert on 2007-01-06
what about Xubuntu?

how do you tell xfce to automatically read .xmodmaprc

thanks

---

