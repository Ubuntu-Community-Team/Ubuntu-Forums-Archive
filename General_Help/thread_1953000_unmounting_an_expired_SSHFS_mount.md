---
title: "unmounting an expired SSHFS mount"
date: 2012-04-05
forum: General Help
---

### Post by hojjat on 2012-04-05
This has happened to me a number of times, and I don't know the solution (should be simple).

I mount a remote server to a local mount point using sshfs like this:
```
sshfs remote.domain.com:/dir ~/remote
```

Then I forget to unmount it at the end (using *fusermount -u ~/remote*) and hibernate my ubuntu machine.

I switch on my machine tomorrow, and the mount is not working. I also can't unmount it using *fusermount* because it gives me the "still in use" error message. The only thing I can do is to restart the machine :(

There should be a way to get rid of a SSHFS mount which is not functioning anymore (because the connection to the server has been lost for hours). How can I do that?

---

### Post by hojjat on 2012-04-11
bump

---

### Post by Lars Noodén on 2012-04-11
It might be a legitimate bug in SSHFS

[http://sourceforge.net/apps/mediawiki/fuse/index.php?title=SshfsFaq#I.27ve_found_a_bug_and_there.27s_no_solution_in_this_FAQ.2C_what_should_I_do.3F](http://sourceforge.net/apps/mediawiki/fuse/index.php?title=SshfsFaq#I.27ve_found_a_bug_and_there.27s_no_solution_in_this_FAQ.2C_what_should_I_do.3F)

Follow the link titled "Link to the download information" under the image of your choice.

---

### Post by hojjat on 2012-04-19
For now, I've learned that by killing the sshfs first, I can run fusermount with no errors.

---

