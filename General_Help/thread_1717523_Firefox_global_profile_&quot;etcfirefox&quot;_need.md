---
title: "Firefox global profile &quot;/etc/firefox&quot; need help bypassing!"
date: 2011-03-30
forum: General Help
---

### Post by darknomel on 2011-03-30
Hi all,

I'm part of a team who is currently building an Ubuntu image for deployment of quite a lot of machines, all with different functions.

One of these functions being provisioned through an upstart job is an Internet-Kiosk type machine. This machine has a locked down firefox profile for itself stored in a directory.

My problem is that we have a profile in /etc/firefox so that everyones homepage is the same, but now we need this specific function to load it's own profile. 

I got the lockdown profile working semi ok but doing:
```
firefox -profile /path/to/profile.profile
```

But it's still pulling the homepage from /etc/firefox.

Can anyone give me any help please?

[COLOR="Red"]Nevermind, fixed it by adding the url of the required homepage to the command line launcher. SOLVED![/COLOR]

---

