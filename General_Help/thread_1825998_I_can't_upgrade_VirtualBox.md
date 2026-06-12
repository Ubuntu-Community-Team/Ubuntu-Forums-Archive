---
title: "I can't upgrade VirtualBox"
date: 2011-08-16
forum: General Help
---

### Post by PCaddicted on 2011-08-16
Hello,
I have a problem with VirtualBox: when I execute it and then search for updates, a dialog box appears informing me that a new version is available and offers a link for downloading it.
I download the .deb file and run it, but nothing happens. It should normally display the Software Center, offering to upgrade VBox.
I've tried the well-known command:
```
sudo apt-get update
```but it didn't fix the problem. 
The version of VirtualBox that I'm currently running is 4.0.8 r 71778. The latest version is 4.0.12.
The good part, though, is that my virtual machines(with Mint Linux and openSuSe) can still be executed normally :).
Any help will be appreciated.

Regards,

---

### Post by fabricator4 on 2011-08-16
> **PCaddicted said:**
> Hello,
I have a problem with VirtualBox: when I execute it and then search for updates, a dialog box appears informing me that a new version is available and offers a link for downloading it.
I download the .deb file and run it, but nothing happens. It should normally display the Software Center, offering to upgrade VBox.
I've tried the well-known command:
```
sudo apt-get update
```but it didn't fix the problem. 
The version of VirtualBox that I'm currently running is 4.0.8 r 71778. The latest version is 4.0.12.
The good part, though, is that my virtual machines(with Mint Linux and openSuSe) can still be executed normally :).
Any help will be appreciated.

Regards,

It doesn't automatically start installing, you get a dialogue box asking what program you want to use for the install.  Make sure this dialogue is not buried under a window somewhere.

Don't forget to download and install the extension pack for 4.0.12 also.

Chris.

---

### Post by haqking on 2011-08-16
Some versions require a removal of previous versions.

Just use synaptic to remove the old version then use the .deb to reinstall.

I do it all the time.

---

### Post by PCaddicted on 2011-08-16
> **fabricator4 said:**
> It doesn't automatically start installing, you get a dialogue box asking what program you want to use for the install.  Make sure this dialogue is not buried under a window somewhere.
I certainly don't get that dialogue box. I had no windows displayed when I ran the .deb file[QUOTE=fabricator4]Don't forget to download and install the extension pack for 4.0.12 also.
Chris.[/QUOTE]
What pack?

---

### Post by haqking on 2011-08-16
> **PCaddicted said:**
> I certainly don't get that dialogue box. I had no windows displayed when I ran the .deb file
What pack?

there is an extension pack for Vbox at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

however if i was you remove your current install and use thr .deb top install a fresh, it will pick up your vbox settings

at worst it wont propogate your VM menu so you will need them back which is easy by pointing to the location of the VM's

---

### Post by Elfy on 2011-08-16
Alternatively add the necessary to the sources list and it'll appear as an update.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by haqking on 2011-08-16
> **forestpiskie said:**
> Alternatively add the necessary to the sources list and it'll appear as an update.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

i had problems with the update from sources list.  It would trash my install everytime.

So recenlty when it tells me there is an update i just download the .deb.

But i suspect it was something particular to my machine and config, i didnt bother troubleshooting it too much.

---

### Post by Elfy on 2011-08-16
:)

to be frank I tend to just keep using the same one I install until I reinstall/upgrade - then it gets the newest one

---

### Post by PCaddicted on 2011-08-17
> **forestpiskie said:**
> :)

