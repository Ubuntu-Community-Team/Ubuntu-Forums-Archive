---
title: "enable remote desktop by command line in 10.4 lucid"
date: 2010-06-26
forum: General Help
---

### Post by louisJ on 2010-06-26
Hi

how to enable remote desktop by command line in 10.4 lucid?
The command 
sudo gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
doesn't work, because when I open /system/pref/remote desktop,  it is still not activated.

Any idea?

Thanks

---

### Post by geirha on 2010-06-26
Firstly, running gconftool-2 as sudo is definately wrong. If something's not working right away, don't just put sudo in-front and think it'll magically work.

Secondly, gconftool-2 needs to know how to contact dbus. This is unfortunately cumbersome. The first thing you need to know, is which display the X server is running at. If you have only logged in with one user, the display number is usually 0, so if we assume that:

```

# display number, assuming 0
display=0

# get the machine-id
read -r machineid < /var/lib/dbus/machine-id

# source the right file under .dbus to set the needed variables
. "$HOME/.dbus/session-bus/$machineid-$display"

# export the variables sourced from that file
export DBUS_SESSION_BUS_ADDRESS DBUS_SESSION_BUS_PID DBUS_SESSION_BUS_WINDOWID

# Run gconftool-2
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

```

EDIT: The above is if you ssh in (or similar) to your box. If you are running it locally, the above should not be needed as the needed variables will be inherited; you only need to remove the sudo.

---

### Post by louisJ on 2010-06-26
Thanks a lot [geirha]("http://ubuntuforums.org/member.php?u=243323")

I am using it locally (as a newbie as you could guess) so it works without sudo.
thanks

---

### Post by bodhi.zazen on 2010-06-26
Just be aware that VNC is easily cracked. Be sure you secure the connection.

---

### Post by louisJ on 2010-06-26
yes I go through an ssh tunnel
thanks anyway

---

### Post by louisJ on 2010-06-28
an other thing:
with command line,
how to deactivate the confirmation "you must confirm each access to this machine" and activate "allow other users to control your desktop" ?

edit: ok I just figured it out:
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/view_only false

---

