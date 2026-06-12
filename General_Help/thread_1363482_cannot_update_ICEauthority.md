---
title: "cannot update ICEauthority"
date: 2009-12-24
forum: General Help
---

### Post by danastasio on 2009-12-24
hi I'm running on ubuntu 9.10. After a restart I got the error "Could not update iceauthority file /home/dntel/.iceauthority"

followed by:
"there is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256"

and then:
"nautilus could not create the following required folders: /home/dntel/desktop, /home/dntel/.nautilus. Before running nautilus, please create these folders, or set permissions such that nautilus can create them."

I know that most people say that 
```
sudo chown dave:dave /home/dave/.ICEauthority
sudo chmod 644 /home/dave/.ICEauthority
```

does the trick, but in my case, it does not, also, it was suggested that I remove the file. I did that... and the system never regenerated it. So I can't even attempt any chmod/chown commands... I have 30 or 40 gigs of college stuffs that I was going to back up today. (I do make regular backups, i swear!)
I dont know what I can do. I made another user and i dont want to copy the file because i dont know if there is any user specific information in there. I tried nano-ing the file, but its not written in plain text so that was a no go. Any ideas?
Happy merry christmas eve!

---

### Post by danastasio on 2009-12-28
Alright, this goes out to anyone who may stumble across this in the future should they run into the same issue I had. So far as I know, this is not fixable. It is possible to make a new user and copy the file into your own ~/ however you have to chown and chmod every. single. time. you logout/shutdown. The only thing you can do is to backup and re-install Ubuntu. Don't bother trying to delete .dmrc or .ICEauthority either, the system wont re-generate the files.
Anyway, I'm off to re-install

<rant>
and because my computer wont effing burn a CD right, i'll be upgrading from Hardy to Karmic all day D=
</rant>

I wish you better luck than me!

Mods: I'm not marking this as solved  because it isn't and I dont want to confuse anyone who happens across this in a search engine.

---

