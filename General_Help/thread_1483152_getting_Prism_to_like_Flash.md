---
title: "getting Prism to like Flash"
date: 2010-05-14
forum: General Help
---

### Post by HiImTye on 2010-05-14
here is how I got flash to work in prism. prism was working fine with flash in 9.10 but the 10.4 install caused it to stop working. after doing all of these ***with no success ***I decided to open up a terminal and see what the problem was.

here is what I did prior to finding the problem,

[LIST=1]
[*]purged and reinstalled flash
[*]cleared my [website storage]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html") cache from flash
[*]deleted all shortcuts to Prism
[*]deleted Prism settings (~/.prism) then purged and reinstalled Prism.
[/LIST]
finally, I decided to open up a terminal and see what was going on. I made a dummy Prism app on my desktop then copied and pasted the 'command' from the properties (right click > properties). I pasted that in a terminal
```
tye@T:~/Desktop$ "prism" -override "/home/tye/.webapps/dummy@prism.app /override.ini" -webapp dummy@prism.app
```it gave me the following output
```
Attempting to load the system libmoon 
Segmentation fault

```so, knowing that libmoon is part of moonlight I performed the following:
```
tye@T:~/Desktop$ aptitude search moonlight
```which provided me with this (omitting unimportant results)
```
i A moonlight-plugin-core                                                    - Free Software clone of Silverlight 2.0 - plugin core components                   
i   moonlight-plugin-mozilla                                                 - Free Software clone of Silverlight 2.0 - Xulrunner 1.9 plugin
```so, I removed the packages and any related packages, like so:
```
tye@T:~/Desktop$ sudo apt-get purge moonlight-plugin-core moonlight-plugin-mozilla && autoremove
```made a dummy prism app and viola! prism was working.

so there you have it, moonlight is currently breaking prism. for now uninstall it if you want flash apps to work in prism

hope this helped (and/or gave you some insight on how to help yourself with another problem you may be facing)

---

### Post by Foxcow on 2010-07-14
Awesome!

I istalled Prism on both my laptpp and desktop.  Both are running 10.04.  It didn't work on my desktop machine because it had the Moonlight plugins.  Now it appears to be working beautifully.

Thank you very much!

---

