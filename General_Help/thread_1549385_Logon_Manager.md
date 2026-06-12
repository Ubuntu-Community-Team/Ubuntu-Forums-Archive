---
title: "Logon Manager"
date: 2010-08-09
forum: General Help
---

### Post by TuxIsCute on 2010-08-09
Hi Ubuntu People Out There,

I updated to the newest Ubuntu release (10.04 LTS) bypassing the 9 series altogether and I like it for the most part.  The first thing I had to do, though, was put my close, minimize, and maximize buttons back in the right place.  Not a hard fix at all.  Then I had to reinstall my NVIDIA graphics driver and reset-up my dual monitors. This wasn't difficult either although I did forget how to run the NVIDIA X Configuration application as root.  But I got that sorted quickly and updated my x configuration.

But now, I face a problem that I simply cannot get around (and neither, it seems can my friend Google) and so I come here to the ether of the internet for a helping hand.  I want my old login back.  I don't want it to be Windows-ish where you click your name and enter the password.  I want to have to type the username and password in again to login.  I know in previous releases you could use both systems and switch between them, but I can no longer seem to get it to let me switch it back.  Please help me do this.  I don't care if I have to rip Ubuntu apart and rebuild the thing with gaffer tape just to have that functionality returned to me.  I need it the way it was.

Also, and this is simply an addendum, but the application to make the NUMLCK key be on at system boot is no longer supported.  I remember reading a while back that in future releases Ubuntu wanted to write this in natively so is it there yet?  If not, how can I make that blasted NUMLCK key be on at boot?

Thank you my fine Ubuntu people.

-TIC-

---

### Post by ajgreeny on 2010-08-09
On my system the numlock is always on at boot time.  I think you must shutdown with that configuration for it to be so, but have never had a problem.  There is a package called **numlockx** available in the repos, but I though it was largely deprecated in gnome these days.  Worth trying?

As for the login screen, GDM was updated in 9.10 to the current style of setup, and is almost completely non user-configurable.  There are a few threads suggesting how to do things differently, but I've never bothered to look further about this.

---

### Post by earthpigg on 2010-08-09
you could always try [ubuntu tweak]("http://ubuntu-tweak.com/"), but it is not officially supported by ubuntu.

see attached image. i've never tried checking that box, but ubuntu tweak usually does what it says it will.

---

### Post by TuxIsCute on 2010-08-09
Hey,

Thanks for pointing me to Ubuntu Tweak!  It did exactly what I wanted it to and it looked good doing it!  Thanks again.

Now for the NUMLCK problem:  That application USED to work but doesn't anymore.  I don't even think it is in the repositories anymore.  And Ubuntu does not save my settings at all when I exit.  I always use NUMLCK but it never saves it.  It is annoying!

Thanks aain for Ubuntu Tweak!

---

### Post by ajgreeny on 2010-08-10
> **TuxIsCute said:**
> Hey,

Thanks for pointing me to Ubuntu Tweak!  It did exactly what I wanted it to and it looked good doing it!  Thanks again.

Now for the NUMLCK problem:  That application USED to work but doesn't anymore.  I don't even think it is in the repositories anymore.  And Ubuntu does not save my settings at all when I exit.  I always use NUMLCK but it never saves it.  It is annoying!

Thanks aain for Ubuntu Tweak!
It's definitely in the repos, but I did say it was now a deprecated package, for gnome at least, if not other DEs.

I don't know why your numlock will not work, unfortunately;  hardware problem?

---

