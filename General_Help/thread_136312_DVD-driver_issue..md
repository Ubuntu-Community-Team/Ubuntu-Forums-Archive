---
title: "DVD-driver issue."
date: 2006-02-25
forum: General Help
---

### Post by HarryW on 2006-02-25
Hi!
I recently installed kubuntu 5.10 on my laptop, however, a problem have ocurred. My DVD-driver can't read any kind of DVD-discs. Am i supposed to change something in settings? If anyone what is wrong, than please respond to this question. Thanks in advance.

---

### Post by vayu on 2006-02-25
[QUOTE=HarryW]Hi!
I recently installed kubuntu 5.10 on my laptop, however, a problem have ocurred. My DVD-driver can't read any kind of DVD-discs. Am i supposed to change something in settings? If anyone what is wrong, than please respond to this question. Thanks in advance.[/QUOTE]

What are you trying to open them with (konqueror, xine, kaffeine,...) and what type of media are we talking about, computer data, videos,...?

For instance I use xine to play dvd movies and I have to go into the setup window and select the gui tab, then change configuration settings to master of the known universe.  Then that let's me have the option under the media tab to set the device for dvd playback.  It's usually set to something like /dev/dvd which doesn't exist on my system.   I'm not all that knowledgable so what I do to find out the device name of my cdrom is to type "cat /etc/fstab" in a command window and then look at what is being mounted to /media/cdrom or anything similar.  In my case it is /dev/scd0 on one machine and /dev/hdc on another.

If none of this makes sense just answer the top question.

---

