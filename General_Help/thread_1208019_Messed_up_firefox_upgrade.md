---
title: "Messed up firefox upgrade"
date: 2009-07-08
forum: General Help
---

### Post by ianmillington on 2009-07-08
Hi

I've made a right mess of upgrading to FF3.5. I could not get Thunderbird to recognise FF3.5 as the default browser for links. I finally managed it by uninstalling 3.0.11 and then extracting the tar.gz file to the /usr/lib/firefox directory. However, my bank will not accept 3.5 as a valid browser (although it does accept 3.5 in windows and 3.0.11 in Linux so I downgraded. Finally got it working apart from links in Thunderbird no longer work. 

Is there anything I can do about this? I'm blowed if I can find any settings within Thunderbird to make it work.

Thanks

Ian

---

### Post by ianmillington on 2009-07-08
OOPS!

Answer here

[https://lists.ubuntu.com/archives/ubuntu-us-co/2008-August/005042.html](https://lists.ubuntu.com/archives/ubuntu-us-co/2008-August/005042.html)

---

### Post by lovinglinux on 2009-07-08
That's not the correct way of doing Firefox 3.5 installation.

Delete the files you have extracted to /usr/lib/firefox then re-install Firefox 3.0.11, then follow one of the methods available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT). 

There is a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them (5 times) and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by ianmillington on 2009-07-09
Yep, I know it's not the right way, I did it before visiting here. I've now got 3.0.11 up and running properly but because of my bank rejecting 3.5 (Linux only I have to say as it works with Windows) I'm staying put for a while.

---

### Post by lovinglinux on 2009-07-09
You could try [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59) for sites that do not accept the new version.

---

### Post by ianmillington on 2009-07-09
Yes, I have used that on occasions but the version in the repos is not compatible with 3.5. The one from the mozilla extensions page has just installed succesfully on my work (windows) FF3.5 so I'll try that when I get home tonight.

---

