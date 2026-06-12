---
title: "Auto VLC startup in CLI only install"
date: 2009-07-28
forum: General Help
---

### Post by n1wil on 2009-07-28
I have an application where I need to have VLC start playing a looped playlist upon system startup.  I obviously can't run it as root.  

The system has Ubuntu 9.04 install with NO GUI.  I would rather not run a GUI on this box as I don't want people interacting with it.

In my application, it is intended to be remotely administered via webmin.

So here goes my question:

When I run the command:
vlc -I http -Z -L --volume 500 /home/john/list.m3u

in a SSH terminal or on the local console when logged into the keyboard, VLC runs just find and the machine outputs sound - no problem.

I'd like to have this done at startup right after the system boots and that's where I'm having the problem.  I have tried inserting the command in /etc/rc.local as such:

su username -c 'vlc -I http -Z -L --volume 500 /home/john/list.m3u'

and I would think this should work, but it doesn't.  Can anyone help me?

This problem is VERY frustrating!

---

