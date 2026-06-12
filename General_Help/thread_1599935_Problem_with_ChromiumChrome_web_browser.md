---
title: "Problem with Chromium/Chrome web browser"
date: 2010-10-18
forum: General Help
---

### Post by androidcupcake on 2010-10-18
Hi all..

All of a sudden Chromium browser stopped responding. When I click to open the browser, all I get is a "round" symbol and Chromium tries to load unsuccessfully. It does not oopen up whatsoever. It was working perfectly last night..

I tried uninstalling and reinstalling Chromium from Synaptic. I even downloaded the stable release of Google Chrome from the Google website. No luck! Google Chrome installed from the Google site does not even "try" to open up. 

All this out of the blue? 

What do I do next?

---

### Post by searchfgold6789 on 2010-10-18
I would see if one of the following work:

[LIST=1]
[*]Purging/reinstalling chromium. To do this open up a terminal, and type in:```
sudo apt-get purge --reinstall chromium
```
[*]Install bleachbit```
sudo apt-get install bleachbit
```and run it```
sudo bleachbit
```with all the options checked. This clears all of your temporary files.
[*]If those do not work, try running the web browser as root.```
sudo chromium
```. If that works post back and we will show you how to change chromium so that it belongs to you and not the root user.
[*]If none of those work, please run chromium from the terminal ```
chromium
``` and post what happens :)
[/LIST]
good luck,
search
P.S. It might be of use later if we knew what kind of Ubuntu you are using ...

---

### Post by viralmeme on 2010-10-18
> **androidcupcake said:**
> Hi all.. All of a sudden Chromium browser stopped responding .. What do I do next?
Delete the ~/.config/chromium directory in your home folder ..

---

### Post by searchfgold6789 on 2010-10-18
> **viralmeme said:**
> Delete the ~/.config/chromium directory in your home folder ..
You can do that by typing in the terminal ```
rm -r ~/.config/chromium
``` because it is a hidden folder.
It's automatically removed when you try my suggestion of purging chromium, probably.

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> I would see if one of the following work:

[LIST=1]
[*]Purging/reinstalling chromium. To do this open up a terminal, and type in:```
sudo apt-get purge --reinstall chromium
```
[*]Install bleachbit```
sudo apt-get install bleachbit
```and run it```
sudo bleachbit
```with all the options checked. This clears all of your temporary files.
[*]If those do not work, try running the web browser as root.```
sudo chromium
```. If that works post back and we will show you how to change chromium so that it belongs to you and not the root user.
[*]If none of those work, please run chromium from the terminal ```
chromium
``` and post what happens :)
[/LIST]
good luck,
search
P.S. It might be of use later if we knew what kind of Ubuntu you are using ...


Thank you! 

I am using Ubuntu 10.10.

Results: 

1. Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'chromium-bsu' instead of 'chromium'
Package chromium-bsu is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2. Had tried Bleachbit already. No luck! 

3. sudo chromium
sudo: chromium: command not found

4. sudo chromium
sudo: chromium: command not found

Chromium is listed under Applications > Internet as "Chromium web browser still.

---

### Post by praveenthivari on 2010-10-18
try to reinstall first..

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> You can do that by typing in the terminal ```
rm -r ~/.config/chromium
``` because it is a hidden folder.
It's automatically removed when you try my suggestion of purging chromium, probably.

Tried this one..

Initially it seemed to work. I got the Chromium startup screen asking if I wanted to import firefox settings and set as default, etc. 

On clicking "OK", Chromium tried to load, but ultimately didn't! :| I can see it on the taskbar saying "Starting Chromium", but does NOT actually start.. 

What next?

Thanks so far..

---

### Post by androidcupcake on 2010-10-18
> **praveenthivari said:**
> try to reinstall first..

Yup.. Done that, as mentioned in my first post. Does not seem to be working..

---

### Post by searchfgold6789 on 2010-10-18
Try suggestions 1, 3 and 4 and replace "chromium" with "chromium-browser". :) In suggestion 4 omit the sudo ... also remember that purge is different from remove.
ChromiumBSU is actually an arcade game...

---

### Post by ean5533 on 2010-10-18
> **androidcupcake said:**
> Thank you! 

I am using Ubuntu 10.10.

Results: 

1. Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'chromium-bsu' instead of 'chromium'
Package chromium-bsu is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2. Had tried Bleachbit already. No luck! 

3. sudo chromium
sudo: chromium: command not found

4. sudo chromium
sudo: chromium: command not found

Chromium is listed under Applications > Internet as "Chromium web browser still.

Do those same instructions again, but replace "chromium" with "chromium-browser". "chromium" is not the correct package name.

