---
title: "Nothing remembered"
date: 2009-12-17
forum: General Help
---

### Post by Fitch on 2009-12-17
I've installed Jaunty, had it for a few weeks now, and things seem to get worse every day.

Mozilla Firefox can't even remember the start page, nor where I want the downloads to go. 
It just defaults to [http://start/ubuntu.com](http://start/ubuntu.com), every time I start it.  For the month or two I've had Linux, I used to have it default to the router "http://192.168.1.1".  Won't do that now...

---

### Post by aysiu on 2009-12-18
Assuming your username on Ubuntu is *fitch*, can you close Firefox, and then paste the following command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo chown -R *fitch:fitch* /home/*fitch*/.mozilla
``` and then start  Firefox again and see if you can get it to remember your new home page?

---

### Post by Fitch on 2009-12-18
Thanks for that! :P

Never did quite get the hang of "sudo chown" thingy, but, fingers crossed, that seems to have cured it.

Just wonder why it decided to go funny in the first place... 

Cheers!

---

### Post by aysiu on 2009-12-18
> **Fitch said:**
> 
Just wonder why it decided to go funny in the first place...  Could be this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Fitch on 2009-12-18
Aha! Methinks you've been eating too many beans! Open the window!.:lolflag:

Thanks for that.  I shall try to "remember" the correct way in future...

---

