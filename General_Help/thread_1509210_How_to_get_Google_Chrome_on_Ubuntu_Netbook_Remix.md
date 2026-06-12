---
title: "How to get Google Chrome on Ubuntu Netbook Remix"
date: 2010-06-14
forum: General Help
---

### Post by koanakai on 2010-06-14
Hello,

This is my second day using a Linux based OS and it is very confusing for me. I think I can appreciate it once I get the hang of it. I don't like Firefox and want to use Google Chrome instead so I went to the website and downloaded it. I, whatever the equivalent of unzipping it, and it didn't tell me where it went. That's not the problem, however, I want Google Chrome to show up where all the other apps are. You know, where you get apps retrieved from Ubuntu Software Center. 

Sorry for the n00b question. I need to find a good website to read up on Linux basics. Thanks in advance!

---

### Post by fooman on 2010-06-14
download the appropriate file from here (choose 32bit or 64bit .deb for ubuntu):

[http://www.google.com/chrome/eula.html?platform=linux](http://www.google.com/chrome/eula.html?platform=linux)

then just double-click on the file to install.  after it installs,  you should find it under applications > internet

hope that helps.

---

### Post by scouser73 on 2010-06-14
> **koanakai said:**
> Hello,

This is my second day using a Linux based OS and it is very confusing for me. I think I can appreciate it once I get the hang of it. I don't like Firefox and want to use Google Chrome instead so I went to the website and downloaded it. I, whatever the equivalent of unzipping it, and it didn't tell me where it went. That's not the problem, however, I want Google Chrome to show up where all the other apps are. You know, where you get apps retrieved from Ubuntu Software Center. 

Sorry for the n00b question. I need to find a good website to read up on Linux basics. Thanks in advance!

I assume that there are no 64bit netbooks, so here goes.

**1** - Go to [http://www.google.com/chrome/eula.html?platform=linux](http://www.google.com/chrome/eula.html?platform=linux)

**2** - in the options list, select **32 bit .deb (For Debian/Ubuntu)**

**3** - Finally click **Accept and Install**

Google Chrome will now be installed on your computer.

---

### Post by koanakai on 2010-06-14
Thank you so much. I may be asking this question later so I'm going to go ahead and ask it now. How do I properly delete an app to make sure all of its supporting files go with it?

---

### Post by garvinrick4 on 2010-06-14
> **koanakai said:**
> Thank you so much. I may be asking this question later so I'm going to go ahead and ask it now. How do I properly delete an app to make sure all of its supporting files go with it?
See what this does for you.

```
sudo apt-get purge (package name)
``````
man apt-get
```

Read the "man apt-get" in terminal that is the best way to learn.

---

