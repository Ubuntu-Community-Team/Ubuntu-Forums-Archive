---
title: "multi-user, network manager applet icon not showing"
date: 2010-05-11
forum: General Help
---

### Post by NathanScrivener on 2010-05-11
My family uses a computer running Ubuntu 10.04. We each have a separate login. This computer connects to the internet via wifi.

A behaviour which I have noticed is as follows - the first user to log in gets the network manager applet icon. So they can control the network connection. Any other user that subsequently logs in does not.

Now this is a real pain in the butt as sometimes our wifi connection drops and I might have left my wife logged in and used the 'switch user' function to get access to my login. The only way I can access the applet is by switching back to her login.

Is there any way to make this appear in everyone's login's at the same time?

---

### Post by dcstar on 2010-05-11
> **NathanScrivener said:**
> My family uses a computer running Ubuntu 10.04. We each have a separate login. This computer connects to the internet via wifi.

A behaviour which I have noticed is as follows - the first user to log in gets the network manager applet icon. So they can control the network connection. Any other user that subsequently logs in does not.

Now this is a real pain in the butt as sometimes our wifi connection drops and I might have left my wife logged in and used the 'switch user' function to get access to my login. The only way I can access the applet is by switching back to her login.

Is there any way to make this appear in everyone's login's at the same time?

Doubtful, networking is something that should only be controlled in one place, having multiple users simultaneously able to change things just doesn't make sense if you want a stable system.

---

### Post by MarceloPatropi on 2010-05-17
I have exactly the same problem.

Me, my wife and daughter share the computer.

We connect via wifi. So if the connection drops, it's a pain to get it up again.

Would WICD ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) be a solution?

---

### Post by BslBryan on 2010-05-17
I would suggest trying to run the command
```
nm-applet
```
from a terminal.

---

### Post by elizabeth_b on 2010-08-06
I was being irritated by this too.

[NathanScrivener]("http://ubuntuforums.org/member.php?u=409548"), in case it wasn't clear, you want to run "sudo killall nm-applet" in a terminal, followed by "nm-applet".  That brings up the applet in your own session.  (It kills it in your wife's session, but the status was that it was dead there anyway).

Thanks

---

### Post by HK1 on 2010-11-02
patience, this bug is only 2 years old.
see [#284596]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596")

---

### Post by NathanScrivener on 2010-11-02
> Doubtful, networking is something that should only be controlled in one place, having multiple users simultaneously able to change things just doesn't make sense if you want a stable system.

And it seems that there are those that would argue against having this functionality.

Even though it hampers usability.

And btw I'm sure a multi-user NM-Applet could be devised for desktop users, without stability issues. It might not be appropriate for server environments where you have multiple users using the system simultaneously. Desktop users might have more than one user logged in at the same time, but they are not both using it at the same time.

THIS FEATURE IS NEEDED

---

### Post by Rhemat on 2011-09-25
I have been looking for a solution to this since my fiance's laptop broke.  She is not familiar with Linux, so I remain logged in to keep my laptop connected to our network.  However, when it times out, she won't have access to the applet to reconnect.

It would really be appreciated if such functionality could be added.

---

