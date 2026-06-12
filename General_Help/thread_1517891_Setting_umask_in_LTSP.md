---
title: "Setting umask in LTSP"
date: 2010-06-25
forum: General Help
---

### Post by JoelAV on 2010-06-25
Hey all,

I'm setting up an application server for a small organization using Ubuntu 10.04 and LTSP.  We built a machine with a quad core Athlon II, got a Gigabit swtich, and a couple Gigabit ethernet cards.  I burned gPXE into a couple EPROMs and turned their old PIII and Duron systems into thin clients.

So far so good.

Now, I'm trying to set up a shared directory that two users in the same group can both read and write.  Let's call it "/home/shared".  I want to set UMASK to 007, so that by default, files are created readable and writable by user and group, with no permissions for anybody else.  I changed a line in "/etc/profile" from "umask 022" to "umask 007".  After rebooting the app server, the umask does appear to be 007 when you log in at the console.  However, it doesn't seem to affect the terminals.

So I figured I needed to change it in "/opt/ltsp/i386/etc/profile".  vi helped me out with that.  Didn't make a difference in the terminals.  Ok, I need to rebuild the image, so I did an "ltsp-update-image" and rebooted the terminal.  umask is still 022.  ???

I changed UMASK in "/opt/ltsp/i386/etc/login.defs" and rebuilt the image.  No change.  ???  I really don't understand why this isn't working.  

How can I change the UMASK for users who log in on an LTSP terminal?

JCE

---

### Post by JoelAV on 2010-06-28
Any ideas?

---

### Post by JoelAV on 2010-06-30
I finally found the answer here:  [http://ubuntuforums.org/showthread.php?t=711066]("http://ubuntuforums.org/showthread.php?t=711066")

Should this go in the Ubuntu LTSP Wiki?

---

### Post by mrln on 2012-03-22
> **JoelAV said:**
> I finally found the answer here:  [http://ubuntuforums.org/showthread.php?t=711066](http://ubuntuforums.org/showthread.php?t=711066)

Should this go in the Ubuntu LTSP Wiki?

Hello!

 Please add this to the LTSP Wiki very important!

I lost it a long time ago

---

