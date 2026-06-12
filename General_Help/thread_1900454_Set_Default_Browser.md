---
title: "Set Default Browser?"
date: 2011-12-26
forum: General Help
---

### Post by cdmoomaw on 2011-12-26
Hi all, I have recently installed Xubuntu on an old HP Pavilion zv5000, and it is running fairly well, aside from the fact that although I have both set Chromium browser as default in the browser, as well as in the settings panel; the OS still opens Firefox with a link. All the existing articles I found were either browser-specific or dealt with Thunderbird. I am running Xubuntu 11.10.

Thanks,
~ CDMoomaw

---

### Post by Toz on 2011-12-26
Hello and welcome to the forums.

Where (which application) is the link coming from? There may be an application-specific setting to set the browser.

Otherwise, try in a terminal window:
```
sudo update-alternatives --config x-www-browser
```
...and (maybe)
```
sudo update-alternatives --config gnome-www-browser
```
...and make sure chromium is selected.

---

### Post by cdmoomaw on 2011-12-26
It's coming from any and every application on the machine (so far, I have tried Thunderbird, AbiWord, Leafpad; all opening Firefox), and on the terminal lines, do I type them exactly as written, or am I supposed to insert "chromium-browser" somewhere?

---

### Post by Toz on 2011-12-26
Type them as you see them. You will prompted for your password (root privileges are required to make this change) and then you will be prompted for which browser to choose. Type the corresponding number for chromium. 

See if that helps.

---

### Post by cdmoomaw on 2011-12-26
Tried both, to no avail.

---

### Post by Toz on 2011-12-26
Have a look at this link regarding gconf settings: [http://askubuntu.com/questions/18418/how-to-set-which-application-is-launched-by-xdg-open]("http://askubuntu.com/questions/18418/how-to-set-which-application-is-launched-by-xdg-open")

---

### Post by cdmoomaw on 2011-12-26
Nothing, unless I type xdg-open [www.google.com](www.google.com) does it open chromium. Also, in the article, 

[LIST]
[*]/desktop/gnome/url-handlers/unknown/command
[*]/desktop/gnome/url-handlers/http/command
[*]/desktop/gnome/url-handlers/https/command
[*]/desktop/gnome/url-handlers/about/command
[/LIST]
the 1st and 4th entries don't exist on my system, only the 2nd and 3rd ones. Could this have something to do with Xubuntu? Also, I noticed that before I changed the entries, they were set to Sensible Browser, not Firefox. One last thing, whenever I reopen chromium, it asks if I want to set it as the default, and every time I say yes.

~ CDMoomaw

---

### Post by Toz on 2011-12-26
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1856468]("http://ubuntuforums.org/showthread.php?t=1856468") - specifically post #15 to ensure that you selected the correct option.

---

### Post by cdmoomaw on 2011-12-26
I have tried both Auto and Manual, it is currently set to Manual, and as I said, It affects xdg-open but nothing else, so something is working. I also read in the thread about uninstalling a browser. How would I remove Firefox, if it's even likely to work?

---

### Post by freedmax on 2012-04-02
I solved on my Xubuntu 12.04, but it should go well on previous versions too.
First, clean any file of chromium in ~/.local/share/xfce4/helpers.
After, start Chromium by Xfce menu and then set it as default in preferences.
Then, go to ~/.local/share/xfce4/helpers and edit the file of chromium that is been now created, leaving only these lines:

[Desktop Entry]
Version=1.0
Name=Chromium Web Browser
Icon=chromium-browser
Type=X-XFCE-Helper
X-XFCE-Category=WebBrowser
X-XFCE-Commands=/usr/bin/chromium-browser
X-XFCE-CommandsWithParameter=/usr/bin/chromium-browser "%s"

Then, go to "Preferred Application" in the Xfce Settings Manager and select "Chromium Web Browser" as browser default on menu. 
Now you should have Chromium as default for Chromium and for Xfce.
I hope those of Xubuntu solve this little problem.

---

### Post by cdmoomaw on 2012-04-12
> **freedmax said:**
> I solved on my Xubuntu 12.04, but it should go well on previous versions too.
First, clean any file of chromium in ~/.local/share/xfce4/helpers.
After, start Chromium by Xfce menu and then set it as default in preferences.
Then, go to ~/.local/share/xfce4/helpers and edit the file of chromium that is been now created, leaving only these lines:

[Desktop Entry]
Version=1.0
Name=Chromium Web Browser
Icon=chromium-browser
Type=X-XFCE-Helper
X-XFCE-Category=WebBrowser
X-XFCE-Commands=/usr/bin/chromium-browser
X-XFCE-CommandsWithParameter=/usr/bin/chromium-browser "%s"

Then, go to "Preferred Application" in the Xfce Settings Manager and select "Chromium Web Browser" as browser default on menu. 
Now you should have Chromium as default for Chromium and for Xfce.
I hope those of Xubuntu solve this little problem.

After trying what you suggested, It did not work, but I was able to fix the problem by simply typing "sudo apt-get remove firefox" at the terminal. Thank you all for your help!

~ CDMoomaw

---

### Post by cdmoomaw on 2012-04-12
.

---

### Post by lnxguit on 2012-05-05
I followed these directions EXACTLY, and it worked PERFECTLY!
It took me a couple tries - make sure you choose "Chromium Web Browser".
Thanks freedmax!

---

