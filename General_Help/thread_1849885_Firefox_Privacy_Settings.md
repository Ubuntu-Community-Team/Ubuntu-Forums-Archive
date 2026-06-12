---
title: "Firefox Privacy Settings"
date: 2011-09-25
forum: General Help
---

### Post by greenco on 2011-09-25
I recently installed Ubuntu 10.04 LTS and I am using Firefox 3.3.22. I have tried to set up the Privacy settings to "Use Custom Settings for History" and when I exit the preference screen, the settings are not saved. The next time I look it is showing the default setting. Does anyone have a fix for this problem. I have the same programs installed on my laptop and it also has the same problem.
Thanks

---

### Post by dino99 on 2011-09-25
Firefox 3.3.22, hm thats so old ;)

---

### Post by greenco on 2011-09-25
Sorry about that! It is version 3.6.22

---

### Post by lovinglinux on 2011-09-26
> **greenco said:**
> I recently installed Ubuntu 10.04 LTS and I am using Firefox 3.3.22. I have tried to set up the Privacy settings to "Use Custom Settings for History" and when I exit the preference screen, the settings are not saved. The next time I look it is showing the default setting. Does anyone have a fix for this problem. I have the same programs installed on my laptop and it also has the same problem.
Thanks

Depending on the settings you choose, it reverts because you are using the same settings as the default profile. Try changing the settings a little bit and check if they stick.

If not, then you can delete the file *prefs.js* from your Firefox profile folder, which is located under **~/.mozilla/firefox/<profilename>**. Keep in mind this will reset all your settings, but won't delete bookmarks or passwords. You must close Firefox to do that.

---

### Post by greenco on 2011-09-27
Thanks lovinglinux, but you suggestion did not work. I can not find the "**~/.mozilla/firefox/<profilename" **folder or the** perfs.js** file. In fact I  can not find any file or folder for Firefox. I am now using Foxfire 6.0.2 and it has the same problem as 3.6.22. I used the "Search for files" option under "Places" and there is not any reference for Firefox.

---

### Post by Frogs Hair on 2011-09-27
To find your user folder , open Nautilus use Crtl + H to display hidden folders in home and scroll until you find the .mozilla folder.

---

### Post by greenco on 2011-09-27
I found the perfs.js file in the "Home/coleman/mozilla/firefox/2k4ts7cw" folder. I deleted it and restarted Firefox so it would generate a new "perfs.js" file. It still will not save the privacy settings. If I change it to "Never remember history" and close the window, it will keep this setting. If I change it to "Use custom settings" it will not keep it when I close the screen.

---

### Post by greenco on 2011-09-27
I removed the check mark out of the "Remember Download History" option and it saved the privacy settings.
Thanks for everyone's help!

---

