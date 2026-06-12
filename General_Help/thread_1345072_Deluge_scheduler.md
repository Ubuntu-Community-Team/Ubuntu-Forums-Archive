---
title: "Deluge scheduler"
date: 2009-12-03
forum: General Help
---

### Post by mpatrick on 2009-12-03
Hi,

I am a Newbie to Linux (windows poweruser for many many years)

Just started using Deluge for torrents, which is great, after being used to Utorrent in windows.

However one thing I would like to get working is a scheduler to automatically stop any downloads at 6pm and restart at 11pm (peak times for my ISP)
So I found the following link and followed that
[http://dev.deluge-torrent.org/wiki/UserGuide/Scheduling](http://dev.deluge-torrent.org/wiki/UserGuide/Scheduling)

I followed the article to the letter using Gnome Schedule 2.1.0, ie 

Disable all downloads
deluge -u console -a "config --set max_active_limit 0"
Enable again
deluge -u console -a "config --set max_active_limit 100"

However from testing this nothing happened, the downloads continued and never stopped or started no matter which times I tested (tried it a few times)
I even tried it with the suppress output as in the article and default behaviour,  but still nothing worked.

So does anyone have any ideas as to what I am doing wrong, or maybe another way of doing this? Shame they do not offer a plugin in Deluge to do this.

So at the moment I am using Ktorrent, which has a scheduler plugin that works and does the job I want. However I do not like the look of Ktorrent compared to Deluge and does not seem to offer as many seeds as Deluge for same torrent. Also a lot of people comment that Ktorrent sometimes freezes there machines although I have not experienced that.

I wonder if it is anything to do with the latest version of Deluge I am using 1.1.9 as the article states for Deluge 1.1 only?

I am using Ubuntu Karmic Koala 9.10

Any help would be most appreciated

Regards

Michael

---

### Post by actinium on 2009-12-09
try to run deluge -u console and see if you can do the commands? with 1.1.9 it did work, but it doesn't work for me using 1.2rc4. If you are running the daemon / client mode you would need to connect to the right daemon too.

---

### Post by Cas07 on 2009-12-10
Im running 1.2rc4 and under Preferences|Plugins there is a Scheduler that can be enabled, not sure if its in 1.1.9, but is different to what you referenced and looks a lot simpler to setup.

---

### Post by Tybion on 2010-06-18
To clarify -

Choose **Edit / Preferences** in the Deluge GUI.

Choose to Install the **Scheduler** plugin .. but then you are presented with a file browser .. for Lucid, the location is ..
 **/usr/share/pyshared/deluge/plugins**

$ ls /usr/share/pyshared/deluge/plugins
Blocklist-1.2-py2.6.egg
init.py
Scheduler-0.1-py2.6.egg
Execute-1.2-py2.6.egg
Label-0.1-py2.6.egg
WebUi-0.1-py2.6.egg
Extractor-0.1-py2.6.egg
pluginbase.py

(If this location changes in future '**locate .egg**' in a terminal should give you the answer.)

---

