---
title: "Evil Netbook: Won't Let Me Log In :("
date: 2009-12-29
forum: General Help
---

### Post by 1awesomeguy on 2009-12-29
I have Ubuntu Netbook Remix 9.10. All packages are up-to-date and working (I did a retstart after the latest kernel upgrade).

I changed my main user's password in the User and Groups setting last night. Today, I cannot log in with my new password ("Authentication Failure"). I did remember using sudo last night using my new password. I can log in to my user account using the old password, but I get the following errors:

"Could not update ICEauthority file /home/chris/.ICEauthority"

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

"Nautilus could not create the following required folders: /home/chris/Desktop, /home/chris/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

Then I get the "Record your encryption passphrase" dialoge. It only tells me my passphrase with my new password.

Finally, I am left with just a blank screen showing my background and my mouse.


Summary: I can log in to Ubuntu using only my old password. My /home directory is encrypted using my new password.


Thanks in advanced for any help!

-Christopher

---

### Post by Brandon Williams on 2009-12-30
It sounds like your passwd wasn't completely updated somehow. After you log in, try running passwd in a terminal to change from your old password to the new one. Hopefully, this will update the things that weren't updated the first time.

---

