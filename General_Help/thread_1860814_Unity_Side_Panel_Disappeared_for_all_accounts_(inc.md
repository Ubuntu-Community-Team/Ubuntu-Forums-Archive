---
title: "Unity Side Panel Disappeared for all accounts (including Guest) in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Angus77 on 2011-10-15
I only installed 11.10 on my desktop yesterday, so I've been doing a lot of dickering around (installing software, getting my family's multilingual accounts set up), so I'm not sure what Imight have done to trigger this.

The side panel in Unity has disappeared.  This happens in all accounts, including Guest.  All I get is a menu bar at the top (File Edit View Go Bookmarks Help).

I'm not familiar with Unity at all.  I haven't upgraded the family desktop since 10.04 (I use Debian on my laptop at work).  I haven't played around with any config files yet.

Can anyone help?

---

### Post by Angus77 on 2011-10-15
Turns it it was related to the fglrx driver, which I had installed and then removed.  I followed the instructions on another post on how to reconfigure the xserver to make sure it was using the open drivers (apparently it was still trying to load the uninstalled fglrx driver), and now everything works.

---

### Post by dauren on 2011-10-15
I've the same issue. How did you manage to solve it? I didn't install fglrx driver.
I'm new to ubuntu and would appreciate if you describe your solution in a simple way. 
Thanks.

---

### Post by Angus77 on 2011-10-15
If you've never installed the fglrx driver, then my solution won't help you.  My problem was that, after uninstalling the fglrx driver, the system was still trying to load the now-nonexistent driver.  I had to reconfigure the system to stop doing that.

---

