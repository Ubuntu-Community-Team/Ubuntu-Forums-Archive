---
title: "Video turns white"
date: 2009-09-13
forum: General Help
---

### Post by Shiv4m on 2009-09-13
Okay I have been getting this problem till the day I installed Ubuntu for the very first time but never asked for help about this issue till now. Sometimes when I got on YouTube or MTV cribs, the video turns completely white/grey and only sound comes up. When I'm lucky the video shows up or when I restart FireFox it works but for other websites like MTV, it will never show up.

I searched everywhere for a solution but never found anything:

[IMG]http://img29.imageshack.us/img29/5066/screenshotgy.png[/IMG]

---

### Post by thegreatsnafu on 2009-09-13
Hi,

What version of Adobe Flash Player are you using? Are you using a 32bit ubuntu or a 64bit? These will help me to better understand your question.

---

### Post by Shiv4m on 2009-09-14
No idea on which Flash player I'm using and I'm on a 64bit.

---

### Post by Shiv4m on 2009-09-14
How would I be able to check my flash player version and does anyone have a solution to this?

---

### Post by thegreatsnafu on 2009-09-14
> **Shiv4m said:**
> How would I be able to check my flash player version and does anyone have a solution to this?

That's easy:


[LIST=1]
[*]Go to any flash enabled web page.
[*]Right click on the flash element.
[*]Select the "About Flash Player" option.
[/LIST]
This will tell you the version of flash you are using

---

### Post by Shiv4m on 2009-09-14
Okay I have version 9 of flash, what now?

---

### Post by thegreatsnafu on 2009-09-15
The only thing I can suggest for you now is to install the beta version of flash 10 64-bit. Here's the link:

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

That should work much better on a 64-bit system...

---

### Post by Shiv4m on 2009-09-15
How would I go by installing this?

---

### Post by thegreatsnafu on 2009-09-16
OK, here's how to install.


[LIST=1]
[*]Go to the adobe labs flash page: [http://labs.adobe.com/downloads/flashplayer10.html.]("http://labs.adobe.com/downloads/flashplayer10.html")[]("http://labs.adobe.com/technologies/flashplayer10/")
[*]Then at the bottom of the page, click "[COLOR=Black][Download 64-bit Plugin for Linux]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz")[/COLOR] (TAR.GZ, 3.64 MB)".
[*]Close firefox.
[*]Open the file and drag the contents to the desktop.
[*]Open a terminal and type or copy: ```
cd Desktop
``` and press enter/return.
[*]Then type or copy: ```
sudo mv libflashplayer.so /usr/lib/firefox/plugins/
``` and press enter/return.
[*]Reopen firefox.
[/LIST]
That should do it! enjoy!

---

### Post by Perfect Storm on 2009-09-16
There installation script here; [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by Shiv4m on 2009-09-16
Works, thank you so much!

---

### Post by thegreatsnafu on 2009-09-16
Glad to see that your problem is solved. If you have any more problems, the community (and myself) are always glad to help. Enjoy Ubuntu!!!:)

---

