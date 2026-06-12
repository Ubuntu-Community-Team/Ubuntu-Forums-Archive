---
title: "Am I typing this command correctly?"
date: 2009-12-27
forum: General Help
---

### Post by azitizz on 2009-12-27
Hi there, Im following instructions to install a backend for Canon Pixma printer/scanners. Ive been having success downloading the files etc.. up to the point in the instructions located at [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html) 
Under the heading "Build SANE" that says to "run:> $ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
I seem to have the proper packages installed but I keep getting the error messages in terminal when I copy and paste the above command in it: > bash: $./configure: No such file or directory


Ive tried variations of the ./configure with or without the "$" and spaces and it continues to give me error msgs.
Im sure Im doing something wrong thats probably simple. Im still a beginner at this.
Any help would be extremely appreciated

---

### Post by taurus on 2009-12-27
Leave the **[COLOR="Red"]$[/COLOR]** out because that symbol is supposed to be your prompt.

```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

Of course, make sure you are in the right directory before you run the ./configure command.

---

### Post by azitizz on 2009-12-27
> **taurus said:**
> Leave the **[COLOR="Red"]$[/COLOR]** out because that symbol is supposed to be your prompt.

```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

Of course, make sure you are in the right directory before you run the ./configure command.
Thanks for the speedy reply. However still it gives me the message:
> bash: ./configure: No such file or directory

I copied and pasted the exact text you gave me into treminal.

---

### Post by taurus on 2009-12-27
Are you in the _right directory_?

What's the output of this command from a terminal?

```
ls -la
```

---

### Post by azitizz on 2009-12-27
> **taurus said:**
> Are you in the _right directory_?

What's the output of this command from a terminal?

