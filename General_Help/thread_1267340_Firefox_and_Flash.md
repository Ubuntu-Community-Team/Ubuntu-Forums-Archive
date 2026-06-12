---
title: "Firefox and Flash"
date: 2009-09-15
forum: General Help
---

### Post by RedRat on 2009-09-15
Running Hardy 8.04 LTS

Ok, I was running Firefox 3 today and after an upgrade on the kernel, FF3 just refused to start. I removed FF completely and reinstalled it. Now I have a "virgin" version of FF and it runs fine. I removed all of the old entries in the .mozzila directory. 

My problem is that it will not play Flash videos, e.g., YouTube. It tells me that I have java script turned off or I do not have the latest versions of Adobe Flash player. I do have java script turned on in FF, I also have the latest Adobe Flash player plugin installed. 

I have searched this site and none of the suggestions seem applicable. Any ideas.

---

### Post by sopadeajo on 2009-09-15
Install the flash player add-on directly from youtube webpage.There is a radio button for Ubuntu (at least for my case).

---

### Post by x C0MMAND0 x on 2009-09-15
If you have 64 bit, do the following.

1. Go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

2. Download the file at the bottom and extract it. It is called libflashplayer.so

3. Go to /home/YOURUSER/.mozilla (hold ctrl-h to show hidden folders)

4. Make a folder called "plugins"

5. Move "libflashplayer.so" to /home/YOURUSER/.mozilla/plugins

6. Restart firefox.

This is the ONLY way I have been able to get it to work, as other users on the forums helped me with this process.

---

### Post by pricetech on 2009-09-15
You might want to copy libflashplayer.so to /usr/lib/mozilla/plugins and /usr/lib/opera/plugins  if you're using other browsers such as Galeon, Opera and Seamonkey.

If you're running 32bit, then just reinstalling flash should do it.

---

