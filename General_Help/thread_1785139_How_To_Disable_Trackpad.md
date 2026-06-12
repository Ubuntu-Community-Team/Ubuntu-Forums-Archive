---
title: "How To Disable Trackpad"
date: 2011-06-17
forum: General Help
---

### Post by carmenat250 on 2011-06-17
I'm using Ubuntu on my Lenovo laptop which has a pointer mouse and trackpad.

It looks exactly like this:

[http://imageshack.us/photo/my-images/709/trackpad.jpg/](http://imageshack.us/photo/my-images/709/trackpad.jpg/)

How do I disable just the trackpad, but not the red pointer mouse or the buttons above/below the trackpad.

I did do a search and found a file I can download, but isn't there a keystroke or something built into Ubuntu that would avoid me having to download a third party solution.

---

### Post by tgalati4 on 2011-06-17
sudo apt-get install tpconfig
man tpconfig

Over or Under?

Update:  I noticed an "enable touchpad" box under mouse settings in the Preferences section.

A quick google search shows that Fn+F8 will disable the touchpad on T400.  You need to run a script shown here:  [http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400)

Don't know if it will work on other models.

---

### Post by carmenat250 on 2011-06-18
> **tgalati4 said:**
> sudo apt-get install tpconfig
man tpconfig

Over or Under?

I like to use the left/right buttons above the trackpad and the red mouse pointer

---

### Post by tgalati4 on 2011-06-18
Over or Under referred to how you like your toilet paper.  Over or under the roll--as in tp config.  Subtle joke.

---

### Post by carmenat250 on 2011-06-18
I didn't catch the joke, sorry, but the email I got for this response brought me back to this tread.

I wasn't able to get the code that you listed above to work, but I noticed that you updated one of the comments which I have shown below.

I didn't really want to run any extra scripts on my laptop, but just did the fn+f8 and guess what, trackpad disabled.

This solution was PERFECT, thank you

****************************************
Update: I noticed an "enable touchpad" box under mouse settings in the Preferences section.

A quick google search shows that Fn+F8 will disable the touchpad on T400. You need to run a script shown here: [http://www.thinkwiki.org/wiki/Instal..._ThinkPad_T400](http://www.thinkwiki.org/wiki/Instal..._ThinkPad_T400)

Don't know if it will work on other models.

---

### Post by tgalati4 on 2011-06-19
Fn+Fn8 doesn't  work  on mine, so I would need to run the script to activate those keys.

---

