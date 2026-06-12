---
title: "Having Major Problems - Please Help"
date: 2006-05-07
forum: General Help
---

### Post by jeradzan12 on 2006-05-07
Hi.  I am relatively new to Linux and Ubuntu.  I love Ubuntu, but am having a few problems.  First - When I try to compile anything, I get an error stating the C compiler cannot create executables.  Like I said this happens regardless of what I am compiling.  Second, for some odd reason, I turned the pc on this morning and X will no longer start automatically.  I have to log in and get it going manually.  Third, my volume control no longer appears next to the clock.  Anytime I need to do anything there I have to go through the applications menu.  Detailed instructions would be appreciated, because as I said I am new to Linux and don't have the basics down just yet.  If there is anything else you need from me, please let me know.  I am typing this on my mac right now as I am working diligently trying to get everything to work on my Ubuntu, so I cannot provide the lspci right now if you need it.  I am using a Dell Latitude C600 with 256 MB RAM if that helps.

Thanks.

---

### Post by aysiu on 2006-05-07
[QUOTE=jeradzan12]Hi.  I am relatively new to Linux and Ubuntu.  I love Ubuntu, but am having a few problems.  First - When I try to compile anything, I get an error stating the C compiler cannot create executables.  Like I said this happens regardless of what I am compiling.[/quote] If you're new to Linux, I'm not sure why you're compiling software. Take a look at these two links for how to install software easily:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

> Second, for some odd reason, I turned the pc on this morning and X will no longer start automatically.  I have to log in and get it going manually.   Next time, instead of typing it in manually (I'm assuming you're doing so by typing *startx*), type this instead: ```
sudo /etc/init.d/gdm restart
``` > Third, my volume control no longer appears next to the clock. Right-click on the panel and select "Add to Panel." > If there is anything else you need from me, please let me know. Yes, are you using Dapper, by chance? I know you're posting in the Breezy (5.10) section, but you shouldn't be encountering all these problems with Breezy.

---

### Post by jeradzan12 on 2006-05-07
Thanks for the info.  By the way, I am using Breezy but just this evening have upgraded to dapper.

---

