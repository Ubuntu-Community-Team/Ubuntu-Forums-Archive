---
title: "gammu-smsd will not work!!! :*-("
date: 2010-04-07
forum: General Help
---

### Post by TechMansoor on 2010-04-07
I have tried installing gammu-smsd on both hardy and jaunty...:-( this is the error I'm getting...

> The following packages have unmet dependencies:
  gammu-smsd: Depends: libgsmsd7 but it is not going to be installed
              Depends: libpq5 (>= 8.4~0cvs20090328) but 8.3.9-0ubuntu9.04 is to be installed
E: Broken packages
radio@SMSgateway:~$ 


I have tried looking for both of these packages individually but to my suprise no luck!! And when I google such error messages, nothing comes up..

can any of you awesome dudes help me? I'm almost into tears..I just wish I knew what to do to begin troubleshooting and or my options at this point for making this work...:-(

some of my referenced articles:

[http://back2arie.wordpress.com/2009/08/]("http://back2arie.wordpress.com/2009/08/")

Thanks in advanced guys...

---

### Post by TechMansoor on 2010-04-08
Anyone?

---

### Post by back2arie on 2010-04-22
It's looks like dependencies problem, make sure your repository configuration in [FONT=monospace][/FONT]/etc/apt/sources.list is right.
for example, if you use jaunty it's should be something like this:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
and for the PPA:
> deb [http://ppa.launchpad.net/nijel/ppa/ubuntu](http://ppa.launchpad.net/nijel/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/nijel/ppa/ubuntu](http://ppa.launchpad.net/nijel/ppa/ubuntu) jaunty main 

---

