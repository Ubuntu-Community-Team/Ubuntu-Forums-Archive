---
title: "Firefox problem"
date: 2010-08-01
forum: General Help
---

### Post by atravnic on 2010-08-01
I know, I know, you folks will hand me my head for posting what may well be a non-Ubuntu questions. But since I don't know if it's an Ubuntu or a Firefox problem, I decided to bravely stick my neck out. The problem: suddenly, when I came back from vacation and fired up my laptop, my applications won't load. The Firefox homepage loads, but when try to launch, say, Huffington, or Yahoo, or CNet, it churns away endlessly and nothing ever happens. I'm running Firefox 3, Beta 5 and Ubuntu 8.04. 

Please let me live.         ...Fred

---

### Post by borth92 on 2010-08-02
reinstall the newest firefox since u have an old one anyways and see if it gets working

---

### Post by themusicalduck on 2010-08-02
Might be worth making a new firefox profile to see if it fixes it.

Open your home folder and press ctrl+h, then look for the .mozilla folder and rename it to .mozillaold then reload Firefox.

Your bookmarks and settings will appear to have gone, but as long as you have just renamed it you can always change it back and revert it back.

---

### Post by lovinglinux on 2010-08-02
There is nothing wrong about posting Firefox questions and threads. I would be banned already if it wasn't allowed :)

Anyway, if the pages keep loading and never appear. Disable ipv6.

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For future reference, see [Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")


> **themusicalduck said:**
> Might be worth making a new firefox profile to see if it fixes it.

Open your home folder and press ctrl+h, then look for the .mozilla folder and rename it to .mozillaold then reload Firefox.

Your bookmarks and settings will appear to have gone, but as long as you have just renamed it you can always change it back and revert it back.

Instead of renaming Mozilla, I like to recommend creating a new profile using the profile manager.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by atravnic on 2010-08-02
> **borth92 said:**
> reinstall the newest firefox since u have an old one anyways and see if it gets working

Makes sense. Except that I've tried to update Firefox--and here is full disclosure: I'm not an industrial strength Linux user, :(, I'm actually way down on the totem pole--and haven't been able to figure out how to do it. Can you point me? Thanks bunches, in advance even.   ...Fred

---

### Post by lovinglinux on 2010-08-02
> **atravnic said:**
> Makes sense. Except that I've tried to update Firefox--and here is full disclosure: I'm not an industrial strength Linux user, :(, I'm actually way down on the totem pole--and haven't been able to figure out how to do it. Can you point me? Thanks bunches, in advance even.   ...Fred

Go to "Applications > Accessories > Terminal" and paste the command below and run it:

```
sudo apt-get install --reinstall firefox
```

Nevertheless, I don't think this will solve anything. In your first post you say that Firefox open and the Firefox homepage loads, so I'm assuming you don't have any problems with applications starting. Re-installing Firefox probably won't help. But you also said "my applications won't load.." and "...say, Huffington, or Yahoo, or CNet, it churns away endlessly and nothing ever happens." I'm not sure what you mean. Are you saying that after Firefox starts, you try to visit Yahoo page and it keeps loading? If that is the case, see my previous post for solution. If not, then please be more descriptive about your problem.

---

### Post by atravnic on 2010-08-05
> **borth92 said:**
> reinstall the newest firefox since u have an old one anyways and see if it gets working

I did a re-install, but it re-installed the version I've been using: Firefox 3, Beta 5. What do I need to do to get the latest release? Thank you so much for your help.   ...Fred

---

### Post by Don Barzini on 2010-08-05
> **atravnic said:**
> What do I need to do to get the latest release? Thank you so much for your help.   ...Fred


Add the Mozilla repository. In a terminal type....

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```

Then run an update and upgrade....

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by atravnic on 2010-08-05
> **themusicalduck said:**
> Might be worth making a new firefox profile to see if it fixes it.

Open your home folder and press ctrl+h, then look for the .mozilla folder and rename it to .mozillaold then reload Firefox.

Your bookmarks and settings will appear to have gone, but as long as you have just renamed it you can always change it back and revert it back.

I used LovingLinux's suggestion to disable IPv6 and it worked. Question: Is there any value in making a new Firefox profile now or should I leave well enough alone. Thanks    ...Fred

---

### Post by atravnic on 2010-08-05
> **lovinglinux said:**
> There is nothing wrong about posting Firefox questions and threads. I would be banned already if it wasn't allowed :)

Anyway, if the pages keep loading and never appear. Disable ipv6.

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For future reference, see [Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")




Instead of renaming Mozilla, I like to recommend creating a new profile using the profile manager.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

I used your 4 step method to disable IPv6, and TARA, it worked. Thank you so much! (Sure glad they haven't kicked out yet :D.)

But you mentioned something else that I'd like to ask you about. I looked for my connection settings but couldn't find them (looked in Firefox and in Ubuntu Admin Network and Network Tools). I also couldn't find how to disable IPv6 in Preferences. Maybe none of this really matters now, I'm just curious. Thanks again     ...Fred

---

### Post by atravnic on 2010-08-05
> **Don Barzini said:**
> Add the Mozilla repository. In a terminal type....

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```

Then run an update and upgrade....

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

.............................................................

Here is what I got:
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
[sudo] password for atravnic: 
sudo: add-apt-repository: command not found

Sorry to have to keep asking, but I'm rather helpless when it comes to Linux code.     ...Fred

---

### Post by lovinglinux on 2010-08-06
> **atravnic said:**
> I used your 4 step method to disable IPv6, and TARA, it worked. Thank you so much! (Sure glad they haven't kicked out yet :D.)

But you mentioned something else that I'd like to ask you about. I looked for my connection settings but couldn't find them (looked in Firefox and in Ubuntu Admin Network and Network Tools). I also couldn't find how to disable IPv6 in Preferences. Maybe none of this really matters now, I'm just curious. Thanks again     ...Fred

Open Firefox, type **about[noparse]:[/noparse]config** in the address bar and hit enter. You will see a list of preferences and a filter field. Type **network.dns.disableIPv6** in the filter and you will see that only that preference will be displayed. Double-click on it to set it to false.

More about how to change preferences: [http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)

> **Don Barzini said:**
> Add the Mozilla repository. In a terminal type....

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```

That doesn't work in Ubuntu 8.04. That feature is only available in Ubuntu Karmic or superior. Besides, Firefox 3.6.8 is already in Hardy repositories, so there is no need to use a PPA.

@atravnic

I don't know why you are still using Firefox 3 beta 5. As explained above, you should have already Firefox 3.6.8, which is a lot faster than Firefox 3.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be locates at the bottom of the info dialog:

[IMG]http://lh5.ggpht.com/_EPRFmO0pKhs/TFi0kqRSPaI/AAAAAAAAAik/G3M3J5mmDOo/s400/Firefox_Version.jpg[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

