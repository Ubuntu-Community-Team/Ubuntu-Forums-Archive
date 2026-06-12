---
title: "can't install avast; tried indications from forum"
date: 2009-06-30
forum: General Help
---

### Post by jadu on 2009-06-30
hello,

I want to install Avast. for windows viruses that I might send to friends, and because I'm going to try to set up a network with a windows machine.
I downloaded the deb version from here:
[http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html)
because I saw on a post that it was the recomended version.

Apparently I have a 64 bit set-up on my computer. When I try to install, it tells me "wrong architecture" i386. And the details says install-size is not available KB.
I tried in a terminal something I saw in a post:
dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb
But it says 

"the requested operation requires superuser privileges" (I'm translating from spanish, but more or less that)

I also tried this similar command from another post (I don't know the difference)
sudo dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb

but it says:
dpkg: the area of the database is blocked by another process.


so I tried to install the rpm version from the same site. But it opens file manager and says "type of file not suported"

Then I tried the tar gz version. Now it opens for me a window that says "avast4workstation 1.3.0.tar.gz. When I right click, it gives me an option to open or extract. I don't know which I need to do. If I navigate in the extract option, and go to where it's saved in the tmp folder, it the rpm and tar gz versions show up, but they're light colored, they can't be highlighted. I don't know what to open if that's what I need to do.

Avast doesn't show up in "add or remove programs".


I'm also a bit confused because I tried to get rid of one version of avast before installing another, but it wouldn't let me. It says 
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


you'll notice, I don't know what any of these messages mean, or the difference between the different kinds of files. 

Any idea how to get this working?

thanks

---

### Post by jadu on 2009-07-02
hi I'd like to bump this up, maybe someone has some advice?
I did try looking in the forums but I really couldn't find anything that explained this.
thanks in advance

---

