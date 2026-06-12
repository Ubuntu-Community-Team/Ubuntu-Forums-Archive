---
title: "SSH Port Forwarding that won't quit!"
date: 2009-10-01
forum: General Help
---

### Post by neeko321 on 2009-10-01
Hi All,

I was recently playing with port forwarding via ssh from a remote location to my home server. During the session I set up a wordpress blog and performed some other menial tasks. Now that I'm home I am trying to access the site by navigating to 'localhost' but I am immediately redirected to the port I was previously forwarding to. Unfortunately there is nothing at that location. I have tried:
specifying port 80 specifically, killing all instances of ssh, shutting down the ssh server, rebooting and determining that there are no proxies enabled in Apache.

The only clue that I have here is that when I was setting up the port forwarding I left out some arguments, so it looked like this:

ssh -L 15560:localhost:80 user@domain

This logs me into the server. The command should have looked like this:

ssh -L 15560:localhost:80 -fN user@domain

I suspect this may have established some kind of permanent remapping but I'm not 100% on that. Any help would be appreciated.

Thanks!

---

### Post by neeko321 on 2009-10-01
Just a note that this Ubuntu 9.04 Server

---

### Post by Giblet5 on 2009-10-01
Only a web page can "redirect" you to another port...

It's the web page itself that's doing this.

Edit it. Fix that. Save it. Try loading it.

---

### Post by neeko321 on 2009-10-01
Thanks, Giblet. You are right. I didn't quite understand how ssh would still be redirecting or would have written some kind of file that would redirect. I think Wordpress might write your the port into some kind of file when performing the config. I moved the WP install and it comes up fine.

Cheers!

---

