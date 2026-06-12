---
title: "how can i install opera latest from the repos or what options do I have"
date: 2010-05-24
forum: General Help
---

### Post by nmvictor on 2010-05-24
I am running Lucid in my Apple iBook of course powerpc architecture and due to firefox's cruel treat on my CPU, I want to install opera which I am told is a bit lightweiht and friendly on CPU.I tried sudo "apt-get install opera" and I got "the package opera does not have an installation candidate .... and so forth....", I visited the opera for powerpc download page and I couldn't see Ubuntu among the listed OS'ses. I am not sure what to do? Is their an option coz I love firefox but my iBook wont stand it without the 100% CPU usage. Someone please help.

---

### Post by elmosim2 on 2010-05-24
.

---

### Post by Zemblan on 2010-05-24
[http://ubuntu-tutorials.com/2010/01/22/install-opera-10-web-browser-in-ubuntu/](http://ubuntu-tutorials.com/2010/01/22/install-opera-10-web-browser-in-ubuntu/)

---

### Post by Chesamo on 2010-05-24
Use this **IF AND ONLY IF** the link posted by Zemblan does not work.

You can get the .deb file from here:

[http://www.opera.com/browser/download/?os=linux-ppc&ver=10.53b1](http://www.opera.com/browser/download/?os=linux-ppc&ver=10.53b1)

After installing the .deb, run ```
sudo apt-get -f install
```

---

### Post by nmvictor on 2010-05-24
> **Zemblan said:**
> [http://ubuntu-tutorials.com/2010/01/22/install-opera-10-web-browser-in-ubuntu/](http://ubuntu-tutorials.com/2010/01/22/install-opera-10-web-browser-in-ubuntu/)

Thanks, that worked perfectly.And now my system doesnt lag like it used to with firefox, CPU usage is hardly above 30%, firefox is great and it has a reputation but on this system, Im gonna go with opera.SHAME ON YOU FIREFOX.
Thanks everyone else

---

