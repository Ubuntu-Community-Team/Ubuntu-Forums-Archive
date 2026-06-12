---
title: "Completely remove Firefox?"
date: 2009-12-30
forum: General Help
---

### Post by PDA1 on 2009-12-30
I want to completely remove Firefox.  I DON'T want any traces of it left on my machine.

Synaptic doesn't do it well and leaves traces of it.

How do I get rid of Firefox?

---

### Post by Barriehie on 2009-12-30
> **PDA1 said:**
> I want to completely remove Firefox.  I DON'T want any traces of it left on my machine.

Synaptic doesn't do it well and leaves traces of it.

How do I get rid of Firefox?

You can see [this post](http://ubuntuforums.org/showthread.php?t=1231349&highlight=remove+firefox) regarding complete removal.

Barrie

---

### Post by PDA1 on 2009-12-30
Tried it.

Doesn't work.

The wretched thing keeps coming back.

---

### Post by Enigmapond on 2009-12-30
Quite possibly you have more than one version on your system as if you did what the tutorial said, that would have worked. Possibly look also in your root/bin opt and ect directories for anything "firefox" or "mozilla".

---

### Post by lovinglinux on 2009-12-30
There is no need to remove Firefox if you are worried about personal data. Just delete the folder ~/.mozilla/firefox, which contains your Firefox profiles. All your personal data (cookies, passwords, history, bookmarks, extensions...) will be deleted.

You might also want to delete ~/.macromedia, to get rid of flash cookies.

If you still want to delete the application files, then run these:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.1
sudo apt-get purge firefox-3.5
sudo apt-get purge firefox-3.6
sudo apt-get purge firefox-3.7
```

This will take care of almost all versions that could be installed from the repositories.

If you have installed a different version of Firefox from other sources, then check the Install Other Version section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

That thread will also help you improve Firefox performance if that is the reason why you want to remove it.

---

### Post by jamesisin on 2009-12-30
Could you expand upon "The wretched thing keeps coming back"?  Do you mean to say that it is reinstalling itself?

---

### Post by Barriehie on 2009-12-30
> **PDA1 said:**
> ...muted...The wretched thing keeps coming back.

Please describe wretched, what are your issues???

Barrie

---

### Post by PDA1 on 2009-12-30
My use of the word "wretched" applied to the fact that using Synaptic and deleting the .mozilla/ folder, etc and that Firefox 3.5.8pre kept loading whenever I clicked on the icon found in Applications> Internet (even though everything was supposedly deleted) mad me pretty mad.

I can't get rid of this Shiretoko (what kind of name is that anyway?) 3.5.8pre with none of the methods mentioned above.....short of using a sledge hammer.

I'll have to live with it.


What started this whole thing was that my bank said that I was using an unsupported "browser" and that I should download another version of Firefox.  So, I said to myself, "I'll see if I can remove 3.5.8pre and get the 3.5 (or whatever it was) installed".  Well, I was wrong- so far THE BEAST still keeps coming back when I click on the icon mentioned previously.

I'll just have to live with it.

Thanks for all of the help, folks.

---

### Post by Barriehie on 2009-12-30
Shouldn't have to 'live with it'! I've found this link in another post you might want to check out. [Click here](http://ubuntuforums.org/showpost.php?p=8005059&postcount=3).  Try to get the version you're happy with and then check out this [addon](https://addons.mozilla.org/en-US/firefox/search?q=user+agent+switcher&cat=all&advancedsearch=1&as=1&appid=1&lver=3.0&atype=0&pp=20&pid=2&sort=&lup=).  It's a user agent switcher and firefox will tell the server you're running Vista with IE or whatever you tell it to tell.  I've had a banking site do the same thing so I use this and all is well!

Barrie

---

### Post by blazemore on 2009-12-30
It sounds like you've added some kind of repository for testing versions of Firefox.
Have a look at your Software Sources to see if there's anything like mozilla-testing PPA, remove it and try the above steps again.

Failing that, you could just remove the shortcut from your menu. Right-click the menu and do "edit menus"

---

### Post by PDA1 on 2009-12-30
> **Barriehie said:**
> Shouldn't have to 'live with it'! I've found this link in another post you might want to check out. [Click here]("http://ubuntuforums.org/showpost.php?p=8005059&postcount=3").  Try to get the version you're happy with and then check out this [addon]("https://addons.mozilla.org/en-US/firefox/search?q=user+agent+switcher&cat=all&advancedsearch=1&as=1&appid=1&lver=3.0&atype=0&pp=20&pid=2&sort=&lup=").  It's a user agent switcher and firefox will tell the server you're running Vista with IE or whatever you tell it to tell.  I've had a banking site do the same thing so I use this and all is well!

Barrie


I have to tell you that I laughed when I read your comments.  They're just perfect.  By the way, I installed the User Agent add-on.  That too made my day much better.

Thanks a lot.

---

### Post by Barriehie on 2009-12-30
> **PDA1 said:**
> I have to tell you that I laughed when I read your comments.  They're just perfect.  By the way, I installed the User Agent add-on.  That too made my day much better.

Thanks a lot.

:)

---

### Post by PDA1 on 2009-12-30
> **blazemore said:**
> It sounds like you've added some kind of repository for testing versions of Firefox.
Have a look at your Software Sources to see if there's anything like mozilla-testing PPA, remove it and try the above steps again.

Failing that, you could just remove the shortcut from your menu. Right-click the menu and do "edit menus"


This is what my software sources screen looks like.  Is what you mentioned in it?

---

### Post by darkstaar on 2009-12-30
> **PDA1 said:**
> What started this whole thing was that my bank said that I was using an unsupported "browser" and that I should download another version of Firefox.

Ha. I'd be dumping my wretched bank, not my beloved Firefox.

---

### Post by jamesisin on 2009-12-30
You have repos for both Mozilla Beta and Mozilla Daily.

---

### Post by PDA1 on 2009-12-30
I think we solved the problem-

[http://www.youtube.com/watch?v=PXKXVK-qZa4](http://www.youtube.com/watch?v=PXKXVK-qZa4)


Can I mark this "solved" now?

---

### Post by Barriehie on 2009-12-30
> **PDA1 said:**
> I think we solved the problem-

[http://www.youtube.com/watch?v=PXKXVK-qZa4](http://www.youtube.com/watch?v=PXKXVK-qZa4)


Can I mark this "solved" now?

Had a friend shoot his one time; week later wanted me to fix it!

---

### Post by lovinglinux on 2009-12-31
> **PDA1 said:**
> This is what my software sources screen looks like.  Is what you mentioned in it?

Uninstall Firefox with:

```
sudo apt-get purge firefox firefox-3.5
```

Then open your Software Sources and remove the **ubuntu-mozilla-daily** and **mozilla-beta** ppas. Then  run these:

```

sudo apt-get update
sudo apt-get install firefox

```

This should restore the default Firefox version from the repositories.

---

### Post by danastasio on 2009-12-31
```
sudo apt-get purge firefox*
```

Note the * this little gem tells the system "anything that starts with firefox". You will get everything this way. I did, and running firefox in a terminal tells me it is not installed. If you want to see just how powerful this is, run 
```
sudo apt-get install firefox*
```

Which will show you each and everything firefox related that you could ever possibly install on your system. 
But you are using it to remove.

Yin and Yang.

Apt and Get

Together they make synaptic, and your life easier.

...bed now XD

---

### Post by jamesisin on 2009-12-31
Shouldn't that be --purge?

---

### Post by lovinglinux on 2009-12-31
> **jamesisin said:**
> Shouldn't that be --purge?

Just purge always worked for me. I guess you can do something like this:

```
sudo apt-get remove --purge firefox
```

Which is the same as running:

```
sudo apt-get purge firefox
```

---

### Post by danastasio on 2009-12-31
Honestly, I was never told about the "--" before purge, and have always just used purge w/o issue. Thanks for the info though.

---

### Post by jamesisin on 2010-01-02
Maybe I was mistaken then.  I thought you could use apt-get remove --purge [application] (old method) or apt-get remove [application] and then run apt-get purge (which is more assured since the --purge argument is dependent upon something in the remove argument and not implemented consistently).

---

