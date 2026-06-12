---
title: "repos for more current apps?"
date: 2009-10-16
forum: General Help
---

### Post by schwim on 2009-10-16
Hi there everyone,

Looking at my new Ubu install after all updates, I'm noticing 3.0 Firefox, 2.5.x Pidgin, old gimp, etc.  I was wondering if there's a repo I can enable to get a little bit more cutting edge apps?  I'm not looking for first off the assembly line, but I would like 3.5 for firefox, Pidgin with the Yahoo updates, etc.

I tried enabling preproduction and source in the update window, but after refreshing the lists, there were still no updates for these apps.

thanks,
json

---

### Post by amingv on 2009-10-16
> **schwim said:**
> Hi there everyone,

Looking at my new Ubu install after all updates, I'm noticing 3.0 Firefox, 2.5.x Pidgin, old gimp, etc.  I was wondering if there's a repo I can enable to get a little bit more cutting edge apps?  I'm not looking for first off the assembly line, but I would like 3.5 for firefox, Pidgin with the Yahoo updates, etc.

I tried enabling preproduction and source in the update window, but after refreshing the lists, there were still no updates for these apps.

thanks,
json

Most of the latest updates don't make it to the repos until a while. AFAIK your best bet would be to see if the project has a repo or downloading the latest version from their website.

---

### Post by sirtrent on 2009-10-16
You could also look through PPAs (Personal Package Archives). I've been doing that lately; running Intrepid because of intel video regression in Jaunty, but I've been rocking the PPA repos to get updated Rhythmbox, Firefox, Pidgin, Deluge etc...

I often have success simply googling <AppName ppa> or <AppName ppa ubuntu>.

or just go to the main ppa site and search:

[URL="https://launchpad.net/ubuntu/+ppas"]
https://launchpad.net/ubuntu/+ppas[/URL]


Be aware though that these are largely user created and are unsupported.

---

### Post by hal10000 on 2009-10-16
Try the ubuntu sources.list generator at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by vinutux on 2009-10-16
Just Search google like this Appname+ppa

---

### Post by Bonster on 2009-10-16
I believe UbuntuTweaks has loaded some of the up-to-date PPA within it. Maybe check that out

---

### Post by schwim on 2009-10-16
Thank you all for your posts.  I found [this thread](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html) via my firefox 3.5+ppa search and followed it.  As far as I can tell, it installed correctly(I now have a firefox-3.5.3 directory under /usr/lib).  The system of course still utilizes the 3.0.14 install for the menu shortcuts, preferred app, etc.

Is there a single location where I can change which install ubu uses?

thanks,
json

---

### Post by vinutux on 2009-10-16
System>preferences>prefrred applications and change browser settings

---

### Post by vinutux on 2009-10-16
Check this post worked for me........

[http://ubuntuforums.org/showthread.php?t=1225754]("http://ubuntuforums.org/showthread.php?t=1225754")

---

### Post by hal10000 on 2009-10-16
> System>preferences>prefrred applications and change browser settings

Yes, do this and
```
sudo update-alternatives --config x-www-browser
```
and type in the number shown for firefox-3.5

---

### Post by schwim on 2009-10-16
Thank you all very much!  Posting from 3.5.3 :)

thanks,
json

---