---

### Post by TBABill on 2010-10-18
Did you do any kind of system update last night or this morning? I had this happen, but it was after upgrading to 10.10. It installed the iced tea plugin, which conflicted with the Sun Java plugin. I removed the iced tea plugin and it came up fine. I doubt this is your issue, just throwing it out in case you installed anything involving java.

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> Try suggestions 1, 3 and 4 and replace "chromium" with "chromium-browser". :) In suggestion 4 omit the sudo ... also remember that purge is different from remove.
ChromiumBSU is actually an arcade game...

Results:

1. Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  chromium-browser* chromium-browser-inspector* chromium-codecs-ffmpeg*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 51.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159838 files and directories currently installed.)
Removing chromium-browser ...
Purging configuration files for chromium-browser ...
Removing chromium-codecs-ffmpeg ...
Removing chromium-browser-inspector ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-support .

3. sudo chromium-browser
sudo: chromium-browser: command not found

4. chromium
chromium: command not found

Thanks!

---

### Post by androidcupcake on 2010-10-18
> **TBABill said:**
> Did you do any kind of system update last night or this morning? I had this happen, but it was after upgrading to 10.10. It installed the iced tea plugin, which conflicted with the Sun Java plugin. I removed the iced tea plugin and it came up fine. I doubt this is your issue, just throwing it out in case you installed anything involving java.

Yes, I did update today. As far as I can recall, I didn't install anything Java related..

---

### Post by oregonbob on 2010-10-18
Bump

FYI: I am a longtime Google Chrome user, a chrome addict and my chrome on 10.04 has broken in a similar manner. I have spent numerous hours trying to fix it and never succeeded, including purge, delete config, delete /opt/google, etc.

Oddly I have a laptop with same config but different hardware, 10.04 and chrome. So far it has no problems.

---

### Post by ean5533 on 2010-10-18
> **oregonbob said:**
> Bump.

You don't need to bump a thread that's actively being posted to.

---

### Post by searchfgold6789 on 2010-10-18
Assuming that you tried suggestions 1, 3, and 4  in order, it doesn't look to me as if in suggestion one that apt-get reinstalled chromium-browser after purging it. Before trying 3 and 4 again, (replacing the "chromium" command I gave you with "chromium-browser") please reinstall chromium-browser:```
sudo apt-get install chromium-browser
```
Also post /var/log/dpkg.log here so we can see what upgrades you did :)

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> Assuming that you tried suggestions 1, 3, and 4  in order, it doesn't look to me as if in suggestion one that apt-get reinstalled chromium-browser after purging it. Before trying 3 and 4 again, please reinstall chromium-browser:```
sudo apt-get install chromium-browser
```

Yes, I did try 1, 3 and 4 in the order. 

Results: 

1. sudo apt-get install chromium-browser

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-inspector chromium-codecs-ffmpeg
Suggested packages:
  chromium-browser-l10n
The following NEW packages will be installed:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.8MB of archives.
After this operation, 51.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package chromium-browser-inspector.
(Reading database ... 159621 files and directories currently installed.)
Unpacking chromium-browser-inspector (from .../chromium-browser-inspector_6.0.472.63~r59945-0ubuntu2_all.deb) ...
Selecting previously deselected package chromium-codecs-ffmpeg.
Unpacking chromium-codecs-ffmpeg (from .../chromium-codecs-ffmpeg_0.6+svn20100904r58574+58998-0ubuntu1_i386.deb) ...
Selecting previously deselected package chromium-browser.
Unpacking chromium-browser (from .../chromium-browser_6.0.472.63~r59945-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up chromium-browser-inspector (6.0.472.63~r59945-0ubuntu2) ...
Setting up chromium-codecs-ffmpeg (0.6+svn20100904r58574+58998-0ubuntu1) ...
Setting up chromium-browser (6.0.472.63~r59945-0ubuntu2) ...

2. sudo chromium-browser

Attempting to load the system libmoon 
Segmentation fault

3. chromium

chromium: command not found

Thanks again! 

Something new in 2nd command this time.. Hope that throws some light..

---

### Post by androidcupcake on 2010-10-18
Correction to my previous post.

3rd command result: 

chromium-browser

Attempting to load the system libmoon 
Segmentation fault

---

### Post by searchfgold6789 on 2010-10-18
> **androidcupcake said:**
> Correction to my previous post.

3rd command result: 

chromium-browser

Attempting to load the system libmoon 
Segmentation fault
**AHA.**
Try removing and reinstalling libmoon.```
sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge chromium-browser
sudo apt-get install chromium-browser
```
Maybe it will work without you having to use the final two commands...

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> **AHA.**
Try removing and reinstalling libmoon.```
sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge chromium-browser
sudo apt-get install chromium-browser
```Maybe it will work without you having to use the final two commands...

Some improvement. 

After removing and reinstalling libmoon and with the "sudo chromium-browser", Chromium opens up beautifullt with the beautiful bluish title bar browser. 

But when I try opening Chrome from App > Internet > Chromium, I get the following error: "Your preferences cannot be read. Some features may be unavailable and changes to preferences won't be saved".

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> **AHA.**
Try removing and reinstalling libmoon.```
sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge chromium-browser
sudo apt-get install chromium-browser
```Maybe it will work without you having to use the final two commands...

I tried removing and reinstalling chromium too.. Same error when I open chromium directly from App > Internet OR Chromium-browser from Terminal. 

But works perfectly when I use the "sudo chromium-browser" command..

Thanks!

---

### Post by ean5533 on 2010-10-18
> **androidcupcake said:**
> I tried removing and reinstalling chromium too.. Same error when I open chromium directly from App > Internet OR Chromium-browser from Terminal. 

But works perfectly when I use the "sudo chromium-browser" command..

Thanks!

Well, when you run the program by using "sudo chromium-browser", what it's doing is running Chromium as user "root" instead of the user you're logged in as. The fact that it's working for root but not working for you makes me wonder if there's something wrong with your home directory, such as it being not writeable or something strange like that.

Unfortunately I don't know how to fix this problem. Hopefully someone else will.

---

### Post by androidcupcake on 2010-10-18
> **ean5533 said:**
> Well, when you run the program by using "sudo chromium-browser", what it's doing is running Chromium as user "root" instead of the user you're logged in as. The fact that it's working for root but not working for you makes me wonder if there's something wrong with your home directory, such as it being not writeable or something strange like that.

Unfortunately I don't know how to fix this problem. Hopefully someone else will.
Oh.. OK.. Thanks for the assistance so far mate.. Appreciate it.. 
I'll use Firefox until this gets fixed.. 

Cheers!

---

### Post by searchfgold6789 on 2010-10-18
> **androidcupcake said:**
> Some improvement. 

After removing and reinstalling libmoon and with the "sudo chromium-browser", Chromium opens up beautifullt with the beautiful bluish title bar browser. 

But when I try opening Chrome from App > Internet > Chromium, I get the following error: "Your preferences cannot be read. Some features may be unavailable and changes to preferences won't be saved".
```
sudo chown -r (username) /usr/lib/chromium-browser/
sudo chown -r (username) ~/.config/
sudo chown -r (username) ~/.cache/

