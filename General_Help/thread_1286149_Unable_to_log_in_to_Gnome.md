---
title: "Unable to log in to Gnome"
date: 2009-10-08
forum: General Help
---

### Post by GovDude on 2009-10-08
I've spent a bit of time on this and I finally found the culprit, but I can't explain it. I've removed all the ~/.bash* files and replaced it with my standard ~/.profile. In that file, among other things, I have the following line:

alias ls='/bin/ls --color=auto -CF'

That line causes gnome-session to immediately exit and I get the warning "Your session only lasted less than 10 seconds." and after clicking "OK" I'm back at the login screen. 

I traced it through the whole X login sequence all the way to /etc/X11/Xsession.d/99x11-common_start which invokes gnome-session and that's where it dies. The .xsession-errors has:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GPG_AGENT_INFO=/tmp/seahorse-qWYNam/S.gpg-agent:12377:1; export GPG_AGENT_INFO

and that's it. Seems to me that something in the gnome-session startup is probably trying to use the "ls" command and my alias is messing with it.

---

### Post by wojox on 2009-10-08
Try dropping into a root shell and changing it with nano to:

```
alias ls='ls --color=auto'
```

Don't know if that will work. You changed all the bash files or just the one's in your home folder?

---

### Post by GovDude on 2009-10-15
Tried the suggestion and that doesn't fix it. It's weird because it was fine initially. It was after a few updates that this started happening.

I only changed what's in my home folder. Got rid of all the various login files like .bashrc and just replaced them with the .profile.

Thanks,
Gary

---

