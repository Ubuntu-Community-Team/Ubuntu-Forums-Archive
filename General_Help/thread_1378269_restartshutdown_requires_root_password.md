---
title: "restart/shutdown requires root password"
date: 2010-01-11
forum: General Help
---

### Post by RonPDX on 2010-01-11
Hello everyone-

I have been having a small problem since I upgraded from Jaunty to Karmic, whenever I shutdown or restart, root password is required due to multiple users being logged-in.

I have run ck-list-sessions, however I can not trace where (or what) session 5 is. 

```

Session3:
	unix-user = '1000'
	realname = 'Ron ******'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-01-11T13:14:33.053161Z'
	login-session-id = ''
Session5:
	unix-user = '114'
	realname = '(null)'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/???'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-01-11T13:44:24.901877Z'
	login-session-id = ''

```

Since I have MythTV installed and there was a similar bug, I tried the following solution without any success: [http://ubuntuforums.org/showthread.php?t=1299948](http://ubuntuforums.org/showthread.php?t=1299948).

Does anyone have any idea where I should next?

Thanks, 

Ron

---

### Post by zvacet on 2010-01-11
> root password is required due to multiple users being logged-in.

No,I don´t think it is bug.It is new option preventing you for shutdown by mistake.If you have multiple users running then you will be asked for password.

---

### Post by RonPDX on 2010-01-11
I with it were that simple. I am the only one logged-in and I don't have any other user accounts setup. 

> **zvacet said:**
> No,I don´t think it is bug.It is new option preventing you for shutdown by mistake.If you have multiple users running then you will be asked for password.

---

