---
title: "Google Chrome: Enable Flash Support"
date: 2010-06-06
forum: General Help
---

### Post by Louisraritan on 2010-06-06
Hi, I am new to Ubuntu and couldn't be happier with such a cool OS.   After installing Lucid Lynx and then Google Chrome (suggested by many as the best browser) I noticed some buggy performance issues.  While watching Youtube videos the sound was fine but the video was choppy.  It took quite a bit of searching around to find a solution for my problem.  Now that I have it, will share it with you as the spirit of Ubuntu has made me feel generous.  Additionally, I will recommend a useful extension for Chrome.

Step 1:  Go to Ubuntu Software Center and search for the Adobe Flash Plugin.  Install it.

Here is where it got tricky for me.

Installing the Flash plugin

Open a terminal and copy/paste these commands to create a plugins folder in the Google Chrome directory

sudo mkdir /opt/google/chrome/plugins
Copy the libflashplayer.so file to the plugins folder.

sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /opt/google/chrome/plugins
Note: change the source path if your libflashplayer.so file is not located at other location.

With me so far?  If yes:
Step 2:  Click applications, Internet, right click Google Chrome and add it to panel (or desktop).  Now right click the Chrome Icon on the panel and choose properties.  On the launcher panel properties box is a command text box.

Copy this command and paste it in the command text box:
/opt/google/chrome/google-chrome --enable-plugins %U

Close the box.  Now my friend, you are all set with flash support in Google Chrome.  No more choppy video (unless you have a hardware problem).

We like watching videos on the internet, like our privacy and also are tired of all the ads.  Chrome has a very useful extension for that.  Go to Google Chrome Extensions and check out AdBlock.  

[https://chrome.google.com/extensions/detail/gighmmpiobklfepjocnamgkkbiglidom?hl=en]("https://chrome.google.com/extensions/detail/gighmmpiobklfepjocnamgkkbiglidom?hl=en")

Install it and consider choosing to let it run with incognito.  The developer of AdBlock says it doesn't collect information about your history.  Up to you if you trust that or not but I chose to let it go incognito.  Voila!  No more choppy vids or annoying ads.  Test it out by visiting here and as a bonus treat, increase Chromes speed and performance.

[http://www.youtube.com/watch?v=gMQ1kZQyFQ4]("http://www.youtube.com/watch?v=gMQ1kZQyFQ4")

---

