---
title: "Ubuntu Server: Can't shutdown from power button"
date: 2006-05-13
forum: General Help
---

### Post by bullgr on 2006-05-13
Hi...

Need help... please, it's important for me...

I have setup a Ubuntu file server with ubuntu server cd 5.10 "Breezy Badger" in my workplace.;)

Because the other co workers are "winblows zombies" i want to start and shutdown the pc from the power button.

Starting is ok... i power on the pc and leave it as it is in the login prompt without login and all works fine.

But to shutdown, the power button are not respond. I must login and shutdown from the command line.

For me its ok but for the "winblows zombies" is this unacceptable.
And i can't always there to shutdown the pc (vacation, sik etc).

In my home the power button works fine and for shutdown, but there i have the ubuntu desktop version installed.

The server pc is a P4 1.8

Thank's

---

### Post by skippy81 on 2006-05-13
Firstly you need to focus on ACPI, since it the powerbutton produces an ACPI event.  Therefore you want to have ACPI enabled in BIOS and in the Kernel - if you installed your server using "noacpi" as a boot option, then that would explain the problem.  

Try doing this from a terminal

 > sudo gedit /etc/acpi/events/powerbtn

This is what my file looks like:-

> # /etc/acpi/events/powerbtn
# This is called when the user presses the power button and calls
# /etc/acpi/powerbtn.sh for further processing.

# Optionally you can specify the placeholder %e. It will pass
# through the whole kernel event message to the program you've
# specified.

# We need to react on "button power.*" and "button/power.*" because
# of kernel changes.

event=button[ /]power
action=/etc/acpi/powerbtn.sh

as you can see it runs a script called powerbtn.sh that looks like this 

> #!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

[ -f /var/lock/acpisleep ] && exit 0

# If gnome-power-manager is running, let it handle policy
if [ `pidof gnome-power-manager` ]; then
  exit
fi

# Check for kpowersave
if [ `pidof kpowersave` ]; then
  exit
fi

# And for kded/klaptopdaemon
if test -f /usr/bin/dcop; then
  if [ "x$(dcop kded | grep klaptopdaemon)" != x ]; then
    exit
  fi
fi

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && test -f /usr/bin/dcop
then
    dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
else
    /sbin/shutdown -h now "Power button pressed"
fi

Check if your files look the same as mine.

---

### Post by bullgr on 2006-05-13
thank's for the quick response...

The problem is that were is not any
/etc/acpi
the folder does not exist...

Don't forget, i have Ubuntu Server installed

---

### Post by jtibau on 2006-05-13
Since the file server is used at an office I guess you want it to shutdown everyday at the same time... After everyone leaves.
Sounds to me like you could try setting up a task that shuts it down every day after office hours. I think the cron service manages that kind of stuff but I don't know how to configure it yet :( . I'll let you know if I figure it out soon...

---

### Post by bullgr on 2006-05-13
I find the solution... because a install from "Ubuntu Server cd" don't install acpi by default (like the desktop version), i must install it manualy

> sudo apt-get install acpid

and all is done... now everyone can shutdown the server from the power button (even the winblows zombies) without the need to login first.

Thank's for the help and for the quick response :-D

---

### Post by nexxus07 on 2008-07-15
Thank you, this was very helpful for stopping my virtualbox machines which are set up to start with the init.d. 

This script helped me a great deal in setting it up:
** [http://farfewertoes.com/code/vboxcontrol/](http://farfewertoes.com/code/vboxcontrol/)**

and  now they shut down and start up completely automatically which is just what I need.

---