```in terminal will probably fix your problem.

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> ```
sudo chown -r (username) /usr/lib/chromium-browser/
sudo chown -r (username) ~/.config/
sudo chown -r (username) ~/.cache/

```in terminal will probably fix your problem.
Errors encountered after running the commands: 

chromium-browser

[7162:7162:5196133419:FATAL:chrome/browser/zygote_host_linux.cc(123)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted

sudo chromium-browser
[7169:7169:5228324625:FATAL:chrome/browser/zygote_host_linux.cc(123)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted

---

### Post by searchfgold6789 on 2010-10-18
```
 sudo chown root /usr/lib/chromium-browser/
```

---

### Post by androidcupcake on 2010-10-18
> **searchfgold6789 said:**
> ```
 sudo chown root /usr/lib/chromium-browser/
```
after running the above command and "sudo chromium-browser" on Terminal I receive the following: 

sudo chromium-browser
[7230:7230:5601255958:FATAL:chrome/browser/zygote_host_linux.cc(123)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted

---

### Post by searchfgold6789 on 2010-10-18
```
sudo chown -r root /usr/lib/chromium-browser/
```
then attempt to just open chromium as usual.

---

### Post by androidcupcake on 2010-10-19
> **searchfgold6789 said:**
> ```
sudo chown -r root /usr/lib/chromium-browser/
```
then attempt to just open chromium as usual.
I am currently at work. Shall try this on getting home and update..

---

### Post by androidcupcake on 2010-10-19
No luck!!

---

### Post by searchfgold6789 on 2010-10-19
In post #21, did you omit the last two commands, or did you run all of them?
I think that running all of them again, if you did not before, may help you.
Because I remember saying that it might work without reinstalling Chrome.

---

### Post by androidcupcake on 2010-10-19
> **searchfgold6789 said:**
> In post #21, did you omit the last two commands, or did you run all of them?
I think that running all of them again, if you did not before, may help you.
Because I remember saying that it might work without reinstalling Chrome.
I did run all the 4 commands.. I tried it all over again as well.. It does work, but with the error message I previously mentioned.. Chromium opens up only as root if I use the sudo command..

---

### Post by searchfgold6789 on 2010-10-19
Never mind!
I messed up that command. Instead of typing ```
chown -r root /usr/lib/chromium-browser
```It should have been ```
sudo chown -R root /usr/lib/chromium-browser
```
My bad.
Hope it gets you somewhere.

---

### Post by androidcupcake on 2010-10-19
> **searchfgold6789 said:**
> Never mind!
I messed up that command. Instead of typing ```
chown -r root /usr/lib/chromium-browser
```It should have been ```
sudo chown -R root /usr/lib/chromium-browser
```
My bad.
Hope it gets you somewhere.
I did use "R". However after running the above command and trying to open Chromium, via Terminal, throws the following error:


[2449:2449:695023848:FATAL:chrome/browser/zygote_host_linux.cc(123)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted

---

### Post by Anutesyn on 2010-10-19
> **praveenthivari said:**
> try to reinstall first..

This is what I was going to suggest.

---

### Post by praveenthivari on 2010-10-19
watever method u hv used to install, undo tht. 
Purge ppa of chromium (U can use 'ubuntu tweak')  or if u hv not added chromium ppa ( i.e installed directly from software centre) just uninstall it.

Use 'ubuntu tweak' to clear all config files and all related packages from 'Package Cleaner'. then again try to install.
(Dont know if this has been suggested earlier, didn't go through all comments above)

---

### Post by brouwser on 2010-10-20
Hi all,
Thanks for your help. I had the same problem. These instructions from earlier replies in this thread solved it on my computer:
sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge chromium-browser
sudo apt-get install chromium-browser
Cheers.

---

### Post by searchfgold6789 on 2010-10-20
Next try ```

