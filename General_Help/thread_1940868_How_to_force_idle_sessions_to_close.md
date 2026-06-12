---
title: "How to force idle sessions to close?"
date: 2012-03-14
forum: General Help
---

### Post by lisanels47 on 2012-03-14
I have users that use the "switch user" function all the time, and on the really low-end computers, this causes resource issues.

I'd like a script or something that would detect when a user is idle for 15 min and then force close their session.

Idea's?

---

### Post by lechien73 on 2012-03-14
You could try using **timeoutd**. From the manpage:

> timeoutd enforces the time restrictions specified for each or all users.
 .
 timeoutd scans /var/run/utmp every minute and checks /etc/timeouts for
 an entry which matches a restricted user, based on:
 .
  - The current day and time
  - The tty that the user is currently logged in on
  - The user's login ID
  - Any primary or secondary groups the user is in
 timeoutd can restrict local users, X11-users and users via telnet/SSH
 for a maximum of their session, max. day, idle or no login at all.

I see this package available for Maverick (10.10) with X support, but not since, so you may have to compile from source. I have seen this running to enforce 15min timeouts.

---

### Post by Space_Balls on 2012-03-30
I'm also looking for a solution to this problem. I will see, if I can find something, otherwise I will script my own solution. ConsoleKit might be useful for this.

---

### Post by lisanels47 on 2012-05-20
Still got no solution for this.  How does the screensaver detect idle sessions?  I could use that method maybe....

---

