---
title: "how do i install bit defender for linux"
date: 2010-04-26
forum: General Help
---

### Post by mul01 on 2010-04-26
Hi all,
i am wondering if anyone can help me i send this anti virus scanner for linux on the ubuntu geek site.

bit defender for linux i downloaded the ubuntu version any1 know how to install it?

sorry i am a newbite i am still learning.

heres the link to it on bit defenders site [http://www.bitdefender.co.uk/business/antivirus-for-unices.html](http://www.bitdefender.co.uk/business/antivirus-for-unices.html)

if anyone could help that would be great.
thanks:)

---

### Post by balaknair on 2010-04-26
Step 1:
Save the downloaded .deb.run file to your /home directory

Step 2:
Open a terminal(Applications menu> Accessories> Terminal) and type in the following command(replacing the *** with the actual file name, or just type upto *BitDef* and press the tab key, it should autocomplete); the command is case sensitive.

*sudo sh BitDefender-Antivirus-Scanner-***.deb.run*

Type in your password when prompted, you will now see a License agreement. Accept it by typing in *accept*

Now you can run the program from Applications menu> System Tools> BitDefender Scanner

Start the program, type in the license key(free 1 year license available here [http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/) ), update the antivirus signatures and that's it.

---

### Post by carl4926 on 2010-04-26
Save yourself the trouble.

Consider if you Really need it.!

---

### Post by shaka_zulu on 2010-04-26
you can just click twice on that file and it will make self-installation. But like guy before me said save your self trouble. you will not need it.

---

### Post by insane_alien on 2010-04-26
unless he's maybe setting up a box that checks files before they get somewhere they can cause real damage.

seriously, there are some very good reasons for having an AV on linux. just because none of them are 'zomg linux is so prone to viruses' doesn't mean that there is absolutely no reason whatsoever.

---

### Post by shaka_zulu on 2010-04-26
Of course that Linux is not immune 100% on viruses but since he is a new user i had a feeling like have AV is a must. :) All important files may be encrypted and well hidden if that is a case. Access to them can be limited etc. Bottom line if somebody want something let him have it :)

---

### Post by shaka_zulu on 2010-04-26
Of course that Linux is not immune 100% on viruses but since he is a new user i had a feeling like having AV is a must. :) All important files may be encrypted and well hidden if that is a case. Access to them can be limited etc. Bottom line if somebody want something let him have it :)

---

### Post by elliotn on 2010-04-26
i did the same thing when i first got my ubuntu, bt google told me i may not need a/v

---

### Post by mul01 on 2010-04-26
thanks balaknair its installed now and scanning. :)

thanks for all the comments i thought it was best to get A.V to be safe as i dont want to get any windows virus and pass it on to windows users or incase any linux ones get made or something and u never know.

so got 1 to be safe.

thanks all

---

### Post by bumder on 2010-08-11
if i wanted to uninstall BitDefender for Ubuntu completely (logs and config files etc.), would i just use:

$ sudo apt-get remove BitDefender

or is there a better command?

cant seem to find BitDefender in synaptic package manager.

---

### Post by balaknair on 2010-08-11
> **bumder said:**
> if i wanted to uninstall BitDefender for Ubuntu completely (logs and config files etc.), would i just use:

$ sudo apt-get remove BitDefender

or is there a better command?

cant seem to find BitDefender in synaptic package manager.

To remove bitdefender completely including configuration files use the purge command
```
sudo apt-get purge bitdefender-scanner bitdefender-scanner-gui
```

---

### Post by marl30 on 2010-08-12
There is a great antivirus in the Ubuntu Software Center called Clamtk. It works like a charm. You could have gotten it instead of those other poorly supported AV scanners out there. I know Linux don't necessarily need an AV, as virus treats are minimal. However, I use an AV mainly because I often share files I download with Windows. The latest version can be downloaded from [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/).

There's also a Nautilus extension available in the Software Center for Clamtk that allows you to right click on specific files and scan them as you would in Windows.

---

