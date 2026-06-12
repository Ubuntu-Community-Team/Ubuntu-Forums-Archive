---
title: "Associate magnet links to Chromium"
date: 2012-09-17
forum: General Help
---

### Post by Galdov on 2012-09-17
Hi

I've been looking for hours and found some tutorials but i have no luck, I could perfectly do it in Firefox by adding a boolean, but I use Chromium a lot and couldn't get it working

I'm using qbittorrent in Ubuntu 10.04


What i did was in a terminal:

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission %s" 

gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool 

gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

but changed to qbittorrent where says transmission, and it gives me this message:

> Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details - 1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

didn't understand very well what is trying to tell me :(

and also the tutorial told me to edit the /usr/bin/xdg-open and add the line "DE=gnome" where it says

[IMG]http://i.imgur.com/3UAt2.png[/IMG]

but the magnet links still dont work with Chromium, giving me this message:

[IMG]http://i.imgur.com/n0y6P.png[/IMG]

any ideas? :D

---

