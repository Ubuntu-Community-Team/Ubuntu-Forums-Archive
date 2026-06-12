---
title: "mpd start up at boot help!"
date: 2010-06-02
forum: General Help
---

### Post by avatardvr@gmail.com on 2010-06-02
Arg.  looking for help with mpd.  running ubuntu 9.04 and have mpd installed and running good.  I just cant seem to get it to start at boot.  i want it to run on a headless system so dont want to have to login to start it.  i have successfully done this on another system but i cannot remember how i did it and cant seem to find any help in google or searching here.  any advice will be really appreciated.

---

### Post by Brandon Williams on 2010-06-02
Did you set START_MPD=true in /etc/default/mpd? If so, then the system is probably attempting to start mpd at boot and failing. Are there any useful log messages in /var/log/mpd/mpd.log?

---

### Post by avatardvr@gmail.com on 2010-06-02
nothing in the log, just avahi: service music player successfully established.  and of course the database info.  is there somewhere i can put the /etc/init.d/mpd start so that it starts at boot.  if i have to have it auto logon i will, dont want to...  I appreciate the help.

---

### Post by Brandon Williams on 2010-06-05
You skipped over my first question ... does /etc/default/mpd contains 'START_MPD=true'?

---

### Post by avatardvr@gmail.com on 2010-06-05
sorry, my bad.  yes it does.

---

### Post by avatardvr@gmail.com on 2010-06-07
so, any more advice on this?  could really use the help.

---

### Post by avatardvr@gmail.com on 2010-06-10
nothing?

---

### Post by avatardvr@gmail.com on 2010-06-26
well, didnt get any real help with this, solved it myself by wiping and installing 10.04.  works fine now.

---

