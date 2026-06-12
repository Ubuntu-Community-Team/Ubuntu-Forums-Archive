---
title: "Looking for distribution software"
date: 2010-02-05
forum: General Help
---

### Post by grkuntzmd on 2010-02-05
Sorry if this is not the correct forum, but...

My company has over 230 servers in the field (running Windoze Server 2003 with cygwin). I frequently write small admin utilities (in Bash or Java) and need to deploy them (new and updates) to all of the servers over ssh.

I run Ubuntu (9.10) on my laptop (don't ask about the Windoze servers -- it was NOT my decision).

Any suggestions for the best way to do this?

---

### Post by Bachstelze on 2010-02-05
rsync comes to mind, if you can put all your utilities in the same folder, you can then synchronize them periodically with it.

---

### Post by grkuntzmd on 2010-02-05
I wrote a (convoluted) deployment system in bash for sending updates to our main product, where I have to guarantee that an update goes through eventually, even if a machine is unreachable at the time of deployment, but I was hoping for a simple solution were reliability is not paramount. Something along the lines of:

   send-update -d "~/bin" file ...

where the send-update command would already have a list of destinations.

I guess I could write something like this as a bash script that uses rsync.

---

