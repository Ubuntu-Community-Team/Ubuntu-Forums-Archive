---
title: "Handle RAR archives in LiveCD"
date: 2009-07-10
forum: General Help
---

### Post by masterton on 2009-07-10
How can I open and read RAR archives in Ubuntu LiveCD? 
What additonal program should I install? (I don't know how to install program which has to be complied first)
Thank you. :p

---

### Post by frenkel on 2009-07-10
Search google next time. You can install unrar for it.

---

### Post by wojox on 2009-07-10
You need to open the terminal and

```
sudo apt-get install unrar
```

But I don't know for sure with a live cd?

If it works navigate to the directory where your rar file is and type:

```
unrar x filename.rar
```

---

### Post by libra1780 on 2009-07-10
once installed the above unrar package you can also use ark (standard in Kde distro's, don't know about gnome's)
Remember to repeat all steps after every reboot

---

### Post by masterton on 2009-07-10
> **wojox said:**
> You need to open the terminal and

```
sudo apt-get install unrar
```

It doesn't work in LiveCD. Error message:
```
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by wojox on 2009-07-10
Type in terminal:

```
pstree
```

Paste it back up here. We can see what running.

---

### Post by ajgreeny on 2009-07-10
In the live CD, I imagine update manager will be running as there will be a lot of potential updates, even though there is no point in installing them on a live CD.

You can, however, certainly install the occasional utility like unrar on a live CD and use it, I have done it with other applications, but it will be gone the next time you boot up, of course.

---

### Post by wojox on 2009-07-10
Can he turn update manager off to make apt-get available?

---

### Post by masterton on 2009-07-10
I tried again and this gives me this message this time.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
Package unrar has no installation candidate
```

I installed the latest uBuntu yesterday. 
Where can I check what version my uBuntu is running?

> **wojox said:**
> Type in terminal:

```
pstree
```

Paste it back up here. We can see what running.

Here you are:
```

init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bluetoothd
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;fast-user-switc
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;6*[{firefox}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;bluetooth-apple
     &#9474;                             &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;{evolution-alarm}
     &#9474;                             &#9500;&#9472;gnome-panel
     &#9474;                             &#9500;&#9472;metacity
     &#9474;                             &#9500;&#9472;nautilus
     &#9474;                             &#9500;&#9472;nm-applet
     &#9474;                             &#9500;&#9472;python
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;ssh-agent
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfs-hal-volume&#9472;&#9472;&#9472;{gvfs-hal-volume}
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9492;&#9472;2*[hald-addon-stor]
     &#9500;&#9472;indicator-apple
     &#9500;&#9472;klogd
     &#9500;&#9472;6*[login&#9472;&#9472;&#9472;bash]
     &#9500;&#9472;mixer_applet2&#9472;&#9472;&#9472;{mixer_applet2}
     &#9500;&#9472;mount.ntfs-3g
     &#9500;&#9472;nm-system-setti
     &#9500;&#9472;notify-osd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9500;&#9472;wpa_supplicant
     &#9492;&#9472;yelp&#9472;&#9472;&#9472;2*[{yelp}]

```

---

### Post by wojox on 2009-07-10
Ok try

```
sudo apt-get install unrar-free
```

---

### Post by masterton on 2009-07-10
> **wojox said:**
> Ok try

```
sudo apt-get install unrar-free
```

It seems it installed successfully but it doesn't extract files correctly.
I tried to press extract to extract all files in one RAR archive. The dialog said extract sccuessful but no file shows up in the directory.
Then I tried another RAR archive. It has 4 files but only 2 files are shown up after extracting. The dialog said extract sccuessful but clearly it's not.

What's up?

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  pike
The following NEW packages will be installed:
  unrar-free
0 upgraded, 1 newly installed, 0 to remove and 156 not upgraded.
Need to get 22.0kB of archives.
After this operation, 111kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/universe unrar-free 1:0.0.1+cvs20071127-1 [22.0kB]
Fetched 22.0kB in 1s (12.1kB/s)                     
Selecting previously deselected package unrar-free.
(Reading database ... 111297 files and directories currently installed.)
Unpacking unrar-free (from .../unrar-free_1%3a0.0.1+cvs20071127-1_i386.deb) ...
Processing triggers for man-db ...
Setting up unrar-free (1:0.0.1+cvs20071127-1) ...

```

---

### Post by wojox on 2009-07-10
Not sure maybe try downloading the .rar file again?

---

### Post by masterton on 2009-07-10
> **wojox said:**
> Not sure maybe try downloading the .rar file again?

No, that's not the problem. I tried a few more and it only claimed it is successful but it doesn't extract anything at all most of the time.

It seems to do with the broken (faulty?) unrar function.

I use the GUI to extract by the way.

---

### Post by masterton on 2009-07-10
Using command line will see the actual result. Every file in the archive it tries to extract returns failed

---

### Post by ajgreeny on 2009-07-10
Make sure you have the multiverse repos enabled and try to install unrar again, it is definitely in there, so I can see no reason for you not to be able to install that instead of the unrar-free.

---

### Post by masterton on 2009-07-10
> **ajgreeny said:**
> Make sure you have the multiverse repos enabled and try to install unrar again, it is definitely in there, so I can see no reason for you not to be able to install that instead of the unrar-free.
I tried this command line:
```
sudo aptitude install p7zip p7zip-full rar unrar
```
Well I wonder if I have installed something redundant but it works now.

---

