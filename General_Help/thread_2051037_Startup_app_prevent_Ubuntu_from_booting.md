---
title: "Startup app prevent Ubuntu from booting"
date: 2012-09-01
forum: General Help
---

### Post by Mich3lin on 2012-09-01
Hi, recently I added startup application, so it will run every time w/o running it manually. But somehow I must insert it incorrectly, because when I run Ubuntu, it lists applications which are now starting and stops on the last but one. So I realized that it's probably causing this problem and removed it via recovery (~/.config/autostart/). But even after remove, it still looks the same.
So, is there any other file or list of startup apps where it should be removed? 
Thanks

---

### Post by mcduck on 2012-09-01
What kind of startup application are you talking about, and how did you add it?

The Startup Applications you can configure in the settings only apply to *that user's desktop startup*, and have nothing to do with what happens during the boot process. So there's nothing you could add there that would prevent the system to booting correctly, even in the worst case you'd still get as far as the login screen and only get problems after the user in question tries to log in.

---

### Post by Mich3lin on 2012-09-01
I followed this guide: [http://ubuntu-tutorials.com/2006/12/02/imwheel-5-button-mouse-within-nautilus-ubuntu-610/](http://ubuntu-tutorials.com/2006/12/02/imwheel-5-button-mouse-within-nautilus-ubuntu-610/) but instead of adding it as script to startup, I add it as app. Wild idiot over here :)

//EDIT: Just a second, I'll upload a video for better understanding

So, here it is: [http://www.youtube.com/watch?v=QqIlKFOSfGw&hd=1](http://www.youtube.com/watch?v=QqIlKFOSfGw&hd=1)

---

### Post by mcduck on 2012-09-01
Like I said, the startup script can not prevent your system from booting, as it's not executed at that tij ebut a lot later instead.

I'd recommend first uninstalling the imwheel package and, if not done automatically, the /etc/X11/imwheel/imwheelrc file as well. That gide you've been following is for a seriously old Ubuntu version, I bet there must be some more up-to-date infomration how to configure the buttons...

---

### Post by Mich3lin on 2012-09-01
> **mcduck said:**
> Like I said, the startup script can not prevent your system from booting, as it's not executed at that tij ebut a lot later instead.

I'd recommend first uninstalling the imwheel package and, if not done automatically, the /etc/X11/imwheel/imwheelrc file as well. That gide you've been following is for a seriously old Ubuntu version, I bet there must be some more up-to-date infomration how to configure the buttons...

Yeah, when I think about it now, you're right... Startup is executed later.

Anyway, I removed imwheel, but still can't boot. Same error.

---

### Post by mcduck on 2012-09-01
Could you tell what the exact error is? That might be helpfull for figuring out what the problem is... ;)

edit: nevermind, you had already posted a video about the problem. Sadly there's no error messages on the video so it doesn't help much. Perhaps try looking through the log files in /var/log to see if any of the system logs has anya ctual eroor messages during the boot?

---

### Post by Mich3lin on 2012-09-01
> **mcduck said:**
> Could you tell what the exact error is? That might be helpfull for figuring out what the problem is... ;)

In a fact, there is no error, that's the problem, otherwise I won't bother you at forum and search Google instead. Watch this... [http://www.youtube.com/watch?v=QqIlKFOSfGw&hd=1](http://www.youtube.com/watch?v=QqIlKFOSfGw&hd=1) this is everything I know.

---

