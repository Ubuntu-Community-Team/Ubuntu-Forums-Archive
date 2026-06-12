---
title: "mplayer plugin not working in mozilla... :("
date: 2006-06-01
forum: General Help
---

### Post by user1397 on 2006-06-01
i installed the mozilla-mplayer plugin but when i try to view videos in firefox, it doesn't work!!!

---

### Post by Rackerz on 2006-06-01
If you've got the w32codecs installed I'd try the 'totem-xine-firefox-plugin' instead, I'm using it and it performs better than Mplayer for me. Or do you need mplayer specifically?

---

### Post by user1397 on 2006-06-01
[quote=Rackerz]If you've got the w32codecs installed I'd try the 'totem-xine-firefox-plugin' instead, I'm using it and it performs better than Mplayer for me. Or do you need mplayer specifically?[/quote] i do have the w32 codecs installed.  ill try the totem-xine plugin.  can you point me to a site that you know works with it?

---

### Post by Rackerz on 2006-06-01
[http://www.apple.com/trailers/sony_pictures/zathura/](http://www.apple.com/trailers/sony_pictures/zathura/)

It worked great for me on that site.

---

### Post by user1397 on 2006-06-01
[quote=Rackerz][http://www.apple.com/trailers/sony_pictures/zathura/]("http://www.apple.com/trailers/sony_pictures/zathura/")

It worked great for me on that site.[/quote]okay that worked thanks
i hate how yahoo trailers never work!!! :evil:

---

### Post by Rackerz on 2006-06-01
[QUOTE=erik1397]okay that worked thanks
i hate how yahoo trailers never work!!! :evil:[/QUOTE]

Lol. No problem ;).

---

### Post by persev on 2006-09-13
> **erik1397 said:**
> okay that worked thanks
i hate how yahoo trailers never work!!! :evil:

Here is how I got them to work.

Well I got it working! Took 3 days but finally success!  Okay here is what I did- first I removed w32codecs, mplayer, mozilla-mplayer, gstreamer0.10-pitfdll via synaptic; then I did "sudo apt-get remove automatix" in a terminal; then installed the latest version of Automatix; finally reinstalled codecs and Swiftfox browser with plugins. 
Now everything works in Swiftfox but if I open Firefox yahoo news videos still won't play in it.  I'm not sure which of these operations did the trick and I not going to undo everything to find out either as long as everything works under Swiftfox.

---