```
ls -la
```
it says:> total 420
drwxr-xr-x 56 mikepanc mikepanc  4096 2009-12-27 14:27 .
drwxr-xr-x  3 root     root      4096 2009-10-14 19:56 ..
drwx------  3 mikepanc mikepanc  4096 2009-10-15 09:05 .adobe
drwxr-xr-x  4 mikepanc mikepanc  4096 2009-12-22 14:55 .audacity-data
drwxr-xr-x 10 mikepanc mikepanc  4096 2009-12-16 12:41 .azureus
drwxr-xr-x  9 mikepanc mikepanc  4096 2009-12-15 10:44 Azureus Downloads
-rw-------  1 mikepanc mikepanc   845 2009-12-13 22:55 .bash_history
-rw-r--r--  1 mikepanc mikepanc   220 2009-10-14 19:56 .bash_logout
-rw-r--r--  1 mikepanc mikepanc  3115 2009-10-14 19:56 .bashrc
drwxr-xr-x  7 mikepanc mikepanc  4096 2009-12-13 22:48 .cache
drwxr-xr-x  6 mikepanc mikepanc  4096 2009-12-09 10:26 .cddb
-rw-r--r--  1 mikepanc mikepanc     0 2009-12-01 13:50 chanting
drwx------  3 mikepanc mikepanc  4096 2009-11-10 22:41 .compiz
drwxr-xr-x 13 mikepanc mikepanc  4096 2009-12-21 08:58 .config
drwx------  3 mikepanc mikepanc  4096 2009-10-14 20:05 .dbus
drwxr-xr-x 16 mikepanc mikepanc  4096 2009-12-23 11:33 Desktop
-rw-r--r--  1 mikepanc mikepanc    23 2009-11-02 06:29 .dmrc
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-14 20:05 Documents
-rw-------  1 mikepanc mikepanc    16 2009-10-14 20:05 .esd_auth
drwxr-xr-x  8 mikepanc mikepanc  4096 2009-11-09 22:53 .evolution
-rw-r--r--  1 mikepanc mikepanc   357 2009-10-14 19:56 examples.desktop
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-11-01 22:36 .fontconfig
drwx------  5 mikepanc mikepanc  4096 2009-12-27 12:07 .gconf
drwx------  2 mikepanc mikepanc  4096 2009-12-27 14:44 .gconfd
drwx------  4 mikepanc mikepanc  4096 2009-10-15 21:33 .gegl-0.0
drwxr-xr-x 22 mikepanc mikepanc  4096 2009-11-30 12:25 .gimp-2.6
-rw-r-----  1 mikepanc mikepanc     0 2009-12-27 14:41 .gksu.lock
drwx------ 11 mikepanc mikepanc  4096 2009-12-27 11:08 .gnome2
drwx------  2 mikepanc mikepanc  4096 2009-10-14 20:05 .gnome2_private
drwx------  2 mikepanc mikepanc  4096 2009-12-27 12:07 .gnupg
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-12-27 09:57 .gstreamer-0.10
-rw-r--r--  1 mikepanc mikepanc   120 2009-12-27 12:07 .gtk-bookmarks
dr-x------  2 mikepanc mikepanc     0 2009-12-27 12:07 .gvfs
drwxr-----  2 mikepanc mikepanc  4096 2009-10-18 20:06 .hplip
-rw-------  1 mikepanc mikepanc 40002 2009-12-27 12:07 .ICEauthority
drwx------  3 mikepanc mikepanc  4096 2009-12-15 10:48 .icedteaplugin
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-17 23:49 .icons
drwx------  3 mikepanc mikepanc  4096 2009-10-18 14:39 .kde
drwx------  2 mikepanc mikepanc  4096 2009-10-19 12:45 .kino-history
-rw-r--r--  1 mikepanc mikepanc  2969 2009-10-19 12:45 .kinorc
drwx------  3 mikepanc mikepanc  4096 2009-10-15 21:28 .local
drwx------  3 mikepanc mikepanc  4096 2009-10-15 09:05 .macromedia
drwx------  5 mikepanc mikepanc  4096 2009-12-09 10:14 .mozilla
drwxr-xr-x  3 mikepanc mikepanc  4096 2009-12-04 14:52 Music
drwxr-xr-x  3 mikepanc mikepanc  4096 2009-10-14 20:05 .nautilus
drwxr-xr-x  3 mikepanc mikepanc  4096 2009-12-15 10:48 .netx
drwxr-xr-x  3 mikepanc mikepanc  4096 2009-10-15 21:28 .openoffice.org
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-15 21:27 Photos
drwxr-xr-x  4 mikepanc mikepanc  4096 2009-11-10 22:20 .picasa
drwxr-xr-x  3 mikepanc mikepanc  4096 2009-11-04 21:46 Pictures
-rw-r--r--  1 mikepanc mikepanc    37 2009-10-18 20:06 .printer-groups.xml
-rw-r--r--  1 mikepanc mikepanc   675 2009-10-14 19:56 .profile
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-14 20:05 Public
drwx------  2 mikepanc mikepanc  4096 2009-12-27 12:07 .pulse
-rw-------  1 mikepanc mikepanc   256 2009-10-14 20:05 .pulse-cookie
-rw-------  1 mikepanc mikepanc  3625 2009-12-21 12:19 .recently-used
-rw-------  1 mikepanc mikepanc 82867 2009-12-27 11:08 .recently-used.xbel
drwxrwx---  3 mikepanc mikepanc  4096 2009-11-04 21:35 .sane
drwxr-xr-x 14 mikepanc mikepanc  4096 2009-12-27 14:39 sane-backends
drwx------  4 mikepanc mikepanc  4096 2009-12-24 23:03 .Skype
-rw-r--r--  1 mikepanc mikepanc   142 2009-11-10 14:54 .so_sane_state
drwx------  2 mikepanc mikepanc  4096 2009-10-30 23:27 .ssh
-rw-r--r--  1 mikepanc mikepanc     0 2009-10-14 20:09 .sudo_as_admin_successful
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-14 20:05 Templates
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-17 23:49 .themes
drwxr-xr-x  5 mikepanc mikepanc  4096 2009-10-16 23:07 .thumbnails
drwx------  2 mikepanc mikepanc  4096 2009-10-20 21:53 .tsclient
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-15 00:34 .update-manager-core
drwx------  2 mikepanc mikepanc  4096 2009-11-02 15:51 .update-notifier
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-10-14 20:05 Videos
drwxr-xr-x  4 mikepanc mikepanc  4096 2009-11-09 22:39 .VirtualBox
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-12-25 23:35 .wapi
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-11-06 16:37 .xine
drwxr-xr-x  2 mikepanc mikepanc  4096 2009-11-02 06:30 .xinput.d
-rw-r--r--  1 mikepanc mikepanc   573 2009-11-10 22:56 .xscreensaver-getimage.cache
-rw-------  1 mikepanc mikepanc  5446 2009-12-27 14:20 .xsession-errors
-rw-------  1 mikepanc mikepanc  7465 2009-12-27 11:08 .xsession-errors.old


