---
title: "Widescreen Resolution on Dell Monitor"
date: 2010-11-01
forum: General Help
---

### Post by dlday988 on 2010-11-01
Hello,

I have jumped on the ubuntu ship and love it so far.  I would use it as my primary OS but for some reason when I go to system>preferences>monitors I am not able to choose any other resolution besides 4:3 aspect ratio when both my laptop and my monitor are widescreen.  At the moment everything is centered but everything is way too large and our of perspective.  I am on a wubi install within windows xp, running off a toshiba laptop and I am trying to get my monitor to look right.  I have looked around and haven't found a definitive answer.  The monitor is a dell 23" sp2309W.  I am on the newest ubuntu 10 in that i just installed yesterday.  Any help would be great.  And again I am new to linux terminal so a quick walkthrough if necessary would be greatly appreciated.  

Thanks.

---

### Post by papibe on 2010-11-02
Having struggled with monitor resolutions on a toshiba laptop myself, I know how frustrating can be.

There's a log that is generated when you log into your user in graphic mode. It is called /var/log/Xorg.0.log

Post it here so we can take a look. Reset your machine, log into your account and copy/paste the file.

Regards.

EDIT: You can also use [http://pastebin.com/]("http://pastebin.com/") to paste the file

---

### Post by dlday988 on 2010-11-02
Thanks for the response.  I was actually able to figure out the 4:3 aspect ratio problem by just turning off my laptop monitor and then only running off of my external monitor.  

Now my monitor is at 1360x768 16:9 which is the highest resolution option I have.  It fits the monitor alright but in windows I run at 1600X1200 which looks much better.  

Anyway to add 1600x1200 resolution to the options?

Thanks for any help.

---

