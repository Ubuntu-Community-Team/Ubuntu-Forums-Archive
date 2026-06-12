---
title: "Guest account on login screen should not be default"
date: 2011-10-18
forum: General Help
---

### Post by danbuter on 2011-10-18
This is very bad security. 

I found a way to disable, though, on mdeslaur's blog. I wanted to post it here for people to find. Not sure if this works with regular Ubuntu. Many thanks to him!

[http://mdeslaur.blogspot.com/2011/10/how-to-disable-guest-account-in-oneiric.html](http://mdeslaur.blogspot.com/2011/10/how-to-disable-guest-account-in-oneiric.html)

Just sudo your text editor and "The guest account can be disabled by editing /etc/lightdm/lightdm.conf and adding "allow-guest=false" to the "SeatDefaults" section. "

I've used this on my laptop and it worked great.

---

