---
title: "Problem booting into Ubuntu"
date: 2011-11-27
forum: General Help
---

### Post by benpack101 on 2011-11-27
So I was just getting Ubuntu 11.10 where I wanted it, as I ran into some problems with gnome-tweak-tool. I would run the program either through the Activities link in Gnome 3 and it would just sit there trying to load until the task just seemed to kill itself. Through the terminal, I was told there was an error regarding some 'gi' (I can find the error latter perhaps). (I've had Gnome3 shell installed alongside Unity)

Well from there something led me to think it was a problem with python and I made the mistake of sudo apt-get remove python. The removal of that failed, and I decided to restart to get a fresh look at this problem.

I believe before restarting i went sudo apt-get remove gnome-shell. (yep while in the shell)

Now when I boot into Ubuntu (Im dualbooting with win7) I get a black and white login screen and when I type in my password - or try to log in as a guest session, the screen flashes black and goes back to the login screen.

EDIT: When I type in my correct password, the screen quickly flashes, showing this,

"
Pulseaudio configured for per-user sessions
stopping anac(h)ronistic cron
stopping save kernal messages
starting CUPS printing spooler/server
starting Mount network filesystems

stopping Mount network filesystems
"

Looks like I really screwed it up.

Any and all help would really be appreciated!

---

### Post by benpack101 on 2011-11-27
So I was told to try

apt-get install ubuntu-desktop
apt-get install gnome-shell

and even though I am hardwired in, I was getting errors as though it is not connected to the internet

I am trying to follow this video [http://www.youtube.com/watch?v=KIK48qHA_RY](http://www.youtube.com/watch?v=KIK48qHA_RY) - i can follow all of the directions through the final ping (which fails)

then when i try to run the apt-get install ubuntu-desktop again, I get the error "something wicked happened resolving "us.archive.ubuntu.com:http" (-5 - no address associated with hostname)

This then continues to happen with all of the ppas after spending a few seconds trying to connect to each

Help would be much appreciated!

---

### Post by oldtimer7777 on 2011-11-27
Gnome 3 is still in development. You are bound to have problems... 

Did you install the Gnome 3 development PPA yet? 

> **benpack101 said:**
> So I was told to try

apt-get install ubuntu-desktop
apt-get install gnome-shell

and even though I am hardwired in, I was getting errors as though it is not connected to the internet

I am trying to follow this video [http://www.youtube.com/watch?v=KIK48qHA_RY](http://www.youtube.com/watch?v=KIK48qHA_RY) - i can follow all of the directions through the final ping (which fails)

then when i try to run the apt-get install ubuntu-desktop again, I get the error "something wicked happened resolving "us.archive.ubuntu.com:http" (-5 - no address associated with hostname)

This then continues to happen with all of the ppas after spending a few seconds trying to connect to each

Help would be much appreciated!

---

### Post by benpack101 on 2011-11-27
Yes I have,

My good friends at OCN helped me out with this, in the recovery mode I was able to reinstall ubuntu-desktop and gnome-shell.

Oh and by the way, Gnome 3 has been officially released, but it is still in development, like all linux software, people are always working on improving it.

And there is no PPA necessary for GNOME 3 by default it is in the repository.

Thanks anyways for the help!

---

