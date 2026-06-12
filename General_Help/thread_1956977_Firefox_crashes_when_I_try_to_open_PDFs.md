---
title: "Firefox crashes when I try to open PDFs"
date: 2012-04-11
forum: General Help
---

### Post by imaginaryfruit on 2012-04-11
Today I installed adobe reader to download 3 particular documents. 

It froze every other time I tried to open said documents, so as soon as I printed these documents I removed adobe reader again.

Since then I haven't been able to download a pdf from firefox -- when I try to open a pdf firefox stops responding. 

Document viewer is still installed and works fine to open pdf documents already saved to my computer.

I'm using Ubuntu 11.10.

Any ideas? Help would be much appreciated!

---

### Post by lovinglinux on 2012-04-12
Don't bother with Adobe Reader.

Install [PDF Viewer](https://addons.mozilla.org/en-US/firefox/addon/pdfjs/) extension for Firefox.

---

### Post by imaginaryfruit on 2012-04-12
I removed Adobe Reader. But Firefox freezes when I try to open PDFs, whether or not PDF Viewer is enabled.

---

### Post by lovinglinux on 2012-04-12
> **imaginaryfruit said:**
> I removed Adobe Reader. But Firefox freezes when I try to open PDFs, whether or not PDF Viewer is enabled.

Please start Firefox in safe mode and check if the problem persists. To do that, close Firefox, open a terminal and run the following command:

```
firefox -safe-mode
```

If it doesn't help, try a clean profile, just for testing. You can create, launch and delete profiles using the profile manager:

```
firefox -P
```

Report if the problem persist or not using those methods.

---

### Post by imaginaryfruit on 2012-04-12
The problem persists in both cases. The terminal shows the following messages:

```
adina:~$ firefox -safe-mode
No bp log location saved, using default.
[000:002] Browser XEmbed support present: 1
[000:002] Browser toolkit is Gtk2.
[000:002] Using Gtk2 toolkit
[000:009] Warning(clientchannel.cc:637): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:010] Warning(clientchannel.cc:451): Could not initiate GoogleTalkPlugin connection
[000:011] GoogleTalkPlugin not running. Starting new process...
[000:011] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:011] Warning(clientchannel.cc:607): Failed to get GoogleTalkPlugin path. Trying default.
[000:019] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:019] Waiting for GoogleTalkPlugin to start...
[001:106] Attempting to connect to GoogleTalkPlugin...
[001:107] Read port file, port=35256
[001:128] Initiated connection to GoogleTalkPlugin
[001:213] Socket connection established
[001:213] ScheduleOnlineCheck: Online check in 5000ms
[001:307] Got cookie response, socket is authorized
[001:307] AUTHORIZED; socket handshake complete
*** NSPlugin Viewer  *** ERROR: /opt/Adobe/Reader9/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory
[006:218] HandleOnlineCheck: Starting check
[006:219] HandleOnlineCheck: OK; current state: 3
*** NSPlugin Viewer  *** ERROR: /opt/Adobe/Reader9/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory
Killed
adina:~$ firefox -P
*** NSPlugin Viewer  *** ERROR: /opt/Adobe/Reader9/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory
Killed
adina:~$ 
```

---

### Post by lovinglinux on 2012-04-12
You haven't removed Adobe Reader. Run these:

```
sudo apt-get purge acroread
sudo rm -fr /opt/Adobe/ 
```

Be careful to type the second command properly, because it is a recursive removal command using sudo. 

Then start Firefox, type **about:addons** in the address bar, then select plugins, then disable GoogleTalkPlugin. Test if you can open a PDF.

---

### Post by imaginaryfruit on 2012-04-14
It seems I had removed Adobe Reader:

```
adina:~$ sudo apt-get purge acroread
[sudo] password for adina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libcairo2:i386
  libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386 libxinerama1:i386
  nspluginviewer:i386 libxft2:i386 libthai0:i386 libjasper1:i386
  libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386 libxcb-shm0:i386
  libxrandr2:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
adina:~$
```

I ran both commands you suggested, and disabled the Googletalk plugin, and also apt-get autoremove. I still can't open PDFs.

---

### Post by callmemahavir on 2012-04-15
Goto -> Tools -> Add-ons -> Get-Addons -> Search "PDF"

You will find lot of PDF tools for Firefox.

---

### Post by lovinglinux on 2012-04-15
> **imaginaryfruit said:**
> It seems I had removed Adobe Reader:

```
adina:~$ sudo apt-get purge acroread
[sudo] password for adina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libcairo2:i386
  libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386 libxinerama1:i386
  nspluginviewer:i386 libxft2:i386 libthai0:i386 libjasper1:i386
  libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386 libxcb-shm0:i386
  libxrandr2:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
adina:~$
```

I ran both commands you suggested, and disabled the Googletalk plugin, and also apt-get autoremove. I still can't open PDFs.

Please post again the terminal output when when you run Firefox in safe mode:

```
firefox -safe-mode
```

---

