---
title: "Crazy high load"
date: 2011-11-01
forum: General Help
---

### Post by wutz on 2011-11-01
I'm running a website on an Ubuntu server.  It's running on apache2.  When everything is going smoothly, the load will stay around 10 or so, but every so often, it starts to climb, and reaches the hundreds.  It stays there indefinitely and the system becomes unusable until I stop apache.  I don't know if there's some problem with my configuration or what.  Normally when I look at "top" I don't see anything suspicious (to my untrained eye) aside from the extremely high load average.  But this time, something weird showed up.  The CPU usage was up to 67.6%us and 31.9%wa, and the process at the top of the list "java" was apparently using 1102% CPU.  I've included a screencap below.  I've never noticed this before, but is it possible that this java process wasn't showing up for some reason but was still causing the problem, or does top just occasionally spout out crazy 1102% CPU usages for fractions of seconds and I just happened to screen cap when it showed up?

[IMG]http://i.imgur.com/aOKDd.png[/IMG]

I'm pretty positive that the problem is related to apache 2, since all I need to do to get the server to calm down is to stop apache for a few minutes and then restart it.  Does anybody have any ideas as to what the exact cause is?  This has been a huge pain for me for a long time

---

### Post by enkay009 on 2011-11-01
There are some pretty nice options in top that can help you trace this issue.

You trace the process back to it's parent. You'll need to add the column first. You can do this with **'f'** and with **'o'** you can rearrange the order of the fields. The field is called PPID (as in parent process id).

You can also look at the full process path. You may be able to intuitively guess what this process is by seeing this. In top you can do this by typing **'c**'. But top tends to truncate the command. And for java processes commands tend be long. 

You can alternatively use ps and grep with the process id after you determine it with top. For example you could've typed this...

```
ps -Af | grep 16645
```Good luck figuring it out! If killing apache is releasing resources you're right in guessing that it's related to your web server. Now whether that problem is the web server configuration or your web application is another story. But these kind of problems tend to be the web app and not the web server.

---