---

### Post by taurus on 2009-12-27
You are currently in your $HOME so you need to change to where you have saved and unpacked the download.  Did you save it to ~/Desktop?

```
ls -la ~/Desktop
```

---

### Post by sgosnell on 2009-12-27
You shouldn't need to build sane.  It's included in the standard Ubuntu.

---

### Post by azitizz on 2009-12-27
> **sgosnell said:**
> You shouldn't need to build sane.  It's included in the standard Ubuntu.

My Scanner wont work with whatever is packaged. It seems to be a common fix. Thats how I came across the above website on building the sane backend.

> **taurus said:**
> You are currently in your $HOME so you need to change to where you have saved and unpacked the download. Did you save it to ~/Desktop?

Code:

ls -la ~/Desktop

The download was saved in my home folder "mikepanc" I moved it to my desktop now. I tries typing the command again but still the error msg.

---

### Post by azitizz on 2009-12-27
This was what resulted form the command ls la /desktop... (I dont know how to make the tilde symbol) I bolded and coloured the folder I moved in the text below:
> mikepanc@mikepanc-laptop:~$ ls -la ~/Desktop
total 1718736
drwxr-xr-x 17 mikepanc mikepanc       4096 2009-12-27 19:13 .
drwxr-xr-x 55 mikepanc mikepanc       4096 2009-12-27 19:13 ..
drwxr-xr-x  5 mikepanc mikepanc       4096 2009-12-12 23:05 1-day course
-rw-r--r--  1 mikepanc mikepanc        983 2009-12-22 22:40 AudioCD0.k3b
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-12 23:22 Benzie
drwxr-xr-x  3 mikepanc mikepanc       4096 2009-12-04 14:50 Chanting
drwx------  2 mikepanc mikepanc       4096 2009-12-07 21:03 Check Your Head
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-11-11 23:08 Dhamma pics
-rwxr-xr-x  1 mikepanc mikepanc   60106796 2009-12-19 12:33 Droned
drwx------  4 mikepanc mikepanc       4096 2009-12-07 21:06 Genesis Discography Plus
-rw-r--r--  1 mikepanc mikepanc   28071980 2009-12-19 12:34 Lengthwise
-rwxr-xr-x  1 mikepanc mikepanc   56954924 2009-12-19 12:34 Lighten Up 2
drwxrwxrwx  3 mikepanc mikepanc      12288 2009-12-12 23:50 MayOct09
-rw-r--r--  1 mikepanc mikepanc      34932 2009-11-23 09:03 Mike P & Me.jpg
drwxr-xr-x  4 mikepanc mikepanc       4096 2009-12-21 13:40 ONYX
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-23 11:39 Pics
[COLOR="Red"]**drwxr-xr-x 14 mikepanc mikepanc       4096 2009-12-27 14:39 sane-backends**[/COLOR]
drwxr-xr-x  4 root     root           4096 2009-12-13 22:19 scangearmp-mp510-1.00
-rw-r--r--  1 mikepanc mikepanc    1774011 2009-12-13 12:31 scangearmp-mp510-1.00-1.i386.rpm
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-22 14:55 Secret Sauce 1
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-22 14:27 Secret Sauce 2
-rw-r--r--  1 mikepanc mikepanc   21952556 2009-12-19 12:34 Shortwave Transmission On up To The Minuteman Nine
-rwxr-xr-x  1 mikepanc mikepanc  101947436 2009-12-19 12:34 The Brazilian
-rw-r--r--  1 mikepanc mikepanc 1487280000 2007-05-20 12:52 The Highest Welfare.dv
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-14 22:38 torrents
-rwxr-xr-x  1 mikepanc mikepanc        361 2009-12-14 22:16 transmission.desktop
drwxr-xr-x  2 mikepanc mikepanc       4096 2009-12-12 23:22 Vipassana
mikepanc@mikepanc-laptop:~$

