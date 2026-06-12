---
title: "notify-send over ssh"
date: 2010-04-04
forum: General Help
---

### Post by DuXati on 2010-04-04
Hi all,

I know this has been asked before, but I need some help with notify-send over ssh. I'm using an ssh connection between my local computer (Ubuntu 9.10) and a remote server (Ubuntu 8.04 LTS). I'm trying to use the command notify-send to allow the server to notify me when something happens. So I've installed libnotify-bin on both computers and connect with ssh -X. But notify-send does not produce a result...

I don't get an error, but there just isn't any result. The terminal gives a flinch, but no notification is shown.

I know this isn't a lot of information. Are there logs I can check or something like that?

Thanks in advance,

DuXati

---

### Post by terrrorr on 2010-04-04
Hi,

Check this one out. I hope it helps you

[http://ubuntuforums.org/showthread.php?t=1240828]("http://ubuntuforums.org/showthread.php?t=1240828")

---

### Post by DuXati on 2010-04-05
Thanks! 

If I try the ssh command with the command to be executed on the server, I get the error "libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.". This seems to be result of "DISPLAY=:0". 

I've searched around for this environment variable and found out it specifies the display to send the X commands to. Now, the variable  is set to "localhost:10.0". Do you know what value the variable should be to send commands over ssh? The part before the colon should be a host name ([https://help.ubuntu.com/community/EnvironmentVariables#Graphical desktop-related variables]("https://help.ubuntu.com/community/EnvironmentVariables#Graphical desktop-related variables")), so what's the host name of a connected computer?

DuXati

---

### Post by jamesisin on 2012-02-11
Did you ever get this sorted?  I'm trying to send messages remotely using notify-send over ssh and am also getting dbus errors.

---

### Post by DuXati on 2012-02-12
Nope, never got this working. Stopped looking for a solution after some time, a shame. If you do find one, please let me know :)

DuXati

---

### Post by jamesisin on 2012-02-12
I can't get any of these to work remotely:

[http://smashingweb.ge6.org/send-messages-over-network-gnome-popup-box-message/](http://smashingweb.ge6.org/send-messages-over-network-gnome-popup-box-message/)

---

