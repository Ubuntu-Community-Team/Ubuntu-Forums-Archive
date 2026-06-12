---
title: "Syncing Folders between 2 Servers over Wan"
date: 2011-12-04
forum: General Help
---

### Post by djh82uk on 2011-12-04
Hi All

I have a file server at my house, I have built a 2nd server as a mirror which is going to be at my parents house.

I want to sync certain folders from my house to my parents house every night.

Their side is just sat behind a normal broadband router.  What is the quickest & safest way to do this?

Im thinking Rsync over SSH?  Then I only need to forward ssh to that machine.

Is this classed as secure or would I need some sort of vpn?

I have 10Mb upload, will Rsync max that out over SSH?

Thanks

DJH

---

### Post by papibe on 2011-12-04
I personally use rsync over ssh to share pictures, and family videos with my brother (who is out of the country). If you go this way, you'll need also:[LIST]
[*]Create a simple script that can take of the concern of a slow or inestable connection.
[*]Create ssh Public keys for security and easier automation of your script.
[*]Optional: the virtual session manager 'screen'. The easiest way to manage long time execution command line programs.
[/LIST]
Hope it helps,and tell us if you need more details.
Regards.

---

