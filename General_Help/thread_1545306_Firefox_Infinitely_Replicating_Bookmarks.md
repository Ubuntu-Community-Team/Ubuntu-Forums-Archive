---
title: "Firefox Infinitely Replicating Bookmarks"
date: 2010-08-03
forum: General Help
---

### Post by xondak on 2010-08-03
So I was playing RollerCoaster Tycoon 2 in a WINE Virtual Desktop when I went to check my email. I launched Firefox and suddenly my bookmarks started to replicate and haven't stopped. Any tips? I've recorded this happening. Link here: [http://www.youtube.com/watch?v=2lyiaELx__E](http://www.youtube.com/watch?v=2lyiaELx__E)

---

### Post by mendhak on 2010-08-03
Hi, try restarting the machine (so that there are no instances of Firefox present), then try 

firefox -safe-mode

To get it into safe mode.  Is the problem still happening there? Can you right click anywhere in the toolbar area and uncheck the bookmark tab?

---

### Post by xondak on 2010-08-03
I tried running it in safe mode and that did not fix the problem. Would uninstalling/reinstalling the program work? (The problem is I don't want to lose my other bookmarks)

---

### Post by lovinglinux on 2010-08-03
> **xondak said:**
> I tried running it in safe mode and that did not fix the problem. Would uninstalling/reinstalling the program work? (The problem is I don't want to lose my other bookmarks)

Create a new profile using the Profile Manager. To do that, close Firefox then start it from terminal using  the command below:

```
firefox -P
```

Create the new profile and test it. If it works without problems, then you can restore your bookmarks from a backup (see [Backups](http://firefox-tutorials.blogspot.com/2010/05/backups.html) and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html))

BTW, this is the most interesting/bizarre Firefox problem I ever saw. Never saw something like that before.

---

### Post by xondak on 2010-08-04
I've tried firefox -p and tried with root privileges and I receive this error:

```
run-mozilla.sh: Cannot execute /usr/lib/firefox-3.6.8/firefox-bin.pure.
```

No idea what to do now.

---

### Post by lovinglinux on 2010-08-04
> **xondak said:**
> I've tried firefox -p and tried with root privileges and I receive this error:

```
run-mozilla.sh: Cannot execute /usr/lib/firefox-3.6.8/firefox-bin.pure.
```

No idea what to do now.

Don't start it with root privileges, specially sudo, which would cause all sorts of problems. Run the following command (without changes) to fix any permissions issue you might have after starting firefox with root privileges:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Then completely purge firefox and install it again. you won't lose your bookmarks.

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

Then start the profile manager and create a new profile:

```
firefox -P
```

---

### Post by xondak on 2010-08-04
I tried your suggestion and it hasn't fixed the problem.

I get the same error as before. :(

---

### Post by lovinglinux on 2010-08-04
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**2 - System Info**

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

### Post by xondak on 2010-08-04
```
Ubuntu Architecture

Linux xondak-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

akirad.list
akirad.list.distUpgrade
akirad.list.save
banshee-team-ppa-lucid.list
banshee-team-ppa-lucid.list.save
bean123ch-burg-lucid.list
c-korn-vlc-lucid.list
c-korn-vlc-lucid.list.save
falk-t-j-qtsixa-karmic.list
falk-t-j-qtsixa-karmic.list.distUpgrade
falk-t-j-qtsixa-karmic.list.save
fontanon-wiican-lucid.list
fontanon-wiican-lucid.list.save
glennric-dolphin-emu-karmic.list
glennric-dolphin-emu-karmic.list.distUpgrade
glennric-dolphin-emu-karmic.list.save
gm-notify-maintainers-ppa-lucid.list
gm-notify-maintainers-ppa-lucid.list.save
google-chrome.list
google-chrome.list.save
gstreamer-developers-ppa-lucid.list
gstreamer-developers-ppa-lucid.list.save
mozillateam-firefox-stable-lucid.list
mozillateam-firefox-stable-lucid.list.save
ubuntu-boot-ppa-karmic.list
ubuntu-boot-ppa-karmic.list.distUpgrade
ubuntu-boot-ppa-karmic.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save
wiicanteam-ppa-lucid.list
wiicanteam-ppa-lucid.list.save

```

The About Firefox menu only has the version number (3.6.8 ) and the Mozilla Firefox for Ubuntu Canonical - 1.0 

Just noticing some of the stuff in the output here... I did not delete anything yet it says that it can't find the directory. Do you think WINE might have removed something?

---

### Post by lovinglinux on 2010-08-05
Try this:

Go to Software Sources, then disable ubuntu-firefox-stable ppa then:

```
sudo apt-get purge firefox
sudo apt-get clean
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install --reinstall ubufox
sudo apt-get install --reinstall xulrunner-1.9.2
sudo apt-get install --reinstall libsqlite3-0

```


Do you have Xmarks or Firefox Sync or any other bookmark sync extension installed?


> **xondak said:**
> The About Firefox menu only has the version number (3.6.8 ) and the Mozilla Firefox for Ubuntu Canonical - 1.0 

Increase the window height.

> **xondak said:**
> Just noticing some of the stuff in the output here... I did not delete anything yet it says that it can't find the directory. Do you think WINE might have removed something?

No. That is expected. I don't see anything wrong with your report.

---

### Post by lovinglinux on 2010-08-05
Edit: See previous post.

---

### Post by xondak on 2010-08-05
I don't have either of those those extensions installed.

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8
```

And your last codes still hasn't fixed the issue.

---

### Post by lovinglinux on 2010-08-05
> **xondak said:**
> I don't have either of those those extensions installed.

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8
```

And your last codes still hasn't fixed the issue.

Create a new Ubuntu test user, login with that account and check if Firefox replicates the bookmarks too.

---

### Post by xondak on 2010-08-05
I created a new Ubuntu user called test. I opened Firefox and added a few bookmarks, the program was much more responsive and the bookmarks did not replicate.

---

### Post by lovinglinux on 2010-08-05
> **xondak said:**
> I created a new Ubuntu user called test. I opened Firefox and added a few bookmarks, the program was much more responsive and the bookmarks did not replicate.

So, since you have already created a new Firefox user profile and it didn't help (are you sure?), have reinstalled firefox, xulrunner, and libsqlite3-0, don't have any sync extension, then I would guess you have some issue with your gnome user settings that is affecting Firefox.

I would start by deleting ~/.wine. This will remove all software you have installed using Wine tho.

---

### Post by xondak on 2010-08-05
> **lovinglinux said:**
> So, since you have already created a new Firefox user profile and it didn't help (are you sure?)

I created a new OS user, not a new Firefox profile. Every time I try to make a new profile I get that error.

> I would start by deleting ~/.wine. This will remove all software you have installed using Wine tho.

I'm wondering why this would help.

---

### Post by lovinglinux on 2010-08-05
> **xondak said:**
> I created a new OS user, not a new Firefox profile. Every time I try to make a new profile I get that error.

I'm wondering why this would help.

Sorry, my mistake. 

Close Firefox and try this then:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox_old
```

Start Firefox.

---

### Post by xondak on 2010-08-05
That worked! Cool! Thank you so much. :)

P.S. I love your avatar. Battlestar ROCKS.

---

### Post by lovinglinux on 2010-08-05
> **xondak said:**
> That worked! Cool! Thank you so much. :)

P.S. I love your avatar. Battlestar ROCKS.

You are welcome. See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html) to get some of your FF things back.

---

### Post by xondak on 2010-08-05
I just tried to add some bookmarks to the bar and I got this error:

```
ASSERT: parent node must have _DOMElement set
Stack Trace: 
0:PMV_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],1)
1:removeItem(6)
2:PRIT_doTransaction()
3:doTransaction()
4:PAT_commit(false)
5:PAT_doTransaction()
6:doTransaction([xpconnect wrapped nsITransaction])
7:placesTxn_doTransaction([xpconnect wrapped nsITransaction])
8:doTransaction([xpconnect wrapped nsITransaction])
9:PC__removeRowsFromBookmarks(Remove Selection)
10:PC_remove(Remove Selection)
11:PC_doCommand(placesCmd_delete)
12:doCommand(placesCmd_delete)
13:goDoPlacesCommand(placesCmd_delete)
14:oncommand([object XULCommandEvent])

```

---

### Post by lovinglinux on 2010-08-05
> **xondak said:**
> I just tried to add some bookmarks to the bar and I got this error:

```
ASSERT: parent node must have _DOMElement set
Stack Trace: 
0:PMV_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],1)
1:removeItem(6)
2:PRIT_doTransaction()
3:doTransaction()
4:PAT_commit(false)
5:PAT_doTransaction()
6:doTransaction([xpconnect wrapped nsITransaction])
7:placesTxn_doTransaction([xpconnect wrapped nsITransaction])
8:doTransaction([xpconnect wrapped nsITransaction])
9:PC__removeRowsFromBookmarks(Remove Selection)
10:PC_remove(Remove Selection)
11:PC_doCommand(placesCmd_delete)
12:doCommand(placesCmd_delete)
13:goDoPlacesCommand(placesCmd_delete)
14:oncommand([object XULCommandEvent])

```

Where did you get this error ? On the terminal output, as a Firefox alert or the system message bubble?

The bar you mean Firefox bookmarks toolbar or the Ubuntu panel?

Try to disable Ubuntu Firefox Modifications extension.

---

