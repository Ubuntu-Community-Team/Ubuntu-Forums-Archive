---
title: "Lucid not loading all startup programs"
date: 2010-06-10
forum: General Help
---

### Post by BobvanderPoel on 2010-06-10
I've seen this a few times now and it's quite frustrating. When doing a cold start not all the necessary startup up programs are being started. Last night we had a storm, so I turned off my system ... and then booted later. Even later I tried to install some new programs and got lots of strange errors. I will not tell you of my bad language ... but after I manually started /etc/init.d/apt-cacher-ng all worked fine.

Any suggestions as to get all this working on EVERY boot?

---

### Post by BobvanderPoel on 2010-06-14
Bump ...

Yesterday I booted and neither apt-cacher-ng or cups were run. A reboot solved this ... but darned annoying when init doesn't init.

Nobody else with the same problem??? Or a fix??

---

### Post by nhong on 2010-06-23
I also have a simple command to open a ssh proxy connection in the start-up programs list and it doesn't work as well.

by the way, I found that there is a script to play a sound when login on the list doesn't work too.

Any ideas? I cant find a way to run a script at gnome login.

---

### Post by BobvanderPoel on 2010-06-23
Adding stuff to run when gnome starts up is easy enough. Just hit system->preferences->startup-applications

And then hit the <add> button to get your script added. I think the script has to be set to exec.

---

### Post by veko on 2010-09-22
I have the same problem: startup applications are not executed. The problem is not that I haven't set it up correctly and it's not executable. No, the application runs just fine if I execute it on command line. It did also run correctly in Karmic. I've tried to remove it and set it up again, but this does not help.

The application itself is just a simple shell script to toggle touchpad off when usb mouse is connected, see
[http://ubuntuforums.org/showthread.php?t=1310844&page=2#18](http://ubuntuforums.org/showthread.php?t=1310844&page=2#18)

 I'd appreciate some help or pointers how to fix this.

---

