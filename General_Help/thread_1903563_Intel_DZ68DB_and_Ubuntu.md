---
title: "Intel DZ68DB and Ubuntu"
date: 2012-01-02
forum: General Help
---

### Post by Alejandro2 on 2012-01-02
Hello, happy New Year!

First of all I'd like to introduce myself: my name is Alejandro and I'm new to Lynux and Ubuntu.  This will be my first experience with a Lynux based OS and I'm eager to see what it has to offer.

I'm not sure if this is the correct place for this question, sorry if it's not:

I have just installed the latest Ubuntu version on my machine and I can't get the proper resolution set up.  It's running at 1024x768 and I can't get it to any other resolutions.  Is this a motherboard problem or a monitor driver problem?

I have the following PC:

Motherboard: Intel DZ68DB
Micro: Intel i5-2310
Ram: 4GB
Monitor: Samsung SyncMaster 2253nw

Sorry if this was posted already, I tried to look for this info on the forums but I didn't find anything.

Thanks a lot for your help.

---

### Post by Mr Nemo on 2012-01-02
Here check these out and report back.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[http://ubuntuforums.org/showthread.php?t=1705929](http://ubuntuforums.org/showthread.php?t=1705929)

If you haven't already try going to System -> Preferences -> Monitors  and see if you can select another resolution (If you're using 11.10 I believe typing monitors into the search bar will bring it up, I'm not really sure I haven't used Unity much)

Also just for personal knowledge it's Linux not Lynux

---

### Post by sammiev on 2012-01-02
You can also try different version from a CD/DVD or USB stick without installing it on your computer. Great way to see if everything works first and Welcome to Ubuntu Alejandro2!

---

### Post by Mark Phelps on 2012-01-03
Would help to know the make and model video chip. To find out, open a terminal, enter "lspci" -- and look for the line containing "VGA".  Post that info back here.

---