sudo mkdir /var/run/chrome-sandbox
```

---

### Post by mellowb on 2010-10-21
Thank you Brouwser, your suggestion worked for me, but, since I using google-chrome, the commands I used were

sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge google-chrome-stable
sudo apt-get install google-chrome-stable

---

### Post by Erin on 2010-10-21
Hello,

Try running and posting the output of the following:

"ls -al /usr/lib/chromium-browser/chromium-browser-sandbox"

Erin

---

### Post by searchfgold6789 on 2010-10-21
> **searchfgold6789 said:**
> Next try ```

sudo mkdir /var/run/chrome-sandbox
```
I say this because when you did your last upgrade, /var/run/ was erased.
There should have been a patch for this though.
Anyway try it and post back if it works.

---

### Post by dundacil on 2010-10-24
> **mellowb said:**
> Thank you Brouwser, your suggestion worked for me, but, since I using google-chrome, the commands I used were

sudo apt-get remove --purge libmoon
sudo apt-get install libmoon
sudo apt-get remove --purge google-chrome-stable
sudo apt-get install google-chrome-stable

Well, the culprit could be the moonlight plugin(s), rather than moonlib itself? The command sudo apt-get remove --purge libmoon removes both moonlib and the plugins, whereas sudo apt-get install libmoon reinstalls only libmoon without plugins. In my case, I too managed to start chrome after this set of instruction, but after reinstalling the plugins, chrome stopped working.

---

### Post by gregorydillon on 2010-10-27
> **TBABill said:**
> Did you do any kind of system update last night or this morning? I had this happen, but it was after upgrading to 10.10. It installed the iced tea plugin, which conflicted with the Sun Java plugin. I removed the iced tea plugin and it came up fine. I doubt this is your issue, just throwing it out in case you installed anything involving java.


Big thank you.   I experience this same problem.    I used the search function and found this thread.   Read this post, and thought that sounds like what happened to me.   I confirmed I had the iced tea plugin, I removed it and life is good with Chromium again.   Thanks for helping me get the computer running correctly.

---

### Post by MSXManiac on 2011-02-20
> **gregorydillon said:**
> Big thank you.   I experience this same problem.    I used the search function and found this thread.   Read this post, and thought that sounds like what happened to me.   I confirmed I had the iced tea plugin, I removed it and life is good with Chromium again.   Thanks for helping me get the computer running correctly.

I'm too! Finally! But the message for a long time made me believe it was a problem with the moonlight, as it always had the icedtea installed and never had problems until installing libmoon!
Thanks for your help!

---

### Post by enkrypt3d on 2011-02-20
[http://www.google.com/chrome?platform=linux&hl=en](http://www.google.com/chrome?platform=linux&hl=en)

Just use this link to install it ...... you dont need to use the CLI for this.

---

