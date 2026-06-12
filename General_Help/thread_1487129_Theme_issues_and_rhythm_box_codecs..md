---
title: "Theme issues and rhythm box codecs."
date: 2010-05-18
forum: General Help
---

### Post by ChazZeromus on 2010-05-18
Well for one I'd like to say that my theme issues (synonymous to [this]("http://ubuntuforums.org/showthread.php?t=844888&highlight=can%27t+change+theme")) may be caused by my impatience to go and get help from the internet, and that I may have downloaded many unneeded version of apache.

My theme went foobar after I mindlessly installed different variations of apache from synaptic, hoping that all would solve my issue of getting it to work. But now I use xampp for a little bit.

When I installed xammp I noticed my three essential daemons weren't starting, and I knew that due to the other versions I installed through synaptic. As expected, I uninstalled the other versions and xammp started working.

I'm not completely sure of it, but issues start to arise one after another if I inadvertently install unneeded parts of a program when I go trigger happy on synaptic. So I was wondering, a perfect solution to this would be to list every program I recently installed in descending order. Now I have no clue how to do this, and I'm not even sure it should be done in synaptic at all. **So how can I list all my recent installations in order?**

This one maybe common, but I'm a very affluent listener of music and I currently hold about 26K tracks on around 150GiB. on Windows my primary music player was Winamp. Winamp supports a plethora of audio formats, and I'm grateful for using it on my heterogeneous collection. I receive errors intermittently while adding tracks to rhythmbox, saying it needs a Windows Audio codec. I've researched this all the time and found the same solution, install a gstreamer codec. I've went to synaptic and found all appropriate instances of gstreamer and installed all of them ,and yet rhythmbox refuses to play WMA type formats. **What codec or package do I need to play WMA files?**

Thanks for taking the time to read my thread :)

---

### Post by mac9416 on 2010-05-18
Hi, ChazZeromus,

> **ChazZeromus said:**
> **So how can I list all my recent installations in order?**

You might try looking at /var/log/dpkg.log.


> **ChazZeromus said:**
> **What codec or package do I need to play WMA files?**

I believe it is ubuntu-restricted-extras.

I hope that helps some.  :)

---

### Post by gordintoronto on 2010-05-18
Why did you install Apache? You want to operate a web server?

Don't get programs from the Internet, just get them from Synaptic -- unless you really know what you are doing.

Audacious is a lot like classic Winamp.

To get a list of packages recently installed on your system, you can open Accessories/Terminal and enter this command:
cat /var/log/dpkg.log | grep "\ install\ "

See this web page for a way to see your entire history:
[http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html](http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html)

---

### Post by ChazZeromus on 2010-05-19
Thanks guys. I figured I actually had some songs that are encrypted or some other unsupported variation of WMA. That's why I couldn't play some files even though I practically installed all the ubuntu variations of ubuntu-restricted-extras. I think I have to convert them myself on windows.

**My themes went back to normal!** I removed everything mysql and httpd related, including all extra common libraries for them. On next reboot, the themes all went back to their smooth and natural menus and etc. The packages did help a bit, but all it took was for me to realize the name of which all problematic packages were, then after that I sat down with synaptic and removed all my unnecessaries.

I'm working with a web server bundle so I can better manage my configuration files and learn from there. After that I can finally setup normal webserver packages.

---

