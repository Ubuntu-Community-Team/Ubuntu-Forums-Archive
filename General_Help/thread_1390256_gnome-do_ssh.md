---
title: "gnome-do ssh"
date: 2010-01-25
forum: General Help
---

### Post by idlehands on 2010-01-25
I'm trying to figure out the best way to use gnome-do and have colored gnome-terminal windows based on ssh host

Anyone have hints? I figured I could set a bunch of gnome-terminal profiles with the colors I like, and then set some .ssh/config hosts based on the profile names, but I'm not sure how to tie the two together as the only way I know to start the gnome-terminal is with a gnome-terminal -window-profile="profile.name"

Hints?

Thanks

---

### Post by idlehands on 2010-01-29
Here's a solution I worked through with a friend, using info from here:

[http://magazine.redhat.com/2007/11/27/advanced-ssh-configuration-and-tunneling-we-dont-need-no-stinking-vpn-software/](http://magazine.redhat.com/2007/11/27/advanced-ssh-configuration-and-tunneling-we-dont-need-no-stinking-vpn-software/)


I setup an .ssh/config with the hosts and users that i wanted like so:
```

Host xbmc
    HostName 192.168.1.152
    Port 22
    User johann

```

then I created a launcher item under applications with the following:
Name: <host>
Command: gnome-terminal --window-with-profile=xbmc -x ssh xbmc

saved it, and now
gnome-do xbmc
launches a terminal with the colors i want to xbmc

---

