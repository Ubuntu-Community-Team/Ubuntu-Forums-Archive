---
title: "firefox upgrade gone bad"
date: 2009-08-09
forum: General Help
---

### Post by kneewax on 2009-08-09
Okay, here's what I did.

I wanted to upgrade my installation of firefox 3.0 to the latest 3.5.2.  So following I backed up my.mozilla/firefox folder and then did the following:

```

tar xvjf firefox-*.bz2
sudo cp -r firefox /usr/lib/firefox-3.5.2
sudo mv /usr/bin/firefox /usr/bin/firefox.old
sudo ln -s /usr/lib/firefox-3.5.2/firefox /usr/bin/firefox-3.5.2
sudo ln -s /usr/bin/firefox-3.5.2 /usr/bin/firefox

```
which I found as instructions linked from this forum

I now get the following erroe when I try to launch FF:
```

Failed to execute child process "/usr/lib/firefox" (Permission denied)

```

I've looked at all the articles on the forum for that error and haven't found a solution.  Someone suggested I chmod 755 the folder.  But this had no effect.

I am now at a loss, I seem to have hopelessly broken it!  As far as I can tell the firefox files are now in usr/bin/firefox/ and /usr/lib/firefox has the FF add-ons - is this right?

Anyways any help much appreciated.

Thanks

Kneewax

---

### Post by michy99 on 2009-08-09
Have you looked at this thread yet?

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by lovinglinux on 2009-08-09
Try this:

```
sudo rm /usr/bin/firefox
sudo cp /usr/bin/firefox.old /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.5.2 /usr/local/bin/firefox
```

This will restore the original /usr/bin/firefox, then create a link from firefox-3.5.2 to /usr/local/bin/firefox.

You shouldn't run commands without knowing what they do.

---

### Post by kneewax on 2009-08-10
Thanks, that got me back to 3.0.11 and working again!  I appreciate that and quite take the point about running code I don't understand.

So here is my question - if I want to get my current version of FF upgraded to 3.5 how do I do it.  I have masses of links, bookmarks etc that I just don't want to leave behind. Also I don't like haveing redundant programs left hanging about on my machine (tidy PC, Tidy mind....).

Also is it a problem that I am running Jaunty x64? IT has never caused me issues in the past, but I think I read somewherte that FF3.5 was an issue in this area?


BTW this is the HowTo I followed originally: [http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

Cheers

---

### Post by lovinglinux on 2009-08-10
> **kneewax said:**
> Thanks, that got me back to 3.0.11 and working again!  I appreciate that and quite take the point about running code I don't understand.

So here is my question - if I want to get my current version of FF upgraded to 3.5 how do I do it.  I have masses of links, bookmarks etc that I just don't want to leave behind. Also I don't like haveing redundant programs left hanging about on my machine (tidy PC, Tidy mind....).

Also is it a problem that I am running Jaunty x64? IT has never caused me issues in the past, but I think I read somewherte that FF3.5 was an issue in this area?


BTW this is the HowTo I followed originally: [http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

Cheers

I don't know much about 64bit but....

There are some tricks to upgrade FF 3.0 to 3.5 but I don't recommend. You should install FF 3.5 along with 3.0 to avoid troubles.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

