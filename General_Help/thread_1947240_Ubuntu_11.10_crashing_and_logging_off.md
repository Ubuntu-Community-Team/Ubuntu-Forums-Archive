---
title: "Ubuntu 11.10 crashing and logging off"
date: 2012-03-26
forum: General Help
---

### Post by s3pultur4 on 2012-03-26
Hello guys. I'm using Ubuntu 11.10, and there is something happening that is bogging me. From times to times, suddenly my Ubuntu crashes (closes everything), prints a message in the console, and goes to the user screen. In the syslog, there is the following message:


Mar 26 08:10:20 jhonatan-Vostro-3550 gnome-session[3847]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Recurso temporariamente indisponível) on X server :0.#012
Mar 26 08:10:21 jhonatan-Vostro-3550 acpid: client 3733[0:0] has disconnected
Mar 26 08:10:21 jhonatan-Vostro-3550 acpid: client connected from 4902[0:0]
Mar 26 08:10:21 jhonatan-Vostro-3550 acpid: 1 client rule loaded
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Successfully made thread 4981 of process 4981 (n/a) owned by '104' high priority at nice level -11.
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Supervising 1 threads of 1 processes of 1 users.
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Successfully made thread 4988 of process 4981 (n/a) owned by '104' RT at priority 5.
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Supervising 2 threads of 1 processes of 1 users.
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Successfully made thread 4989 of process 4981 (n/a) owned by '104' RT at priority 5.
Mar 26 11:10:22 jhonatan-Vostro-3550 rtkit-daemon[1652]: Supervising 3 threads of 1 processes of 1 users.

I'm using a Dell Vostro 3550. If anybody could give me a light I would appreciate. Thanks.

---

### Post by jyr0s on 2012-04-01
*bump* 
just chiming in to say I've been experiencing the same symptom.

Here's my /var/log/syslog.  Of particular interest is the line that reads: Gdk-WARNING: gnome-session: Fatal IO error 11.  The acpid and rtkit-daemon seem to be consequential to the fatal IO error:
```

Apr  1 13:57:48  avahi-daemon[1162]: last message repeated 2 times
Apr  1 13:57:48 jupiter laptop-mode: Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-17-generic')
Apr  1 13:57:48 jupiter laptop-mode: Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-17-generic')
Apr  1 13:58:13 jupiter gnome-session[2100]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Apr  1 13:58:13 jupiter acpid: client 1339[0:0] has disconnected
Apr  1 13:58:13 jupiter acpid: client connected from 3065[0:0]
Apr  1 13:58:13 jupiter acpid: 1 client rule loaded
Apr  1 18:58:14 jupiter rtkit-daemon[1893]: Successfully made thread 3153 of process 3153 (n/a) owned by '104' high priority at nice level -11.
Apr  1 18:58:14 jupiter rtkit-daemon[1893]: Supervising 1 threads of 1 processes of 1 users.
Apr  1 18:58:15 jupiter rtkit-daemon[1893]: Successfully made thread 3156 of process 3153 (n/a) owned by '104' RT at priority 5.
Apr  1 18:58:15 jupiter rtkit-daemon[1893]: Supervising 2 threads of 1 processes of 1 users.
Apr  1 18:58:15 jupiter rtkit-daemon[1893]: Successfully made thread 3157 of process 3153 (n/a) owned by '104' RT at priority 5.
Apr  1 18:58:15 jupiter rtkit-daemon[1893]: Supervising 3 threads of 1 processes of 1 users.

```

Any ideas?

---

### Post by ehime on 2012-04-23
Bump, same sauce here. Very annoying as its my workbox

```

Apr 23 13:48:43 ehimeprefecture gnome-session[11869]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Apr 23 13:48:43 ehimeprefecture acpid: client 10683[0:0] has disconnected
Apr 23 13:48:43 ehimeprefecture acpid: client connected from 12895[0:0]
Apr 23 13:48:43 ehimeprefecture acpid: 1 client rule loaded
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Successfully made thread 12982 of process 12982 (n/a) owned by '104' high priority at nice level -11.
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Supervising 1 threads of 1 processes of 1 users.
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Successfully made thread 12985 of process 12982 (n/a) owned by '104' RT at priority 5.
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Supervising 2 threads of 1 processes of 1 users.
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Successfully made thread 12986 of process 12982 (n/a) owned by '104' RT at priority 5.
Apr 23 20:48:45 ehimeprefecture rtkit-daemon[1575]: Supervising 3 threads of 1 processes of 1 users.


```

---

