---
title: "gedit + ftp plugin not working"
date: 2012-01-19
forum: General Help
---

### Post by EvilGenius187 on 2012-01-19
Good day to all, 

this is my first post and I've been searching on the net for 4 days now but nothing. 

I've just got a laptop, nothing special with okay specs. Now I want to use it just for fun and webdesign. 

My problem is, I have found a gedit FTP plugin that would do exactly what I want. [http://code.google.com/p/gedit-ftp-browser/]("http://code.google.com/p/gedit-ftp-browser/") But it will not work. When I try to enable it, I get an error. I've tried running gedit via the terminal and it is returning the following error: ***ImportError: No module named gedit***

I already contacted the creator of the plugin and he had no idea and told me to ask on the forums...

There is this other option, going to Places>Connect to server, but Lubuntu is missing this option.

That brings me to this last question; would it be a good idea to install Ubuntu? I installed Lubuntu because it's lightweight. 
Specs: [http://www.dell.com/us/dfb/p/latitude-d620/pd]("http://www.dell.com/us/dfb/p/latitude-d620/pd")

The FTP option is a MUST. I would love to work via FTP + editing files on the fly.

Thanks in advance,
Marvin

---

### Post by cogier on 2012-01-19
Have you looked at **Fire FTP** which is an add on for Firefox browser?

---

### Post by SteveDee on 2012-01-19
> **EvilGenius187 said:**
> ...When I try to enable it, I get an error. I've tried running gedit via the terminal and it is returning the following error: ***ImportError: No module named gedit***...

I've added the 2 files, and I can enable the Plugin without a problem. But I'm not sure how you use it, and I doubt it will work anyway as I suspect that there are dependencies that require more files:-
```

import gedit
import gtk
import gobject
from ftplib import FTP
import re
import sys
import os
import pango

```

You could open Synaptic Package Manager and try to install files with appropriate names. e.g. for ftplib try adding ftplib3.

Installing these files via Synaptic has the advantage that you can always use "History" as a reminder, should you wish to remove any of them.

But it might be quicker to go back to the author an ask what packages are required.

Installing Ubuntu probably won't solve your problem.

Lubuntu runs better on my Dell Latitude D600 than Ubuntu.

---

### Post by EvilGenius187 on 2012-01-20
> **cogier said:**
> Have you looked at **Fire FTP** which is an add on for Firefox browser?
Thanks appreciate it, using Chrome right now though, might check it out if I can't get it to work.

> **SteveDee said:**
> I've added the 2 files, and I can enable the Plugin without a problem...
And thank you too, appreciate it.

That's weird. Edit: Where did you put the files? Just in case...

Why does it work with yours? You probably installed the right packages over the time you've been working with Lubuntu I guess? I'll mail the creator again and will ask for the required packages.

Thanks again for the help, will be back for sure.

---

### Post by SteveDee on 2012-01-20
> **EvilGenius187 said:**
> ...That's weird. Edit: Where did you put the files? Just in case...

I put them in: /home/steve/.gnome2/gedit/plugins
...and when I go to: Gedit Preferences > Plugin I see the attached (screen shot).
But as I said before, I've no idea how to use it. If fact I don't know what an "FTP editor" is!

I don't know if you have researched this to determine its suitability for your web design activities, so I apologise in advance if the following is not appropriate.

FTP = file transfer protocol. Its a means of transferring files between servers (e.g LAN & internet servers).

FireFTP (as mentioned by cogier) allows you to publish (upload) and access/retrieve (download) files via FTP to/from a website.

Kompozer is an HTML editor which allows you to create and edit web pages. You can use this to edit HTML source or edit in a direct graphical view.

I would imaging that this gedit plugin allows text editing for files retrieved via FTP, but please put me right if it does something else.

---

### Post by EvilGenius187 on 2012-01-20
> **SteveDee said:**
> I put them in: /home/steve/.gnome2/gedit/plugins
...
The plugin would do exactly what I want. But I have found something else for Chrome (and would probably work for other browsers also) called ShiftEdit, it works like a charm.

I'd still want to get this to work though. And thanks for your help Steve!

**I have another question that's Lubuntu related, but I'd rather not start a new thread. I have my panel on the left and I would like to center the icons horizontal. And maybe vertical also, would be great!**

---

