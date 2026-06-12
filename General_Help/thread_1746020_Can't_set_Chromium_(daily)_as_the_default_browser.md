---
title: "Can't set Chromium (daily) as the default browser"
date: 2011-05-01
forum: General Help
---

### Post by blinxwang on 2011-05-01
Hello all,
After recently upgrading to Ubuntu 11.04, I noticed that I cannot set Chromium as the default browser without removing Firefox first. Also, I noticed the option of using a custom program as the default browser has been removed. Can someone fill me in on this?

---

### Post by blinxwang on 2011-05-01
Bump!

---

### Post by Lachinchon on 2011-05-01
I had the same problem. Try this: in the Firefox preferences, *deselect* the option for Firefox to always check to see if it is the default browser. Then open Chromium and select it as default. You should then be good to go.

---

### Post by VanR on 2011-05-01
Well you could just remove all browsers but chromium.

---

### Post by blinxwang on 2011-05-01
> **Lachinchon said:**
> I had the same problem. Try this: in the Firefox preferences, *deselect* the option for Firefox to always check to see if it is the default browser. Then open Chromium and select it as default. You should then be good to go.
It's already unchecked.

---

### Post by TedinOz on 2011-05-01
Open Chromium, open Toolbox>Preferences. On the bottom item on the basics page, click 'Make Chromium my Default Browser'. This worked fine for me.

---

### Post by blinxwang on 2011-05-02
I've done that also. It's gotten to the point where I even dove into gconf and manually edited registry keys, but to no avail. The only way to make Chromium the default browser on my system is to remove all other browsers.

---

### Post by x C0MMAND0 x on 2011-05-02
Try purging chromium and then reinstalling and then seeing if it prompts you to set it as default.

```

sudo apt-get purge chromium-browser
sudo apt-get update 
sudo apt-get install chromium-browser
chromium-browser

```

---

### Post by blinxwang on 2011-05-02
> **x C0MMAND0 x said:**
> Try purging chromium and then reinstalling and then seeing if it prompts you to set it as default.

```

sudo apt-get purge chromium-browser
sudo apt-get update 
sudo apt-get install chromium-browser
chromium-browser

```
Oh it prompts me. It's just that after clicking "yes" it will always set Firefox as default. Also, it doesn't show up in Preferred Applications.
Purging/completely removing didn't work either, sorry. I deleted the .cache and .config folders for chromium as well.

---

### Post by x C0MMAND0 x on 2011-05-02
Try purging firefox as well, since it sounds that like is the culprit.  Then run firefox and tell it to NOT be default browser and save that.  Then try with chromium.

---

### Post by Blasphemist on 2011-05-02
You can have firefox, seamonkey, whatever and still have chromium be the default. System settings, preferred applications, set chromium, and tell chromium it is the default as described in an earlier post in this thread through chromium tools, preferences.

---

### Post by blinxwang on 2011-05-02
> **x C0MMAND0 x said:**
> Try purging firefox as well, since it sounds that like is the culprit.  Then run firefox and tell it to NOT be default browser and save that.  Then try with chromium.

Purged firefox and all related packages, and now pic related shows up in Dash. Also, still not showing up in Preferred Applications as shown in my other attached picture.
I've been having this problem since Beta 2 of Natty, I thought it was just a bug because it was in Beta, but now apparently it's not the case.

---

### Post by Blasphemist on 2011-05-02
I don't see what you are referring to.

---

### Post by lakerssuperman on 2011-05-02
Perhaps you should back up and delete your user configuration files and see if that will fix the problem.  Sometimes wiping these files and starting fresh will clear out any of these little nagging problems.

---

### Post by Lachinchon on 2011-05-02
I was premature in my prior post - just making the changes in the browsers themselves was insufficient. 

This seems to have done the trick, however: go into your "Preferred Applications" system app. There will be a drop-down box to select your "preferred" browser. Select Chromium. Open Chromium (or close and reopen if it was open before). You will again get the "Make Chromium your default browser" inquiry, but now that you have made the change in the system app, when you select to make Chromium your default browser in the app itself, it should stick.

---

### Post by blinxwang on 2011-05-03
The problem I have is that Chromium is not showing up anywhere in Preferred Applications. If I set it as the default browser from within Chromium when Firefox is around, Firefox will become the default browser. If I set it from within Chromium when I've removed firefox, nothing will become the default browser. It's like the system doesn't recognize Chromium as a browser. xdg-settings, gconf, and update-alternatives do nothing. And since Preferred applications has somehow lost its ability to set a custom executable as the Default Browser or Mail program, I really can't do anything other than a clean reinstall to get this problem fixed.

---

### Post by r109chaos on 2011-05-06
I was having the same issue with 11.04 aswell.

Try this. Goto Preferred Applications and set your Web Browser. When you do, open up Chromium and click Set As Default.

Bam! Got it. Also make sure chromium is up-to-date with Update Manager.

---

### Post by fenfir on 2011-05-06
From the terminal type the following command to fix. Not sure if this a bug in chrome or an oversight by Ubuntu.

```

touch ~/.local/share/applications/mimeapps.list

```

---

### Post by blinxwang on 2011-05-06
> **fenfir said:**
> From the terminal type the following command to fix. Not sure if this a bug in chrome or an oversight by Ubuntu.

```

touch ~/.local/share/applications/mimeapps.list

```
Alright, these are the contents of that file:
```


[Added Associations]
video/ogg=smplayer.desktop;
video/x-flv=totem.desktop;smplayer.desktop;smplayer_enqueue.desktop;google-chrome.desktop;
audio/x-flac=smplayer.desktop;
application/x-shellscript=gedit.desktop;
video/webm=smplayer.desktop;
x-scheme-handler/http=firefox.desktop;google-chrome.desktop;
x-scheme-handler/https=firefox.desktop;google-chrome.desktop;
application/x-deb=gdebi.desktop;

[Removed Associations]
application/x-extension-webm=vlc.desktop;
application/vnd.adobe.air-application-installer-package+zip=AdobeAIR-application-vnd.adobe.air-application-installer-package+zip.desktop;
text/x-python=wine-extension-txt.desktop;
image/png=wine-extension-png.desktop;
application/x-shellscript=wine-extension-txt.desktop;

[Default Applications]
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
application/x-deb=gdebi.desktop

```

---

### Post by blinxwang on 2011-05-06
As a quick note, editing the defaults of that file to chromium-browser.desktop didn't do anything other than make preferred applications set Firefox as the default browser. Also, do you guys see an option to use a custom app as the web browser in preferred applications?

---

### Post by JCarmo on 2011-05-07
Set chromium as default in the preferred aplications.
Then just right click your desktop. Create a new document, empty file,  name it something.html. Right click on it, choose open with, other application, and choose chromium.

Worked for me

---

### Post by afspear on 2011-05-08
> **r109chaos said:**
> I was having the same issue with 11.04 aswell.

Try this. Goto Preferred Applications and set your Web Browser. When you do, open up Chromium and click Set As Default.

Bam! Got it. Also make sure chromium is up-to-date with Update Manager.

Done!  This worked for me. Thanks!

---

