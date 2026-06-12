---
title: "Firefox 3.0 in Karmic"
date: 2009-11-09
forum: General Help
---

### Post by BlueCanary9999 on 2009-11-09
I'd like to get Firefox 3.0 instead of 3.5 because
1) 3.5 doesn't have close-buttons on non-active tabs (for some reason),
2) there aren't really good themes for 3.5, and
3) the application font in 3.5 is too big.

I've downloaded Firefox 3.0 from the Software Center and also tried "sudo apt-get install firefox-3.0", which downloaded something.  But I don't know how to access either.  Notably, when I type "firefox*" into the terminal, it returns
"No command 'firefox*' found, did you mean:
 Command 'firefox' from package 'firefox-3.5' (main)
 Command 'firefox' from package 'firefox-3.0' (universe)
firefox*: command not found".
Is there a way I could use the universe 'firefox-3.0' package?

Or, more preferably, is there a way I could get the close-buttons back, and shrink the application font for Firefox only?

Thanks in advanced!

---

### Post by jbrown96 on 2009-11-09
Looks like firefox-3.0 should run 3.0. Be aware that 3.0 reaches end of life in December and won't get any more security fixes. In the location bar, type about:config that should allow you to change the font. The lack of close buttons sounds really strange and should be fixed with a reinstall of firefox. If you are messing with the themes, it is possible that it could be causing a rendering bug. Is the button not visible, or does it not exist?

---

### Post by scouser73 on 2009-11-09
You should think carefully about installing older versions of browsers on your system as it's not patched for vulnerabilities unlike the most up-to-date versions.

My advice would be to stick to the latest version of Firefox [Firefox **3.5.5**] and then post questions to the author of the themes you like as to when they're going to update their addons.

---

### Post by BlueCanary9999 on 2009-11-09
Running "firefox-3.0" doesn't work:
```
chris@Suanpan:~$ firefox-3.0
The program 'firefox-3.0' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
firefox-3.0: command not found
chris@Suanpan:~$ sudo apt-get install firefox-3.0
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```o_O
But thanks for the advice.  I guess I ought to get comfortable to 3.5....

about:config seems to only be able to change the fonts in the web page.  I'd like to change the font size in the URL, bookmarks toolbar, and tabs.  It's no biggie, but it's a little annoying right now.

Well, the close buttons returned after reinstalling FF.  :D

Thanks.  I'll email them.

---

