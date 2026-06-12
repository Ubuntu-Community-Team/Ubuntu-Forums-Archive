---
title: "Installing Firefox 4 [beta] on 10.04 - wth??"
date: 2011-01-21
forum: General Help
---

### Post by ksaul on 2011-01-21
So i have installed FireFox 4 Beta (..some reason its called Minefield 4.0 Browser??) on ubuntu 10.04 - now I have recently installed it onto my Windows machine about a week ago and I am inlove with it over Chrome, which is why I made the switch for my Ubuntu machine aswell - but I am wondering..

1) Why does it look like Firefox 3?? On windows its a completely new layout, design, and feel.. but on Ubuntu it looks and acts just like regular Firefox 3.

2) Whats with the name difference? When I pull up my browswer data online it says its Mozilla 5.0, but just dont understand?

3) Some javascript/jquery does not work anymore?

Is there something that I have done wrong, or installed the wrong package? I tried to download the file from firefox's website directly (a .tar.bz2 file) but could not figure out how to install it [i am an ubuntu newbie], so I went into terminal and installed it with the package manager with the following command(s):

```

sudo apt-get remove firefox
sudo apt-get autoremove
sudo apt-get autoclean

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-4.0

```

and this is the About details from the browser (help->about)
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14pre) Gecko/20110121 Ubuntu/10.04 (lucid) Namoroka/3.6.14pre


now this might be more of a firefox question, but I am sure there are some Ubuntu users using the 4.0 beta w/ HTML5, WebGL and other new features - help me out guy :)

---

### Post by Verbeck on 2011-01-21
1. the main difference between the windows and ubuntu version is that the 'menu' is not embedded in the title bar. otherwise, the tabs are on top of the url bar, no status bar..... ;)
2. Minefield is what they call the testing/daily version (which you got from the daily ppa). 'cause its a literally 'minefield' and you might get blown up anytime
3. dunno. haven't experienced it myself

as for the tar.bz, just double click *firefox* from within the extracted folder. no need to compile-install anything (its not branded as minefield btw)

---

### Post by djeikyb on 2011-01-21
(1) Yup. The linux gui is far behind the windows gui. Sucks.

(2) And yeah, the daily snapshots are branded as minefield to remind you it isn't a stable build intended for regular use. Mayhaps you're more adventurous than me, but I'd use a public beta rather than a daily snapshot.

(3) Otoh, I'm sure Mozilla can use knowledgeable testers. You should head over to the Mozilla forums and bug tracker and see if the js issues you're experiencing are known or if you have valuable information to report.

(4) Using synaptic or apt-get will install Firefox to your system. With the tar-bzip package, you extract it and run Firefox from your own profile. It does not get installed to the system. Removal is simple as deleting the extracted folder. If you're running test builds, this could be a cleaner way for you to keep track of FF versions.

(5) In the midst of running all these different test builds, it's pretty likely your FF profile will corrupt. You might want to backup your bookmarks and whatnot, or even run a daily backup of your ~/.mozilla folder. Also, when something goes wrong, the first thing you'll want to do is (temporarily at least) remove your profile to make sure it's not causing the problem.

---

### Post by ksaul on 2011-01-22
I ended up switching back to 3.6 stable version, I was having so many issues with Minefield and webpages not working, cookies not saving, javascript, A LOT.... I might try to download the archive (from their website) file and run it like you described instead of using the ppa - i honestly didnt know there was a difference between 'daily'?? and the downloaded archive.

Chrome still seems to be faster (on windows at least), but firefox has alot of nice debugging and dev tools that chrome is missing out on, and I am glad to see that in firefox 4, FireBug is pretty much already incorporated :)

---

### Post by lovinglinux on 2011-01-22
> **ksaul said:**
> I ended up switching back to 3.6 stable version, I was having so many issues with Minefield and webpages not working, cookies not saving, javascript, A LOT.... I might try to download the archive (from their website) file and run it like you described instead of using the ppa - i honestly didnt know there was a difference between 'daily'?? and the downloaded archive.

Chrome still seems to be faster (on windows at least), but firefox has alot of nice debugging and dev tools that chrome is missing out on, and I am glad to see that in firefox 4, FireBug is pretty much already incorporated :)

Instead of getting the latest from the ppa, get the beta release from Mozilla. The ppa is updated daily so it can include new bugs. However, you shouldn't have been experiencing so many errors. I have been using Firefox since the first alpha and it is pretty stable by now.

See my tutorials on how to install Firefox 4, troubleshoot and optimize it.

[http://www.webgapps.org/firefox/installing-firefox-4](http://www.webgapps.org/firefox/installing-firefox-4)

---

### Post by Spr0k3t on 2011-01-22
> **ksaul said:**
> 1) Why does it look like Firefox 3?? On windows its a completely new layout, design, and feel.. but on Ubuntu it looks and acts just like regular Firefox 3.

> **Verbeck said:**
> 1. the main difference between the windows and ubuntu version is that the 'menu' is not embedded in the title bar. otherwise, the tabs are on top of the url bar, no status bar..... ;)

It's funny how habbits die pretty hard.  I've got minefield looking just like FF3 with the tabs below the bookmarks, and the status bar in place.  I like it better that way since I have more than enough screen realestate.  Personally speaking, the look and feel in Windows7 works well... but the same layout in Ubuntu would feel awkward and out of place; similar to how chrome/chromium feels.

To me, the look and feel of FF3 is better than the windows look and feel of FF4.  Just my opinion though.

---

### Post by djeikyb on 2011-01-22
Hehe, and here I am loving how much better chromium fits in with my desktop. But I use Wmfs, not Gnome.

---

### Post by BigCityCat on 2011-01-22
I don't see how this is different than the Windows look. Am I missing something?

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-3.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-3.png)

---

### Post by mikewhatever on 2011-01-22
I've also been testing Firefox4, and get the menu hidden away, as well as tabs on top. Is there anything else that's supposed to happen to the interface?

---

### Post by djeikyb on 2011-01-22
I've been waiting for the enlarged back button for ages.

---

### Post by mikewhatever on 2011-01-23
djeikyb, why don't you use a Windows-like theme? I think it's called Strata ... something.

Edit: Yeap, here you go.
[https://addons.mozilla.org/en-US/firefox/addon/strata-xp-on-linux/](https://addons.mozilla.org/en-US/firefox/addon/strata-xp-on-linux/)

---

### Post by djeikyb on 2011-01-24
Thanks! Pretty nifty. I'll use it once chrome's lack of customizable key-bindings drives me crazy enough to switch back to FF+keyconfig.

---