---

### Post by bboston7 on 2009-12-27
> **azitizz said:**
> My Scanner wont work with whatever is packaged. It seems to be a common fix. Thats how I came across the above website on building the sane backend.



The download was saved in my home folder "mikepanc" I moved it to my desktop now. I tries typing the command again but still the error msg.

You have to change your directory to the folder you downloaded.  

```
cd ~/Desktop/sane-backends
./configure
make
make install
```

---

### Post by taurus on 2009-12-27
Actually, before you run those commands, you need to first install the build-essential package before you can compile anything from source.  Therefore, run these

```
cd ~/~/Desktop/sane-backends
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure
make
**sudo** make install
-or-
sudo make checkinstall
```

---

### Post by 3rdalbum on 2009-12-27
"./configure" means "run the script called 'configure' in the current directory". So you need to "change directory" into the directory that contains the thing you want to compile.

Open a terminal.

You see the directory that contains the thing you want to compile? Well, in the terminal, type the letters "cd" and press the space bar; and then drag the folder icon to the terminal.

This will fill in the path of the directory. Now switch back to the terminal window and hit Enter.

Now your ./configure command will work, because your terminal is now inside the correct directory.

---

### Post by azitizz on 2009-12-27
> **taurus said:**
> Actually, before you run those commands, you need to first install the build-essential package before you can compile anything from source.  Therefore, run these

```
cd ~/~/Desktop/sane-backends
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure
make
**sudo** make install
-or-
sudo make checkinstall
```
 OH How satisfying!!! My scanner is working now. Thank You Very Much!!!
When I typed "sudo make checkinstall" (because I wasnt sure if I should enter the "sudo make install" in bold or not)
It gave me the following:
> mikepanc@mikepanc-laptop:~/Desktop/sane-backends$ sudo make checkinstall
make: *** No rule to make target `checkinstall'.  Stop.
mikepanc@mikepanc-laptop:~/Desktop/sane-backends$ 
Is this anything to be concerned about?
And if not, now that its working, How do I label this thread as [SOLVED]?
Thank you again and I just grew to love Linux/ubuntu that much more.

---

### Post by azitizz on 2009-12-29
So It only actually worked once and now it does the same thing. If I try to scan from scanimage it gives me an error msg saying "error during device I/O" here is what was done in terminal to test according to the Pixma Linux Blog website:
> mikepanc@mikepanc-laptop:~$ scanimage -L
device `pixma:04A91717_927028' is a CANON Canon PIXMA MP510 multi-function peripheral
mikepanc@mikepanc-laptop:~$ scanimage -T
scanimage: scanning image of size 640x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1920 bytes...	FAIL Error: Error during device I/O
I was excitied for a minute. not sure what happened. The internet disconnects every time I try and it fails for some reason.
Any help would be very gratefully appreciated.

---

