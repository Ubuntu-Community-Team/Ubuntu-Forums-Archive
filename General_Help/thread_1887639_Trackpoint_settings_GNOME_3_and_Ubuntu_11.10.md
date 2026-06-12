---
title: "Trackpoint settings GNOME 3 and Ubuntu 11.10"
date: 2011-11-27
forum: General Help
---

### Post by digib on 2011-11-27
Trying to get my trackpoint settings in a GNOME 3 ubuntu install to work. What I need to do is adjust the sensitivity and speed, that is all. It seems like all the old methods described are now deprecated and do not work [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Any ideas? This here GNOME 3 hassle makes me tired of upgrading. Some true geek should come up with the ultimate GUI for us Thinkpad users to have an easier life :)

Thx in advance for your responses.

---

### Post by paaitken on 2011-12-06
Hi, I've found that the native gnome mouse setting works well on my Thinkpad X61. It has settings for sensitivity and acceleration. Another useful little tool is gpointing-device-settings, also called "Pointing Devices" in the software centre. It works well for defining scrolling sensitivity and middle button emulation (and allows for extra configurations of external mice and trackballs).

[https://launchpad.net/ubuntu/+source/gpointing-device-settings](https://launchpad.net/ubuntu/+source/gpointing-device-settings)

Hope that helps!
[B]
[/B]

---

### Post by MountainX on 2011-12-10
Actually, I agree with the OP, [digib]("http://ubuntuforums.org/member.php?u=856567"). I want my TrackPoint sensitivity and speed to be much higher. I've been using gpointing-device-settings in the past (gnome 2) and I'm using it now in gnome 3, but it isn't doing the trick. I have not found any solution in gnome 3 yet. I'm using a ThinkPad E520.

---

### Post by MountainX on 2011-12-10
I learned a few things. 


[LIST=1]
[*]The xinput set-prop method from this page still works in gnome 3: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)
[*]gpointing-device-settings apparently does not work in gnome 3: [https://bugzilla.redhat.com/show_bug.cgi?id=710053](https://bugzilla.redhat.com/show_bug.cgi?id=710053)
[*]this method worked for me, but I haven't made it permanent yet: [http://www.linuxlog.org/?p=107](http://www.linuxlog.org/?p=107) (I'm thinking about better ways to make it permanent)
[/LIST]

---

