---
title: "Script problem with Firefox"
date: 2012-04-01
forum: General Help
---

### Post by aoniumo on 2012-04-01
There seems to be a problem with Firefox.  Firefox would freeze causing the entire computer to freeze.  While watching video or listening to music, the video and music would just loop not moving.  I don't really want to listen to the same two lines of Coldplay's Paradise over and over again.  The CPU usage would shut up to 100%



Once the computer is stable again.  I'm usually able to fix by unplugging the internet connection, the following script errors would appear one after the other:

1) Script: resource:///components/nsPrompter.js:68  2) Script: chrome://global/content/bindings/browser.xml:0
  3) Script: [https://s-static.ak.facebook.com/rsrc.php/v1/yS/r/B-e2tX_mUXZ.js:53](https://s-static.ak.facebook.com/rsrc.php/v1/yS/r/B-e2tX_mUXZ.js:53)



 What is this "chrome" script?  Why is this happening?  Anyway to fix?

Also in addition to Firefox using a bunch of CPU power, so is  gnom-system-monitor when I have system monitor launched while waiting  for things to get back to normal.  System monitor and Firefox alternate  using 100% of CPU.

Here are the list of plugins installed on Firefox (I have the same since 11.10):

 --Divx webplater
--Gnome shell integration
--IcedTea-Web Plugin (using IcedTea-Web 1.1.3)
--Quicktime Plugin 7.6.6
--Shockwave Flash
--VLC Multimedia Plugin
--Windows Medica Player Plug-in 10


Here are the list of extensions (I've had the same extensions since 11.10 ubuntu was released and only having the problem today):
--Adblock Plus 2.0.3
--Element Hiding Helper for Adblock Plus
--Global Menu Bar intergration 2.0.3
--Noscript 2.3.5
--Roomy bookmarks toolbar 1.3.3
--Ubuntu Firefox modifications 1.0.3
--WOT 20120302

---

### Post by dcstar on 2012-04-01
> **aoniumo said:**
> There seems to be a problem with Firefox.  Firefox would freeze causing the entire computer to freeze.  While watching video or listening to music, the video and music would just loop not moving.
........

I had to downgrade the latest Adobe Flash Player that was released in the updates a couple of days ago because of problems. You may want to try the same thing.

---

### Post by lovinglinux on 2012-04-01
Does it happen on YouTube as well or just on Facebook?

I am asking this because although flash is the probable culprit, Facebook has a long history of causing issues to Ubuntu users. So it might be a javascript issue on Facebook.

---

### Post by aoniumo on 2012-04-01
> **lovinglinux said:**
> Does it happen on YouTube as well or just on Facebook?

I am asking this because although flash is the probable culprit, Facebook has a long history of causing issues to Ubuntu users. So it might be a javascript issue on Facebook.

I don't watch youtube, so I don't know, but since I've disabled scripts for now with noscript, it's not happening.

---

### Post by lovinglinux on 2012-04-01
> **aoniumo said:**
> I don't watch youtube, so I don't know, but since I've disabled scripts for now with noscript, it's not happening.

Let us know if the problem comes back.

---

### Post by aoniumo on 2012-04-02
> **lovinglinux said:**
> Let us know if the problem comes back.


Thank you.  I have this bookmarked and I'm leaving this unsolved for now.  I'll see in about a week.

---

### Post by aoniumo on 2012-04-03
Now, Firefox just shuts down randomly.  Eh?

---

### Post by lovinglinux on 2012-04-03
> **aoniumo said:**
> Now, Firefox just shuts down randomly.  Eh?

Try to re-install Firefox. Open a terminal and run this:

```
sudo apt-get install --reinstall firefox
```


Also try a clean profile:

```
firefox -P
```

That command opens the profile manager.

During the tests, start Firefox from terminal and post any error produced when it crashes.


Also, check if you have the latest video driver installed. You can do that from *Additional Drivers* application.

---

### Post by aoniumo on 2012-04-03
> **lovinglinux said:**
> Try to re-install Firefox. Open a terminal and run this:

```
sudo apt-get install --reinstall firefox
```
Also try a clean profile:

```
firefox -P
```That command opens the profile manager.

During the tests, start Firefox from terminal and post any error produced when it crashes.


Also, check if you have the latest video driver installed. You can do that from *Additional Drivers* application.


If I re-install, will I retain cookies, bookmarks, saved passwords, installed add-ons, extensions, personas, settings, etc.?

---

### Post by lovinglinux on 2012-04-03
> **aoniumo said:**
> If I re-install, will I retain cookies, bookmarks, saved passwords, installed add-ons, extensions, personas, settings, etc.?

Yes, everything is saved in your FF profile.

---

### Post by aoniumo on 2012-04-05
> **lovinglinux said:**
> Yes, everything is saved in your FF profile.

This seems to have worked, but I have another problem.

[http://ubuntuforums.org/showthread.php?p=11818577#post11818577](http://ubuntuforums.org/showthread.php?p=11818577#post11818577)

---

### Post by aoniumo on 2012-04-05
Never mind. It's not solved.  Still crashes all the time mostly when I am donwnloading something and it's 90% done, then it crashes.  Also, all open folders just crash (they just close on their own).

---

### Post by whistlerspa on 2012-05-15
I have the same problem Firefox locks up all the time and is unusable so frustrating

---

### Post by Savio2010 on 2012-05-15
One easy way is to rename the folder .mozilla in your home folder to something else and start ff again. Doing this will recreate a new profile.


The other easy way is to clear the history and delete urlclassifier3.sqlite from /home/user/.mozilla folder, restart ff with addons disabled. help => Restart with Add-ons Disabled. and then enable the add-ons one at a time restart ff each time and diagnose further.

---

