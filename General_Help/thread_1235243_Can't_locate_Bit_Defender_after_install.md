---
title: "Can't locate Bit Defender after install"
date: 2009-08-08
forum: General Help
---

### Post by SPARTAN-118 on 2009-08-08
Hi everybody,

Before we move on to the main topic, just let me say a few things first.

First of all, I know there really is no point in having an antivirus on Linux, as there really is no reason to make a virus for a free OS that you can just download and install again.

Second, I'm not paranoid, just that I have a Wubi install, so if anything happens to Ubuntu, I need to be able to retreat back into Windows. And I do a lot of file transfers between the two systems (from Ubuntu, of course), so I need to be careful of what gets sent over to Vista.

So, with that out of the way, here's my problem.

I tried installing Bit Defender Antivirus Scanner for Unices, according to Tombuntu's [Guide to Downloading and Installing Bitdefender Antivirus on Ubuntu With 1-year Free License](http://tombuntu.com/index.php/2009/07/07/download-and-install-bitdefender-antivirus-on-ubuntu-with-1-year-free-license/).

I got to the point of actually accepting the License Agreement.
After I did, it installed [what looked] like usual, with no visible errors and returning to the directory I installed from.

However, now I can't find it - *anywhere*. It's not in Applications, nor System, and I can't locate the executable in /bin, so I can't create a custom Desktop Launcher.

Also, I can't just double-click the .deb.run file, as gedit pops up, rather than Gdebi Package Installer, and that returns a coding error.

So, where'd it go? Terminal reports it Successfully Installed, so I wonder what happened... :confused:

SPARTAN-118

PS: There really needs to be a :thoughtful: smiley... :mrgreen:

---

### Post by hansdown on 2009-08-08
Hi SPARTAN-118.

Is it in Applications->System Tools->BitDefender Scanner?

---

### Post by ouker on 2009-08-08
I don't know , but I also want to know it later!

---

### Post by SPARTAN-118 on 2009-08-08
No, it's not in Applications -> System Tools. 

Didn't I say it's not in Applications at all?

SPARTAN-118

---

### Post by hansdown on 2009-08-08
> **SPARTAN-118 said:**
> No, it's not in Applications -> System Tools. 

Didn't I say it's not in Applications at all?

SPARTAN-118

Yes you did.

Perhaps you erred in following the guide?

---

### Post by ouker on 2009-08-08
You may can find BitDefender launcher in system tools, and you also can run in terminal with command : bdgui

---

### Post by SPARTAN-118 on 2009-08-08
> **ouker said:**
> You may can find BitDefender launcher in system tools, and you also can run in terminal with command : bdgui
Will try that, right after I get Ubuntu up and running again.

See, I've been trying to use the theme "BlueSpace II", but with Metacity - and it was made for Emerald.

So, while waiting for a response in another of my topics, I decided to try "Blur Windows" in Compiz-config, which was suggested you do after installing the theme. 
That was a grave mistake.

Now, all I see when using Ubuntu is a black screen and my pointer, along with a blue/white gradient box where my screenlets are.

Now I just have to figure out how to change the settings in CompizConfig through the LiveCD, so I can use my system again.

Darn it, I really should be more careful with these things!

---

### Post by lidex on 2009-08-09
For me BitDefender installed to /opt and is present in "System Tools" menu. As for Compiz, check this link:
[http://linux.dsplabs.com.au/compiz-and-metacity-how-to-replace-the-current-window-manager-p30/]("http://linux.dsplabs.com.au/compiz-and-metacity-how-to-replace-the-current-window-manager-p30/")

---

