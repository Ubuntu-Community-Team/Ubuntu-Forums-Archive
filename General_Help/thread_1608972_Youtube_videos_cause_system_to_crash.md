---
title: "Youtube videos cause system to crash?"
date: 2010-10-29
forum: General Help
---

### Post by thebarisaxkid on 2010-10-29
I have problem. (duh)

When I was watching a youtube video,  the video froze along with the whole system.  (I can't move mouse or use keyboard.)  Then the Caps Lock Light and Scroll Lock light start blinking.  (The num lock is turned of by default for some reason).

This has happened multiple times before.  I noticed that it is happening more often in 10.10 than 10.04.

Anyone else with this problem or an answer?

and what do the blinking lights mean?

---

### Post by darkstaar on 2010-10-29
Are you running the Open Source Flash plugin or the Flash from Adobe?

32 bit or 64 bit?

---

### Post by lovinglinux on 2010-10-29
[FF] Code: Firefox Report

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


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
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by thebarisaxkid on 2010-10-29
> **darkstaar said:**
> Are you running the Open Source Flash plugin or the Flash from Adobe?

32 bit or 64 bit?

32 bit.  I installed all codecs and such by tping the code:

sudo apt-get install ubuntu-restricted-extras.

I am using Google Chrome, btw.

---

### Post by thebarisaxkid on 2010-10-29
@lovinglinux I am using Google Chrome

---

### Post by darkstaar on 2010-10-29
May I suggest that you try the new Flash Player "Square" from Adobe?

First, remove **flashplugin-installer** (this is important) through the Synaptic Package Manager. Then grab the new Flash Player from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and place the contents of the archive (libflashplayer.so) into your *.mozilla/plugins* folder.

If you don't have such a folder, simply make one.


> **thebarisaxkid said:**
> I am using Google Chrome

No matter. Chrome will use this plugin as well. However you might want to try YouTube in Firefox to make sure that you're having the same issues.

If your problem persists with the new Flash or isn't an issue at all in Firefox, I'd suggest that perhaps Flash isn't the problem. In any event, you can always revert to the flashplugin-installer simply by reversing the steps above.

---

### Post by uRock on 2010-10-29
How much RAM do you have? 

Did you create a swap partition when you installed ubuntu?

---

### Post by thebarisaxkid on 2010-10-30
> **darkstaar said:**
> May I suggest that you try the new Flash Player "Square" from Adobe?

First, remove **flashplugin-installer** (this is important) through the Synaptic Package Manager. Then grab the new Flash Player from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and place the contents of the archive (libflashplayer.so) into your *.mozilla/plugins* folder.

If you don't have such a folder, simply make one.




No matter. Chrome will use this plugin as well. However you might want to try YouTube in Firefox to make sure that you're having the same issues.

If your problem persists with the new Flash or isn't an issue at all in Firefox, I'd suggest that perhaps Flash isn't the problem. In any event, you can always revert to the flashplugin-installer simply by reversing the steps above.

Thanks, I'll give it a shot in the morning.

---

### Post by thebarisaxkid on 2010-10-30
> **uRock said:**
> How much RAM do you have? 

Did you create a swap partition when you installed ubuntu?

I have 2gb of ram.  I made a 2.5gb swap part.

---

### Post by thebarisaxkid on 2010-10-30
> **darkstaar said:**
> May I suggest that you try the new Flash Player "Square" from Adobe?

First, remove **flashplugin-installer** (this is important) through the Synaptic Package Manager. Then grab the new Flash Player from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and place the contents of the archive (libflashplayer.so) into your *.mozilla/plugins* folder.

I removed the package and downloaded the new flash plugin.  When I enter the .mozilla folder, I see "Firefox" and "Extentions." Now I have to make the "plugins" folder, right?  And when I move the flashplayer_square_p2_32bit_linux092710.tar.gz, how do I do this?  I'm fairly certain that it is more complex than a drag and drop.  Do I have to extract the libflashplayer.so file?
If you can give the codes that would help a lot.

---

### Post by darkstaar on 2010-10-30
**flashplayer_square_p2_32bit_linux092710.tar.gz** is a compressed file as a ZIP file would be. Buried somewhere in there is a file named **libflashplayer.so**. It's the only file but it may be buried in a subfolder or two. Just drag and drop that .so file into .mozilla/plugins.

EDIT: You can open that .gz file by clicking it in Nautilus (the file manager) as you would a .zip file in Windows Explorer.

Again, make certain that you've removed **flashplugin-installer**.

---

### Post by thebarisaxkid on 2010-10-30
It's Morning!

So I did that and now I am going to test it out.

That seemed easier than it should have been.

---

### Post by thebarisaxkid on 2010-10-30
Hmm, It happened again, but the video was paused.

It may not necessarily be a problem with flash, but doesn't mean it isn't the problem.

At the time of the crash, I was running Google (with video open, but paused) virtualbox with Arch on it, an update manager(minimized) and cairo dock.  (I also have compiz effects enabled)

One possibility that I can think ofis the duration that I leave google chrome open.

---

### Post by thebarisaxkid on 2010-10-30
Wait...
Do I have to drop the new flashplayer in a google chrome folder?  I was "testing it out" with Google Chrome instead of firefox.

If so, where is this folder found?

BTW, I opened up firefox (after the crash) for the first time since I added the new flashplayer, and before it opened, a popup window came up and it had a loading bar, as if it was loading something, but it closed too quickly for me to read.

---

### Post by thebarisaxkid on 2010-10-31
Apparently, flash is not the problem.  See my new thread:

[http://ubuntuforums.org/showthread.php?t=1610292](http://ubuntuforums.org/showthread.php?t=1610292)

---

