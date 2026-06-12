---
title: "Do you know any way of syncing Chrome bookmarks without using a google account?"
date: 2011-04-19
forum: General Help
---

### Post by TheHimself on 2011-04-19
I'm looking for a way of syncing my bookmark without using a third party service.

---

### Post by lovinglinux on 2011-04-19
> **TheHimself said:**
> I'm looking for a way of syncing my bookmark without using a third party service.

I think Xmarks can be used with a personal server, but I am not sure.

---

### Post by TheHimself on 2011-04-20
No, Xmarks uses its own server.

---

### Post by Grenage on 2011-04-20
Could you not fashion something rudimentary?  A cron script which checks a file on an FTP server, downloads if the remote is more recent, or uploads if the local is more recent?

---

### Post by TheHimself on 2011-04-20
Yeah, I'm thinking of something like this but I don't know how the script should interact with chrome. I once replaced the bookmarks file in the chrome folder while it was running and didn't get the desired result. Maybe I should restart the browser after each update (which is a little bit inconvenient).

---

### Post by Grenage on 2011-04-20
> **TheHimself said:**
> Yeah, I'm thinking of something like this but I don't know how the script should interact with chrome. I once replaced the bookmarks file in the chrome folder while it was running and didn't get the desired result. Maybe I should restart the browser after each update (which is a little bit inconvenient).

Yes, that's not quite as slick;  I imagine that the bookmarks are loaded when Chrome is run, then accessed in memory (or elsewhere on disc).  A shortcut could run the script and *then* run chrome, *then* run again when Chrome was closed.

If a script won't advance until it has completed its current task, then it wouldn't progress to the final sync until chrome had been closed down.

It's a very dirty hack, but it might serve your purposes.

---

