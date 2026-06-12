---
title: "Nexus 7 not recognized"
date: 2012-07-29
forum: General Help
---

### Post by ArgentSilver on 2012-07-29
So my brand new Nexus 7 tablet is not seen by Ubuntu as an mtp device when plugged into the USB port. Presumably for lack of a udev rule? Anybody know why or have a fix? I turned on USB debugging in Settings already...

Pretty bad that Windows 7 picked it up fine and showed it as a drive! Hate for M$ to have the edge and 'Just Work'!

---

### Post by ArgentSilver on 2012-07-29
A step in the right direction can be found here:
[http://www.nexus7tablethelp.com/2012/07/connect-nexus-7-to-linux-via-mtp-using.html](http://www.nexus7tablethelp.com/2012/07/connect-nexus-7-to-linux-via-mtp-using.html)

It's not automounting, but does work. Does anybody know how to make this automounting?

---

### Post by juanfi on 2012-08-03
Hmmm... It is not working still for me. After adding the 'SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}="4e42", MODE="0666"' line to /etc/udev/rules.d/51-android.rules, restaring udev, 

and trying 
sudo mtpfs -o allow_other /media/Nexus7

(folder which I already made, and writable) I only get the Playlists folder (empty) :(

trying gtmp gives me a coredump.
 
So far I am using adb's from the Android SDK which works for pushing and pulling folders.

Juan

---

### Post by vmunoz on 2012-10-24
Looks like this person has the answer. I am going to try this soon:


[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)

---

### Post by frncz on 2012-10-24
> **vmunoz said:**
> Looks like this person has the answer. I am going to try this soon:


[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)

I don't have a Nexus , but the 'howto' in the link above is beautifully written and clear. It should help many (if it work, of course)

---

### Post by Mark Phelps on 2012-10-24
Good Luck with this ... 

Folks have much the same problem trying to mount a Samsung Galaxy S3 -- and the problem, like with the Nexux 7, is due to Google removing USB Mass Storage mounting option from the ICS version of the Android OS.

Lots of folks have posted here about that problem and, I have yet to see anyone able to solve it successfully.  I tried all of the suggestions on my PC and none of them worked.

IF this works for you, please let us know -- as there are a LOT of us who would like to get access back to the new Android phones and tablets.

---

### Post by carlosfunk on 2012-11-07
Worked perfectly for me.

---

### Post by CaptainLinux on 2012-11-07
> **carlosfunk said:**
> Worked perfectly for me.

Thank you for the update.

---

### Post by layolayo on 2012-11-25
Cheers - the Bernaerts link works a treat

Although as I'm running JellyBean 4.2 I changed 99-android.rules to :

```

SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e41", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e42", MODE="0666" 
ENV{ID_MODEL}=="Nexus_7", ENV{ID_MODEL_ID}=="4e41", ACTION=="add", RUN+="/usr/bin/sudo -u yourlogin /usr/local/sbin/go-mtpfs -allow-other=true /media/Nexus7"
ENV{ID_MODEL}=="Nexus_7", ENV{ID_MODEL_ID}=="4e42", ACTION=="add", RUN+="/usr/bin/sudo -u yourlogin /usr/local/sbin/go-mtpfs -allow-other=true /media/Nexus7"
ENV{ID_MODEL}=="Nexus_7", ENV{ID_MODEL_ID}=="4e41", ACTION=="remove", RUN+="/bin/umount /media/Nexus7"
ENV{ID_MODEL}=="Nexus_7", ENV{ID_MODEL_ID}=="4e42", ACTION=="remove", RUN+="/bin/umount /media/Nexus7"

```

As I was having trouble with PTP initiating. I found using the above PTP connects fine.

Also note that the Nexus7 will always show in Nautilus, but on connection it auto-mounts and it dismounts on removal which is sweet.

---

### Post by carl4926 on 2012-11-25
It should mount as MTP without issue

---

### Post by Smokin Whale on 2012-12-11
Posting to confirm issues here as well. How hard is it for Ubuntu to get reliable MTP working? Feel like switching back to Windows over little silly problems like this. Will try a few commands, hopefully will get it working...

---

### Post by mitulv4u on 2012-12-21
Hey I am not a advanced user, but got my nexus 7 working with this guide

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)

---

### Post by Locus Kiesselbachi on 2013-02-10
> **ArgentSilver said:**
> A step in the right direction can be found here:
[http://www.nexus7tablethelp.com/2012/07/connect-nexus-7-to-linux-via-mtp-using.html](http://www.nexus7tablethelp.com/2012/07/connect-nexus-7-to-linux-via-mtp-using.html)

It's not automounting, but does work. Does anybody know how to make this automounting?

Hello!
Thank you from posting this, but im stuck (bump) in one command:
command
sudo chmod a+rwx /media/Nexus7
gives
Transport endpoint is not connected

MTP is enabled (checked)
USB port works in computer (checked with USB stick)
PC - AMD_Athlon_1800, ASRock_K7S41GX; (L)ubuntuOS_11.10

---

### Post by linfidel on 2013-02-10
> **Locus Kiesselbachi said:**
> Hello!
Thank you from posting this, but im stuck (bump) in one command:
command
sudo chmod a+rwx /media/Nexus7
gives
Transport endpoint is not connected

MTP is enabled (checked)
USB port works in computer (checked with USB stick)
PC - AMD_Athlon_1800, ASRock_K7S41GX; (L)ubuntuOS_11.10

MTP is not the same as a USB drive.  These devices will not work as a USB drive in either Linux or Windows, although there are drivers provided by Samsung for windows.

As for your "one command", most likely that one command is what is working correctly.  If the directory "/media/Nexus7" does not exist, then that command is working as expected, but the previous procedure is not creating the directory, ie, not mounting the device.

I have found that go-mtpfs will work if you have the right software installed, but not very reliably for 64 bits, in my experience so far.  But it does mount, if everything is done correctly, and if the _device is connected and not in sleep mode_.

---

### Post by ccrs8 on 2013-02-10
I have the Nexus 7 and the Galaxy Nexus smartphone.  Both are set up to mount as MTP instead of the old style of just mounting like any old thumb drive.  It's a pain in the butt for sure, but I do love having access to the entire phone/tablet capacity for storage instead of how the Nexus S smartphone was set up, where a hardcoded amount of internal space was set up for apps and the rest set up for storage which could be mounted easily.

ANYWAY, when I first got these devices I followed some of the tutorials linked in this thread to get everything set up.  And it worked fine.  No qualms.  But you know what?  I found that the easiest thing was to just transfer files over my network via FTP.  There is a free FTP server in the Android Google Play Store that is a piece of cake to set up, and then I could just use that to share files between my computer and my phone, and it ends up being a lot faster than using MTP.

---

### Post by linfidel on 2013-02-10
> **ccrs8 said:**
> I have the Nexus 7 and the Galaxy Nexus smartphone.  Both are set up to mount as MTP instead of the old style of just mounting like any old thumb drive.  It's a pain in the butt for sure, but I do love having access to the entire phone/tablet capacity for storage instead of how the Nexus S smartphone was set up, where a hardcoded amount of internal space was set up for apps and the rest set up for storage which could be mounted easily.

ANYWAY, when I first got these devices I followed some of the tutorials linked in this thread to get everything set up.  And it worked fine.  No qualms.  But you know what?  I found that the easiest thing was to just transfer files over my network via FTP.  There is a free FTP server in the Android Google Play Store that is a piece of cake to set up, and then I could just use that to share files between my computer and my phone, and it ends up being a lot faster than using MTP.
Yeah, I have the ftp server, too, and it works fine for simply transferring files.  MTP is more convenient for some things, but mainly because you don't need to set up an ftp client.

---

### Post by ccrs8 on 2013-02-10
> **linfidel said:**
> Yeah, I have the ftp server, too, and it works fine for simply transferring files.  MTP is more convenient for some things, but mainly because you don't need to set up an ftp client.

Ubuntu has ftp client capabilities built in.  Once I set up the FTP server on my Android device (very simple - just enter a username and port number), I can access it by opening the terminal and typing:

$ file-manager [ftp://selected-username@IP-address:port](ftp://selected-username@IP-address:port) number

so for me as a Xubuntu user:

thunar [ftp://ccrs8@192.168.1.32:1024](ftp://ccrs8@192.168.1.32:1024)

Anyway, I guess after typing all of that I can see that maybe that's a pain in the butt, but I think it's less of a pain than setting up MTP in Ubuntu.

---

### Post by Locus Kiesselbachi on 2013-02-11
> **linfidel said:**
> MTP is not the same as a USB drive.  These devices will not work as a USB drive in either Linux or Windows, although there are drivers provided by Samsung for windows.

As for your "one command", most likely that one command is what is working correctly.  If the directory "/media/Nexus7" does not exist, then that command is working as expected, but the previous procedure is not creating the directory, ie, not mounting the device.

I have found that go-mtpfs will work if you have the right software installed, but not very reliably for 64 bits, in my experience so far.  But it does mount, if everything is done correctly, and if the _device is connected and not in sleep mode_.
command
sudo mkdir /media/Nexus7
gives
mkdir: cannot create directory `/media/Nexus7': File exists

:P

---

### Post by linfidel on 2013-02-11
> **ccrs8 said:**
> Ubuntu has ftp client capabilities built in.  Once I set up the FTP server on my Android device (very simple - just enter a username and port number), I can access it by opening the terminal and typing:

$ file-manager [ftp://selected-username@IP-address:port](ftp://selected-username@IP-address:port) number

so for me as a Xubuntu user:

thunar [ftp://ccrs8@192.168.1.32:1024](ftp://ccrs8@192.168.1.32:1024)

Anyway, I guess after typing all of that I can see that maybe that's a pain in the butt, but I think it's less of a pain than setting up MTP in Ubuntu.

Thanks!   Actually, I never tried that.  I guess I was too lazy to look up the format.  I just opened Nautilus (gnome's file manager, in case you forgot), and typed it into the address bar: ```
ftp://me@samsung:port
``` and it prompted me for my password, then opened perfectly (I have an entry in my /etc/hosts file).  I'll try it out a bit and see how it works.

I agree, with all the trouble I've had, this is easier than using fuse.  Last time I used Filezilla, I was getting about 2 MB/s on small files; I'm not sure how that compares with the alternative, but it's OK for most things I transfer.

---

### Post by linfidel on 2013-02-11
> **Locus Kiesselbachi said:**
> command
sudo mkdir /media/Nexus7
gives
mkdir: cannot create directory `/media/Nexus7': File exists

:P

My guess would be that the directory already exists (or a file with that name exists in the directory).

Try doing "ls /media" and see if it's there.  Sometimes error messages actually have useful information.  :)

---

### Post by Kixtosh on 2013-02-24
Same issue for me. Nexus 7 not recognized. I've tried two methods so far, with Lucid Lynx 10.04:

[LIST]
[*]This one was written for Mint: 
[http://blog.jeshurun.ca/technology/connecting-the-google-nexus-7-to-ubuntu-mint-over-usb](http://blog.jeshurun.ca/technology/connecting-the-google-nexus-7-to-ubuntu-mint-over-usb)
[*]The one referenced earlier in the thread: 
[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)
[/LIST]
In the case of the first method, it stopped here:
```
:~$ sudo nano /etc/udev/rules.d/99-android.rules
~$ sudo chmod +x /etc/udev/rules.d/99-android.rules
~$ sudo apt-get install libmtp-common libmtp-runtime libmtp9 mtpfs mtp-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Couldn't find package libmtp-common**
~$ sudo mkdir /media/nexus7
~$ sudo chmod 755 /media/nexus7
~$ sudo mtpfs -o allow_other /media/nexus7
sudo: **mtpfs: command not found**
```

In the case of the second method, it got stuck much earlier on, with this result:
```
~$  sudo chmod a+r /etc/fuse.conf
~$  sudo gedit /etc/fuse.conf
~$ sudo apt-get install libmtp-dev git golang
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package git is not available,** but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: **Package git has no installation candidate**
~$ mkdir /tmp/go
~$ export GOPATH=/tmp/go
~$ go get github.com/hanwen/go-mtpfs
**go: command not found**
```

---

### Post by heyup on 2013-03-10
I found aafm (Android ADB File Manager). Its OK.

[https://github.com/sole/aafm]("https://github.com/sole/aafm")

More details on the above link.

---

### Post by Kixtosh on 2013-03-10
Looks promising, heyup. I might try that out later.

In the meantime, I get around my transfer issues by simply uploading stuff to the free (for 5GB) Google Drive. From there I can transfer to or from the Nexus 7 using my home wifi network. It's quite painless, and anyone with an Android device such as the Nexus 7 has been obliged to create a gmail address to use it, and therefore they already have access to Google Drive using that gmail idendity.

---

### Post by carl4926 on 2013-03-12
[COLOR=#500050][FONT=arial]android-tools
Solved it for me[/FONT][/COLOR]

---

### Post by Topsiho on 2013-03-12
Using:

[http://bernaerts.dyndns.org/linux/268-ubuntu-automount-any-mtp-device](http://bernaerts.dyndns.org/linux/268-ubuntu-automount-any-mtp-device)

solved this problem for me :)

Thanks to Nicolas Bernaerts for his good work.

Topsiho

---

### Post by AlanR8 on 2013-03-12
Ubuntu 13.04

---