to be frank I tend to just keep using the same one I install until I reinstall/upgrade - then it gets the newest one
That would mean creating all the VMs again- a true burden.:(
I've downloaded the so-called extension pack and and ran it. Soon after typing my root password, I got this error message:
>   Failed to install the Extension Pack /home/PCaddicted/Downloads/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack.
 VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=00000000 ErrInfo='VirtualBox version mismatch - expected 4.1 got 4.0'.
 Details:
   Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  ExtPackManager
   Interface: 
  IExtPackManager {2451b1ba-ab1c-42fb-b453-c58433bea8c7}
 Shall I delete the current VBox installation and use that .deb file to install the latest version?

---

### Post by haqking on 2011-08-17
> **PCaddicted said:**
> That would mean creating all the VMs again- a true burden.:(
I've downloaded the so-called extension pack and and ran it. Soon after typing my root password, I got this error message:

Shall I delete the current VBox installation and use the .deb file to install the latest version?


You wont lose your VM's, or at least not unless you do something silly.

Just remove your old version and install the latest version.

Then if your VM do not automatically appear just point virtual box to your VM folder.

I am assuming you have a seperate folder for your VM's.  If not then create one

---

### Post by PCaddicted on 2011-08-17
I've removed the current installation using Synaptic. Then, I executed the .deb file but, again, nothing happened. 
Any solution to this?

---

### Post by haqking on 2011-08-17
> **PCaddicted said:**
> I've removed the current installation using Synaptic. Then, I executed the .deb file but, again, nothing happened. 
Any solution to this?

Reboot machine maybe ?

Check the .deb is not corrupt by using the checksums on the download page

Make sure you have the correct .deb like 32 bit or 64 bit

---

### Post by PCaddicted on 2011-08-17
I've  rebooted the PC.
And the file still won't execute! Ticked the box "Allow executing this file as a program", but in vain...
When I downloaded the file, I certainly selected the correct options( Ubuntu 11.04, i386- I have a 32-bit processor)
:confused:

---

### Post by fabricator4 on 2011-08-17
> **PCaddicted said:**
> I've  rebooted the PC.
And the file still won't execute! Ticked the box "Allow executing this file as a program", but in vain...
When I downloaded the file, I certainly selected the correct options( Ubuntu 11.04, i386- I have a 32-bit processor)
:confused:

It's not an executable file: it's a .deb that can be installed with Gdebi.  When you double click on it should either ask what you want to open the file with (Gdebi) or it should start Gdebi automatically.

If you right click on the package does the menu have and option "Open with Gdebi package installer"?  If so, try clicking on that.

If not, then maybe there's a problem with Gdebi.  Try removing fully, then re-install Gdebi.

Chris.

---

### Post by CharlesA on 2011-08-17
Can you install it with dpkg?

```
sudo dpkg -i whatever.deb
```

---

### Post by PCaddicted on 2011-08-17
> **CharlesA said:**
> Can you install it with dpkg?

```
sudo dpkg -i whatever.deb
```
Thanks for the advice,  but it didn't work. I got this:
```
cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox-4.1_4.1.2-73507~Ubuntu~natty_i386.deb
  
```This thing seems so weird...

---

### Post by fabricator4 on 2011-08-17
> **PCaddicted said:**
> Thanks for the advice,  but it didn't work. I got this:
```
cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox-4.1_4.1.2-73507~Ubuntu~natty_i386.deb
  
```This thing seems so weird...

You have to first change to the directory where the .deb is, or use the full path to the .deb

If you've just left the deb file in the Downloads directory:

cd ~/Downloads
sudo dpkg -i virtualbox-4.1_4.1.2-73507~Ubuntu~natty_i386.deb

While typing the filename, just type "virtualbox" and press tab and it should autocomplete the rest if it's a unique filename - there's less chance of typos if you do it that way, and it saves time.

Chris

---

### Post by PCaddicted on 2011-08-20
> **fabricator4 said:**
> You have to first change to the directory where the .deb is, or use the full path to the .deb

If you've just left the deb file in the Downloads directory:

cd ~/Downloads
sudo dpkg -i virtualbox-4.1_4.1.2-73507~Ubuntu~natty_i386.deb

While typing the filename, just type "virtualbox" and press tab and it should autocomplete the rest if it's a unique filename - there's less chance of typos if you do it that way, and it saves time.

Chris
That worked, thank you :).
Finally got the latest version of VBox installed, so I'll mark this thread as solved for now.

---

### Post by dwaindibbley65 on 2011-12-21
I had the same issue, adding the sources didn't work for me. If had to remove the old version (Which for some reason was the version on my machine seemed to be the natty 11.04 version) then I installed the downloaded .deb 4.1.8 build in this case, it then installed the Oneric 11.10 version fine.

---

