---
title: "Banshee Panel Icon Overhang"
date: 2010-05-07
forum: General Help
---

### Post by Ahriman on 2010-05-07
When I run Banshee (installed from the repos, no bleeding edge version here) and I close it to the Gnome Panel, the icon overhangs the panel by a few pixels.
This picture shows what I mean: [http://yfrog.com/0ubansheequestionp](http://yfrog.com/0ubansheequestionp)
[IMG]http://nikonizer.yfrog.com/Himg30/scaled.php?tn=0&server=30&filename=bansheequestion.png&xsize=640&ysize=640[/IMG]
I have tried increasing the panel height (currently on the lowest settings - 20) but this doesn't help at all. Any ideas on what I can do?

---

### Post by Ahriman on 2010-05-08
Alternatively, is there another place I can ask for help that might be more specific to my problem?

---

### Post by insanity54 on 2010-05-31
Heh, at least yours looks normal! (minus the overhang)

here's what mine looks like:
[IMG]http://img683.imageshack.us/img683/4707/screenshotzl.png[/IMG]
...Ugly as sin. I hate it.

It's supposed to have a transparent background:
[IMG]http://img24.imageshack.us/img24/4331/screenshot1ki.png[/IMG]
...But it's a misbehaving icon and it insists on being opaque.

I think I might just go into:
```
/usr/share/icons/ubuntu-mono-dark/apps/24
```
...and make myself a custom icon, since it looks absolutely ridiculous right now; the icon looks like a broken cd with a number one sticking out the top of it.

Take a look at this:
[IMG]http://img532.imageshack.us/img532/1411/screenshot2on.png[/IMG]
...I was curious so I made my panel size really big. It seems that I have the same problem as you do (notice the System Monitor stops a pixel short of the bottom of the panel, but banshee's Notification area icon does not), but it's not really noticeable with my panel theme because I don't have a horizontal black line on the bottom of my panel like you do:
[IMG]http://img35.imageshack.us/img35/5950/bansheequestion.png[/IMG]

Basically the system theme has that panel background with a 1px line going across the entire bottom, and banshee's notification icon is naughty and doesn't care that it's standing on top of a nice looking line.

Going back to my problem, as a workaround, I was thinking I could make a better icon for myself and put it in:
```
/usr/share/icons/ubuntu-mono-dark/apps/24
```
(that is, IF I can get it to be transparent as it should be.) While I'm at it, if you're interested, I could redo your icon so that it has a transparent backing which also has a "buffer" of a couple pixels at the bottom which are transparent, so it would still be on top of the horizontal panel line, but it won't appear that way, because the bottom of the icon is transparent instead of being opaque and covering up your panel line.

Hopefully I made some sense in my extremely sleep deprived state, lemme know if that helps at all!

---

### Post by Ahriman on 2010-06-03
The way I got around it was to tell Banshee not to minimize to the tray, and add the 'Indicator Applet' to the panel. I also enabled the 'Application Indicator for Banshee' extension inside Banshee - which lets the program be 'closed' to the new indicator applet (and controlled in a limited way).

I did consider going the route you are taking and fiddling with the icon itself, but, with my knack for breaking systems irreparably, I decided against. :D

---

### Post by insanity54 on 2010-06-04
Haha, yeah Ahriman, that sounds like a simpler approach. The more I think about it, I don't think my idea will even work, because the banshee icon already has a transparent background, but something is keeping it from being transparent. I think the same would happen to any custom icon I make.

---

### Post by frogotronic on 2011-06-26
Here's the fix:

[http://askubuntu.com/questions/44628/weird-notification-area-bug-with-banshee](http://askubuntu.com/questions/44628/weird-notification-area-bug-with-banshee)

- CH

---

