---
title: "Google Picasa error"
date: 2009-11-29
forum: General Help
---

### Post by OldGoat58 on 2009-11-29
This is what I got from the terminal launch of the Google Picasa application.  I installed the application by double clicking on the picasa_2.7.3736-15_i386.deb in my download file.  Any help will be greatly appreciated.

mike@mike:~$ /usr/bin/picasa
/usr/bin/picasa: line 139:  5979 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  6082 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
mike@mike:~$ ^C
mike@mike:~$ 

Thanks!
Mike Fairless Hills PA
Ubuntu 9.10 i386 Karmic Koala

---

### Post by john newbuntu on 2009-11-30
In general, you might want to install these from synaptic package manager.  Try uninstalling and reinstalling it.
Go to system->administration->software sources->other software and add:
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

Also run this from a terminal window:
wget --quiet [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) -O - | sudo apt-key add -

Then system->administration->update manager and run update.
You should now see picasa when you open synaptic.  Install it from here and see how it goes.

---

### Post by OldGoat58 on 2009-11-30
> **john newbuntu said:**
> In general, you might want to install these from synaptic package manager.  Try uninstalling and reinstalling it.
Go to system->administration->software sources->other software and add:
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

Also run this from a terminal window:
wget --quiet [http://dl.google.com/linux/linux_signing_key.pub](http://dl.google.com/linux/linux_signing_key.pub) -O - | sudo apt-key add -

Then system->administration->update manager and run update.
You should now see picasa when you open synaptic.  Install it from here and see how it goes.

Thanks for the info John.  I think I may have done something wrong however.  Here is what I got from the Update Manager:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

And I got this from the terminal:

mike@mike:~$ wget --quiet http:dl.google.com/linux/linux signing key.pub -O- | sudo apt-key add -
[sudo] password for mike: 
gpg: no valid OpenPGP data found.
mike@mike:~$ 

I did get the software source added!  =-)  I'm new to CLI of Ubuntu / Linux and I truly appreciate your help!
Mike

mike@mike:~$ wget --quiet http:dl.google.com/linux/linux signing key.pub -O- | sudo apt-key add -
[sudo] password for mike: 
gpg: no valid OpenPGP data found.
mike@mike:~$ wget --quiet [http://dl.google.com/linux/linux](http://dl.google.com/linux/linux) signing key.pub -O- |sudo apt-key add -
[sudo] password for mike: 
gpg: no valid OpenPGP data found.
mike@mike:~$

---

### Post by OldGoat58 on 2009-11-30
mike@mike:~$ /usr/bin/picasa
/usr/bin/picasa: line 139:  3470 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  3573 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
mike@mike:~$ 


A shameless bump is all this reply is.  ;)

---

### Post by john newbuntu on 2009-12-01
On closely looking at your post, it appears like you missed the slashes (//) and/or the underscores in the complete URL.  Here's the command again after removing the link.  Please type these very carefully.

```
wget --quiet http://dl.google.com/linux/linux_signing_key.pub -O - | sudo apt-key add -
```

---

### Post by OldGoat58 on 2009-12-01
> **john newbuntu said:**
> On closely looking at your post, it appears like you missed the slashes (//) and/or the underscores in the complete URL.  Here's the command again after removing the link.  Please type these very carefully.

```
wget --quiet http://dl.google.com/linux/linux_signing_key.pub -O - | sudo apt-key add -
```

I did in fact not use the underscores in the command line.  Being new to the CLI format I'm careful but obviously not careful enough.  This morning I went through Synaptic and completely removed the Picasa application.  I then went to software sources and removed the Google website.  I then repeated the process.  This time when I run the code I get OK at the end.  I then added the application again through Synaptic.  When I click the application link in the menu, applications, graphics, picasa, picsas the application does not launch.  

I'm open to any other ideas.  I did some Google searching on this issue and found where people are using Wine to download and run the Windows version of Picasa.  I'm not sure if I'm supposed to use red or white wine, or if it is the type of whine I need to be careful with.  I'm sorry, I like to have fun with words!  After looking at what people were doing to get the application to run I believe that is a lesson I'd better take after more experience in this new format of OS.  

I need a good photo editing application.  I used Picasa in the Windows environment because that was what my wife used.  If there is a better option for Ubuntu / Linux I'm open to that as well.


Thanks!
Mike  :confused:

---

### Post by john newbuntu on 2009-12-02
In case you have'nt looked at this, here is a possible workaround:
[http://ubuntuforums.org/showthread.php?t=945257](http://ubuntuforums.org/showthread.php?t=945257)

You could also use applications->graphics->GIMP for image editing.

---

### Post by john newbuntu on 2009-12-03
Ok Mike.  Finally I got around trying to doing it myself. Since I love and have used Picasa several times before, I decided to try it myself for the first time on Linux.  On installation, I had the exact same problem that you had.  So here's what I did:
1. Completely uninstall picasa from Synaptic Package Manager.
2. In synaptic, go to settings->repositories-other software.
3. Uncheck the checkbox of deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
4. Click on Add and add this under the apt line:[FONT=monospace]
[/FONT]> deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free5. Now go to edit->reload package information
6. Type Picasa in quick search, mark for installation and apply.
After the installation completes, I have a working Picasa just like how it was in Windows.:D

This is a beta version of Picasa for Linux.  Anyway, as long as the bleeding edge works I am happy.

---

### Post by OldGoat58 on 2009-12-09
> **john newbuntu said:**
> Ok Mike.  Finally I got around trying to doing it myself. Since I love and have used Picasa several times before, I decided to try it myself for the first time on Linux.  On installation, I had the exact same problem that you had.  So here's what I did:
1. Completely uninstall picasa from Synaptic Package Manager.
2. In synaptic, go to settings->repositories-other software.
3. Uncheck the checkbox of deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
4. Click on Add and add this under the apt line:[FONT=monospace]
[/FONT]5. Now go to edit->reload package information
6. Type Picasa in quick search, mark for installation and apply.
After the installation completes, I have a working Picasa just like how it was in Windows.:D

This is a beta version of Picasa for Linux.  Anyway, as long as the bleeding edge works I am happy.

OMG!  You are my Ubuntu God!  I did just as you said and it worked perfectly!  It is finding all the images I had copied from my external hard drive.  It is speeding right on through the loading phase.

John NewBuntu you should be nominated for the Nobel Peace Prize.  Thank you for helping me get my favorite tool for photos back and operating.  Man, I think.........I think I love you man!  WooHoo!!

Thanks!
Mike
Fairless Hills, PA  :D:popcorn:

---

### Post by uberdonkey5 on 2009-12-23
Many thanks also..
I looked at other sites which talked about editing
 /etc/sysctl.conf
but THAT DOES NOT WORK.. this was the only working solution I could find

---

### Post by vx220 on 2009-12-27
Adding my thanks to john newbuntu - switching to the testing repository fixed the segmentation fault issue on 9.10 :)

---

### Post by Bryan55 on 2010-01-25
Hi

In **John newbuntu's **post #8 he suggests using

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free                      

but when I come to "marking to install" I get a **Warning** that the software can't be authenticated and it could allow malicious control of my PC.

Should I be worried by this.

Thanks for you help.

Bryan.

---

### Post by gwpritch on 2010-01-25
It just means you don't have the public key installed. You should be able to find it on the Google download site. But you can still ok the download without the key.

---

### Post by Bryan55 on 2010-01-25
> **gwpritch said:**
> It just means you don't have the public key installed. You should be able to find it on the Google download site. But you can still ok the download without the key.

Thats OK then.

And thanks for such a quick reply.

Bryan.

---

