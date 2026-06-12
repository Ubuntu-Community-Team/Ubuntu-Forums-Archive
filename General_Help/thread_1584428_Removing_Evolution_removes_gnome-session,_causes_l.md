---
title: "Removing Evolution removes gnome-session, causes login loop"
date: 2010-09-29
forum: General Help
---

### Post by tiznom on 2010-09-29
Posting a solution to the login loop I had after removing Evolution, **and related packages**, in the Software Center. If you do so, you will not be able to log back in to your desktop on reboot. You will just be redirected to your login over and over. I found a few threads helpful and lots of well intentioned but bad info in many other posts. Hope this summary helps someone trying to recover their desktop as I was all morning. 

[This post]("http://ubuntuforums.org/showpost.php?p=9446685&postcount=13") [ubuntuforums.org] is what confirmed the problem for me. I ran into a few problems trying to follow the recommendations though. Here's what went wrong and what worked. 

At the login screen, click your name and try your password like normal. Did it come right back to the login screen? Time to fix that. Press Ctrl+Alt+F2. If you see a terminal prompt, skip one paragraph ahead.

I have a HDTV hooked up as a second monitor for occasional use. When I tried the Ctrl+Alt+F2, I just got a blank screen on my main monitor. You have to get to the terminal to continue, so I was stuck. It took a little while for me to figure out to try turning on the second monitor to see the command prompt. If you have more than one monitor connected, turn them all on before your try Ctrl+Alt+F2. 

If you are connected by wifi you may need to plug in to an ethernet port on your router to continue the next part. You have to re-download and install gnome-session, and I was unable to connect over wifi at that point. 

Once you get the terminal up, you have to enter your name & password, then you get a proper command prompt. Type this:
```
sudo apt-get install gnome-session
```You will have to re-enter your admin password, and if you have an internet connection it will download what you need. Type "y" at the prompt to continue downloading and installing. 

That's what worked for me, hope it helps. The second monitor and WPA protected wifi stalled me for a while. I am still scratching my head wondering why something like this could go wrong, but I understand I removed something vital by accident, and didn't get any kind of "are you sure you want to do something this stupid?" warning before it. 

Thanks to *_beckols_* for the info, I just added a couple extra things and put it all in one post.

---

### Post by HermanAB on 2010-09-29
Hmm, trying to uninstall stuff is like trying to unscramble an egg. It is usually better just to let it be.

---

