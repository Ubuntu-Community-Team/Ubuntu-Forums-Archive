---
title: "Update Software Center is gone on 11.10"
date: 2012-01-03
forum: General Help
---

### Post by davidafranklin on 2012-01-03
Hello, I messed up something with my software Center/Update manager  (11.10). I was trying to work on sources and install repositories to  make Google Chromium working.
Long story short, the update manager does not launch anymore and I see I have pending updates to install.

I get the following error message: "Task cannot be monitored or  controlled. The connection to the daemon was lost. Most likely the  background daemon crashed."

When I click on Details, I get: "It seems that the daemon died".

I there a way to repair or reinstall the software center?

When I click on it, it comes up like for 1/10 seconds and goes away.

Thanks!
David

---

### Post by cogier on 2012-01-03
I would try loading **Synaptic Package Manager** from the **Software Center**. Then run it. Search for Update Manager and try reinstalling it. See attached.

If you need more help let us know.

---

### Post by davidafranklin on 2012-01-03
I cannot launch synaptic manager either. The window actually comes up and disappears after 1/10 s.

---

### Post by davidafranklin on 2012-01-03
I have an update. I was able to access the "Sources software" and enable all the sources from the "other" tab. Then I got my update manager back.

I have only error messages from a Google Chromium that cannot be installed. Is there a way to cancel the update so I do not get the message constantly? Even if I uncheck it on the update manager, it keps coming back.

Thanks

---

### Post by cogier on 2012-01-03
Can you let us have a screen shot of the "Other software" page

---

### Post by davidafranklin on 2012-01-03
here you go

---

### Post by cogier on 2012-01-03
The uploaded picture seems corrupt.....

---

### Post by cogier on 2012-01-03
OK got the picture now.

What are the "Independent" items? If you are not sure disable them. I doubt that you need the items with "Source code" either.

Try disabling them all the above items and see if that helps. You can always turn them back on if necessary.

---

### Post by davidafranklin on 2012-01-03
I removed the sources you mentioned. The update software seems working fine but Google Chromium "recommended update" keeps coming (see attached) and I cannot install it so I just want to forget about chromium for now.

---

### Post by cogier on 2012-01-03
I think you already have Chromium installed which is why it is trying to update it.

You need to go into the **Software Center** and **Remove** Chromium.

That should stop the update request

---

### Post by davidafranklin on 2012-01-03
I do not have it installed. I have tried several times but it did not work. I only downloaded the install files. Maybe some files are in a install/temp folder and try to install constantly

---

### Post by cogier on 2012-01-03
Does the **Software Center** show Chromium as installed?

If not close the Software Center and run the following in **Terminal**

*sudo apt-get install -f*

Then

*sudo apt-get clean*

See if that helps (a reboot might be a good idea at this stage)

---

### Post by davidafranklin on 2012-01-03
I tried the *sudo apt-get clean *and reboot.

Chromium still keeps coming out for an install

---

### Post by cogier on 2012-01-03
Can anybody else suggest anything, I am out of ideas.

---

### Post by spacecheck on 2012-01-03
Make sure chromium is not running (nor any package managers, etc.), then try
sudo apt-get purge chromium
see if that removes it completely

Good luck!

---

### Post by davidafranklin on 2012-01-03
I tried that. Chromium still wants to be installed. Here the results of the terminal:

