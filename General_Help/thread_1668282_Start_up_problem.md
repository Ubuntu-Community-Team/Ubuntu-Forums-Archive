---
title: "Start up problem"
date: 2011-01-16
forum: General Help
---

### Post by Alver on 2011-01-16
Hi all learned forum members,

 I have a fully functional dual boot W7/U 10.04.1 since several months and without issues. This morning however I had the following fault message during start up (after the appearance of the Ubuntu logo) on a black screen in a white box: "**Could  not update ICEauthority   file /home/user/.ICEauthority**". When I confirmed the OK (using the Enter key because my mouse was not funtioning) the start up routine finalized normally and I had a normal Ubuntu session without further issues. I looked for the mysterious .ICEauthoriy file but could not find it, as expected. What went wrong and how can I remedy this??

Thx for a possible answer.

Alver

Toshiba L-505 10M dual boot W7/U 10.04

---

### Post by wojox on 2011-01-16
Open a terminal:

```
sudo chown -R user:user /home/user/.*
```

Restart.

---

### Post by Alver on 2011-01-16
> **wojox said:**
> Open a terminal:

```
sudo chown -R user:user /home/user/.*
```

Restart.
Thank you, problem solved. But ... what causes such a problem?

---

### Post by johnaaronrose on 2011-01-28
I am now getting 'Problem with configuration server /usr/lib/libgconf2-4/gconf-sanity-check exit with status 256'. I've tried logging in with Session of Failsafe gnome -  sometimes it's OK & sometimes it isn't.

PS Perhaps I should have used sudo chown /user:user /home/user/.ICEauthority rather than sudo chown user:user /home/user/.*

---

### Post by johnaaronrose on 2011-01-30
Login is now working fine. I found a message (I've forgotten where) about 'deleting' .ICEauthority. The suggested method is:
mv /home/user/.ICEauthority /home/user/.ICEauthority.bak 
(where user is your login id).

This has the advantage that the .ICEauthority file can be restored by
mv /home/user/.ICEauthority.bak /home/user/.ICEauthority 
even if the above method doesn't work.

Since both my login users only gave a 'blank' desktop (i.e. no menus or quick launch icons) when I attempted the standard login, I logged into the user with administrative privileges by changing the Session (at the bottom of the screen) to root login (i.e. not one of the Gnome ones) after selecting/keying in the login id but before keying in the password.

After login I discovered that a much smaller .ICEauthority file had been created (1kb versus 60+) for that user. I opened a Terminal & repeated the command for my other user but with sudo before mv. I then restarted and was able to login for my first Administrative user, logout & login successfully for my second Desktop user.

---

