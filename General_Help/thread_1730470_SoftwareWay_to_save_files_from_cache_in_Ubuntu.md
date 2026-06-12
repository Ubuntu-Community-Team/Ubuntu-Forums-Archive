---
title: "Software/Way to save files from cache in Ubuntu"
date: 2011-04-16
forum: General Help
---

### Post by neosudhan on 2011-04-16
Hello,

Hope this is the right place to ask this...
In windows I use a software called videocacheview to save files from browser cache irrespective of the browser being used (such as youtube videos that have completed caching). I was just wondering if there is a similar software for ubuntu or a command that can do the trick.

Thanks in advance :)

---

### Post by WorMzy on 2011-04-16
Not as far as I know of. You'll have to manually extract the cache files from the respective folders.

Firefox: ~/.mozilla/firefox/[COLOR="Red"]<profile name>[/COLOR]/Cache
Chromium: ~/.cache/chromium/Cache
Opera: ~/.opera/cache

---

### Post by hawthornso23 on 2011-04-16
A sometimes useful trick is to copy files out of memory using the /proc filesystem. 

Example:

[LIST=1]
[*]Go to youtube and browse a video.
[*]Open a terminal and enter ```
 ps -A | grep plugin
``` to find the number of the plugin container process ... ```
 5464 ?        02:31:00 plugin-containe
``` ... in my case 5464
[*]Open nautilus and browse to the process in the /proc file system. In my case /proc/5464.
[*]Open the fd subdirectory which points to the files used by the process as stored in memory.
[*]The files have no names - only numbers - but Nautilus is smart enough to identify which ones are video files. It'll even show you a thumbnail.
[*]You can view the file where it is in memory, or copy it to some other location.
[/LIST]
Cool trick eh. Variants of this trick can also be used to retrieve things like swf files for flash games. The difficult part is knowing which process to look in and figuring out which file to copy.

---

### Post by neosudhan on 2011-04-17
> **hawthornso23 said:**
> A sometimes useful trick is to copy files out of memory using the /proc filesystem. 

Example:

[LIST=1]
[*]Go to youtube and browse a video.
[*]Open a terminal and enter ```
 ps -A | grep plugin
``` to find the number of the plugin container process ... ```
 5464 ?        02:31:00 plugin-containe
``` ... in my case 5464
[*]Open nautilus and browse to the process in the /proc file system. In my case /proc/5464.
[*]Open the fd subdirectory which points to the files used by the process as stored in memory.
[*]The files have no names - only numbers - but Nautilus is smart enough to identify which ones are video files. It'll even show you a thumbnail.
[*]You can view the file where it is in memory, or copy it to some other location.
[/LIST]
Cool trick eh. Variants of this trick can also be used to retrieve things like swf files for flash games. The difficult part is knowing which process to look in and figuring out which file to copy.

Cool trick indeed..I managed to do just what I wanted with this but with a few limitations..

First of all this did not work for chrome as the video rendering process in chrome does not have the word plugin in it. I'm Still trying to figure out how to find out the process name/number for chrome.

Second the direct copy paste did not work for copying the file but cp command did the trick. I have no idea why though. If anyone knows please do enlighten me..

Thanks for the info mate :)

---

### Post by neosudhan on 2011-04-17
> **WorMzy said:**
> Not as far as I know of. You'll have to manually extract the cache files from the respective folders.

Firefox: ~/.mozilla/firefox/[COLOR="Red"]<profile name>[/COLOR]/Cache
Chromium: ~/.cache/chromium/Cache
Opera: ~/.opera/cache

Thanks for your reply but since I'm a newbie to linux I really have no idea as to how to get to the folder path you have specified. It would be great if you could explain the same in more detail.

---

### Post by WorMzy on 2011-04-17
~ = /home/your-username/
.foldername = a hidden folder (any file or folder starting with a dot (.) is hidden by default)

In the Applications | Places | System menu, go to Places -> Home Folder, then press Ctrl+H to make the hidden folders visible.

---

### Post by neosudhan on 2011-04-17
> **WorMzy said:**
> ~ = /home/your-username/
.foldername = a hidden folder (any file or folder starting with a dot (.) is hidden by default)

In the Applications | Places | System menu, go to Places -> Home Folder, then press Ctrl+H to make the hidden folders visible.

Thanks for clearing that up..

And wow...this is much simpler..Thanks mate :)

---

### Post by coldraven on 2011-04-17
Or if you like Firefox just install the Flashgot plugin.

Another handy tip: if you want to go to a directory in Nautilus.
Say you have the path /this/that/else that you have just copied from a terminal or a forum.
In Nautilus press CTRl+L, then Ctrl+V, hit Enter and you're there

---