david@david-Satellite-M115:~$ sudo apt-get purge chromium
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'chromium' can't be removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 chromium-browser-l10n : Depends: chromium-browser (= 15.0.874.106~r107270-0ubuntu0.11.10.1) but it is not going to be installed
 chromium-codecs-ffmpeg : Depends: chromium-browser (>= 4.0.203.0~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
david@david-Satellite-M115:~$

---

### Post by davidafranklin on 2012-01-03
I just ran again the udpate manager (see attached). I have now several other updates Chromium included. When I uncheck CHromium, it does not let me install the other things.

---

### Post by cortman on 2012-01-03
> **davidafranklin said:**
> I just ran again the udpate manager (see attached). I have now several other updates Chromium included. When I uncheck CHromium, it does not let me install the other things.

See post #9 of [this thread.]("http://ubuntuforums.org/showthread.php?t=1901225")

---

### Post by davidafranklin on 2012-01-03
I tried Poste #9, deleted all the eclipse file but then cannot installe the "computer janitor" I gues because of the same issues. I get error message: "The following packages have unmet dependencies:

chromium-browser-l10n: Depends: chromium-browser (= 15.0.874.106~r107270-0ubuntu0.11.10.1) but it is not installed
chromium-codecs-ffmpeg: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
                        Depends: chromium-browser (>= 4.0.203.0~) but it is not installed"


I did reboot as well without runnint computer janitor and nothing was fixed

---

### Post by davidafranklin on 2012-01-03
I did everything again and miracle, seems to work.
Thanks!

I guess nobody has a true fix to install chomium on 11.10 ?

---

### Post by cortman on 2012-01-03
> **davidafranklin said:**
> I did everything again and miracle, seems to work.
Thanks!

I guess nobody has a true fix to install chomium on 11.10 ?

You say the "delete all chromium files" thing worked?

I've installed Chromium on a couple different computers; in fact I suspect that's what I'm using to type this up. Never gave me any trouble.

---

### Post by davidafranklin on 2012-01-03
Once I deleted Eclipse and ran the commands, I was able to install the updates and get rid of the chromium notification. Now Chromium does not show up anymore.

I am wondering if I should try to reinstall. I am afraid I will get the same error messages.

---

### Post by cortman on 2012-01-03
> **davidafranklin said:**
> Once I deleted Eclipse and ran the commands, I was able to install the updates and get rid of the chromium notification. Now Chromium does not show up anymore.

I am wondering if I should try to reinstall. I am afraid I will get the same error messages.

You meant deleted chromium, right? I made the same typo in my post...

If you want to reinstall, use 

```
sudo apt-get install chromium-browser
```

---

### Post by davidafranklin on 2012-01-03
I meant I was trying to install Chromium an this is how I messed everything. I have now have everything back to normal (without chromium) but I am wondering if it could work now as there are many posts of people complaining they cannot get chromium working with 11.10.

---

### Post by cortman on 2012-01-03
> **davidafranklin said:**
> I meant I was trying to install Chromium an this is how I messed everything. I have now have everything back to normal (without chromium) but I am wondering if it could work now as there are many posts of people complaining they cannot get chromium working with 11.10.

I'm using the actual Google Chrome. I downloaded the .deb packages from Google's website and installed them with dpkg. If you need help installing let us know!

---

### Post by davidafranklin on 2012-01-04
If you can help it would be great. When I tried to install thru the update center it did not work, Packages were broken and I was missing something.

---

### Post by cortman on 2012-01-04
Sure, go to [https://www.google.com/chrome?platform=linux&hl=en]("https://www.google.com/chrome?platform=linux&hl=en") and download the .deb package that corresponds to your OS architecture (32, 64 bit).
It'll save it in your "Downloads" folder. You may be able to simply right click and select "install", but a foolproof way that'll work with any system is to use the terminal.
Open it and copy/paste the following-

```
sudo dpkg -i ~/Downloads/google-chrome*
```

And that should do it for you.

---

### Post by davidafranklin on 2012-01-04
I wish it would be that simple. It did not work.
Here is the message I get after running the install from the Terminal :

david@david-Satellite-M115:~$ sudo dpkg -i ~/Downloads/google-chrome*
Selecting previously deselected package google-chrome-stable.
(Reading database ... 173144 files and directories currently installed.)
Unpacking google-chrome-stable (from .../google-chrome-stable_current_i386.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable
david@david-Satellite-M115:~$ 

Also, now, I have an update in my Update Center that wil not install. It says: "The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f" and under DETAILS it says: "The following packages have unmet dependencies:

google-chrome-stable: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
                      Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
                      Depends: libcurl3 but it is not installed
"

---

### Post by davidafranklin on 2012-01-04
Actually,
Although I got the error message for Chromium, it has been installed and I can run it fine Thanks for that.
Now I just have the remainin error message in the Update Center

---

### Post by cortman on 2012-01-04
Did you run 

```
sudo apt-get install -f
```

? This should fix the broken packages. After that run

```
sudo apt-get update && upgrade
```

If you still are getting error messages, run

```
cat /etc/apt/sources.list
```

and paste the output here. I'm not sure what else is going wrong.

---

### Post by davidafranklin on 2012-01-04
Here is what I did just before your reply:

I ran the Janitor and removed everything. Now seems fine. After a reboot, things remained fine.

---

### Post by cortman on 2012-01-04
> **davidafranklin said:**
> Here is what I did just before your reply:

I ran the Janitor and removed everything. Now seems fine. After a reboot, things remained fine.

Great! Glad it's working now. Go ahead and mark the thread [SOLVED], if you would.

---

