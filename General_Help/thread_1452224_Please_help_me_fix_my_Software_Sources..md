---
title: "Please help me fix my Software Sources."
date: 2010-04-11
forum: General Help
---

### Post by Viper2 on 2010-04-11
I recently deleted all my Software Sources that were under **"Other Software"** and all my "Authentication" because Mint kept updating my xulrunner to a new version which would disable Firefox-Smooth-Scaling.  Therefore I deleted all my Software Sources that were under **"Other Software"** and Authentication, and forced Mint to only install the xulrunner which uses Firefox-Smooth-Scaling.  Unfortunately, after I deleted the software sources and authentication, now I can't update my system properly and get error messages that keys are missing.  I added some software sources back the "Other Software" (someone responded to a previous post of mine on which ones to add), and under the "Authentication" window I tried hitting "Restore Defaults", but it only added two keys.  

These are screenshots of my Software Sources windows.  Can someone please help me to fix this?  Thank you very much.

[IMG]http://i226.photobucket.com/albums/dd153/yvs2007/Stuff/Screenshot-1-1.png?t=1271017115[/IMG]

[IMG]http://i226.photobucket.com/albums/dd153/yvs2007/Stuff/Screenshot-2.png?t=1271017192[/IMG]

[IMG]http://i226.photobucket.com/albums/dd153/yvs2007/Stuff/Screenshot-3.png?t=1271017233[/IMG]

---

### Post by stilling on 2010-04-11
to reconfigure your sources from scratch 
click on Sources in my signature

and after you chouse your needs sudo gedit /etc/apt/sources.list
add from official to unofficial save close
sudo apt-get update
to add the unnofiifcial follow the steps from there


Hope this helps

---

### Post by StefanSeo on 2010-04-11
Delete everything you have in the Other Software and add these two:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

Set you distribution on both (karmic) and type: in the first set binary, and in the second Source.

---

### Post by Viper2 on 2010-04-11
> **StefanSeo said:**
> Delete everything you have in the Other Software and add these two:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

Set you distribution on both (karmic) and type: in the first set binary, and in the second Source.

Exactly how do I add these to "Other Software"?  I can't just click "add" and copy & paste them.  Doesn't work.

Thanks.

---

### Post by oldsoundguy on 2010-04-11
OR .... you can install Ubuntu Tweaks for your build and let it do all of the work for you.

---

