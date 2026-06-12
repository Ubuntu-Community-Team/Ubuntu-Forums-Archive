---
title: "Cannot Change Firefox Download Location"
date: 2009-07-15
forum: General Help
---

### Post by mju4t on 2009-07-15
Hello hello,

My firefox has been acting up lately.  I can't change the location of my firefox downloads.  I click edit --> preferences, then when I click on the BROWSE button to choose a location, nothing pops up.  Also, when I download something, the file doesn't seem to get saved anywhere.  Any ideas?  Thanks,

Alex

---

### Post by wojox on 2009-07-15
You could try this, type about:config into navigation box then scroll down to browser.dowload.dir and set it manually. ex. /home/yourusername

---

### Post by mju4t on 2009-07-15
uh oh....there is no browser.download.dir!

---

### Post by y-lee on 2009-07-15
Hmm very odd. You could try to create one.

[LIST]
[*]Type about:config into the address bar
[*]Right click the about:config window and choose **New** and then **String**.
[*]In the **New String Value** pop-up window type **browser.download.dir** and click **ok**
[*]In the **Enter String Value** pop up window type the location of whatever download directory you wish to use and click **ok**
[/LIST]

---

