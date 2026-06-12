---
title: "How do you install Wunderlist"
date: 2011-09-20
forum: General Help
---

### Post by ernestj on 2011-09-20
Sorry, I am still new to Linux. I am trying, I learn something new everyday. I am trying to install Wunderlist. I went to the website and downloaded the .tgz file, extracted it, used file manager to open the file. It asks me which program to use. Help. How do I do "run" this file?
Thanks,
Ernie

---

### Post by wildmanne39 on 2011-09-21
Hi, I went and downloaded the file but I could not extract it because it is for 32 bit and I am running 64 bit ubuntu.

You need to look at the read me file it will tell you how to install it.
Thank you

---

### Post by sub sexy on 2011-09-24
ernestj,

I was able to easily run Wunderlist on my Ubuntu 11.04 64 bit. Download the file "wunderlist-1.2.4-linux-64.tgz from Wunderlist website. Link: [http://www.6wunderkinder.com/downloads/wunderlist-1.2.4-linux-64.tgz](http://www.6wunderkinder.com/downloads/wunderlist-1.2.4-linux-64.tgz)

Once download right lick on the file and select extract here or double click to open the file in the archive manager. Extract the contents of the file and you will now have a folder called "Wunderlist-1.2.4. Go into the folder and look for the file name "Wunderlist" and just double click and the Wunderlist application will open. 

Hope this helps.

---

### Post by s1d on 2011-09-25
> **ernestj said:**
> Sorry, I am still new to Linux. I am trying, I learn something new everyday. I am trying to install Wunderlist. I went to the website and downloaded the .tgz file, extracted it, used file manager to open the file. It asks me which program to use. Help. How do I do "run" this file?
Thanks,
Ernie
I was having similar trouble. The issue seems to be with permissions. The trick is to first make sure that the "Wunderlist" launcher file is executable using chmod +x and then enter root mode and launch it from the shell. For the uninitiated, open shell and change to the Wunderlist directory and run following commands :

```

$ chmod +x Wunderlist
$ sudo -s   <enter password on prompt>
# ./Wunderlist  

```

---

### Post by ClientAlive on 2011-09-25
FWIW I came across something recently that may be useful to you. While it is a bit old the information is pretty general (but technical too). While it may not address your specific issue, the information it contains may help you figure out what to do to solve the problem. In any case it's not a huge read. Take a peek if think it might help.

[http://www.tldp.org/HOWTO/Software-Building-HOWTO.html](http://www.tldp.org/HOWTO/Software-Building-HOWTO.html)


;)

---

### Post by SecretCode on 2011-09-30
I'm finding that I can only run Wunderlist using sudo and this (of course) is unacceptable.

Report posted here: [Wunderlist | Unable to run Wunderlist on Linux without sudo](http://support.wunderlist.com/customer/portal/questions/46241-unable-to-run-wunderlist-on-linux-without-sudo)

---

### Post by ClientAlive on 2011-10-01
> **SecretCode said:**
> I'm finding that I can only run Wunderlist using sudo and this (of course) is unacceptable.

Report posted here: [Wunderlist | Unable to run Wunderlist on Linux without sudo](http://support.wunderlist.com/customer/portal/questions/46241-unable-to-run-wunderlist-on-linux-without-sudo)


Hmmm . . .

I've never run into a situation like that before but the first thing I thought when I read that is 'permissions' and wundered if user space applications are supposed to be owned by root or by the user. I did a

```

ls -la /usr/bin

```

(from my home directory) only to discover that all the apps in that directory are, in fact, owned by root. There are also some programs that install to a different directory (such as thunderbird, which installs to your home directory as a hidden file). So, just to check it out, I also did a

```

ls -la

```

(while in my home directory of course). What I saw was that all the apps installed there (and there are a considerable number of them) are owned by me, the user.

This makes me wunder about your wunderlist  :p. Where is it installed and who owns it? Who is supposed to own it? If it is owned by root, is it possible that doing a

```

chown uname:groupname

```

to change the ownership to your uname and groupname would solve your problem?

Be careful with chown. Make sure you use it right if you are going to use it. It can bite you if you don't.


HTH

---

### Post by doublewitt on 2011-10-02
very nice application...!! :D

---

### Post by SecretCode on 2011-10-02
ClientAlive: I've tried installing it in /opt (and running chown -R me:me) on it; and in my home folder. Same results each time.

Run with sudo, the first time it runs it puts up a licence agreement window and thereafter it remembers it. Run without sudo, it always shows the licence agreement window and then crashes. I'm pretty sure this means it's writing its config data to some location that a regular user does not have access to, but so far I have not been able to find out what it is (no clues from find ... -mmin -5).

---

### Post by doublewitt on 2011-10-02
Maybe it has something to do with the folder location where it was extracted to. Myself, I downloaded it and extracted it to the system DOWNLOADS folder and it works just fine from there... I even created a launcher on the system panel and it works.

and maybe it has nothing to do with that - but just trying to help...! :-k

---

### Post by ClientAlive on 2011-10-02
> **SecretCode said:**
> ClientAlive: I've tried installing it in /opt (and running chown -R me:me) on it; and in my home folder. Same results each time.

Run with sudo, the first time it runs it puts up a licence agreement window and thereafter it remembers it. Run without sudo, it always shows the licence agreement window and then crashes. I'm pretty sure this means it's writing its config data to some location that a regular user does not have access to, but so far I have not been able to find out what it is (no clues from find ... -mmin -5).


Hmmm. Yeah, I probably should have done it before that last post, but I went to their website - even downloaded and extracted the program (Linux version) and poked around in there just briefly. I wasn't aware of it before then but I saw it looks like a windoze app. I've seen other programs like that, that were made to work for Linux, just not familiar with how they do it. I would think a dev would recompile the source for our platform to achieve the result, heck, maybe that is what they did with Wunderlist. Anyhow. I wish you the best of luck. If I have time I might poke around in the program again. I'm not an experienced programmer though.

:)

---

### Post by SecretCode on 2011-10-04
Update - I've tested the installation in freshly installed Ubuntu vms. Apart from first having to install curl, in 64bit Maverick and Natty I get exactly the situation I've described.

In 32 bit Natty it works fine. The local data all seems to be installed in ~/.titanium/Wunderlist/.

Does anyone have the 64 bit version of Wunderlist running successfully?

---

### Post by fank1 on 2011-10-05
I have also installed curl, because it seems to be required:

```
$ ./Wunderlist 
/home/xy/Wunderlist-1.2.4/installer/installer: error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory

```

After installing curl, when I run the Wunderlist executable from a console in Natty 64 bit, I get a segmentation fault.

---

### Post by CarlosFerreira on 2011-10-17
I read - on OMG Ubuntu, I believe - that it was supposed to be on the Software Centre. Remember seeing some screenshots and all. However, I can't find it there. Can anybody confirm if they have the same issue?

---

### Post by doublewitt on 2011-10-20
I wunder if it's in the software center only in the latest Ubuntu version. Could that have anything to do with it? I'm running 10.04 LTS and it's NOT in the software center - even after updates...

On the Wunderlist blog, it also states that it's available in the Ubuntu software center. For me it's not working. Nonetheless, I was able to install it with the downloaded file.

Wow - that "smart date recognition" is really nice & easy to use... the 1st time I've seen such a clever way to enter tasks. 
:D

---

### Post by CarlosFerreira on 2011-10-23
> **doublewitt said:**
> I wunder if it's in the software center only in the latest Ubuntu version. Could that have anything to do with it? I'm running 10.04 LTS and it's NOT in the software center - even after updates...

On the Wunderlist blog, it also states that it's available in the Ubuntu software center. For me it's not working. Nonetheless, I was able to install it with the downloaded file.

Wow - that "smart date recognition" is really nice & easy to use... the 1st time I've seen such a clever way to enter tasks. 
:D

Can't find it on the Software Centre for either 10.04 LTS or 11.10. Both 32-bit - I wonder if the version on the Software Centre is only for 64 bit?

---

### Post by collisionystm on 2011-11-16
I just figured this out. Hope it helps someone.

INSTALLING WUNDERLIST ON UBUNTU 11.10 ONEIRIC x64

open a new Terminal

```
cd Downloads
``````
wget http://www.6wunderkinder.com/downloads/wunderlist-1.2.4-linux-64.tgz
``````
tar -xf wunderlist*

``````
sudo mv Wunderlist* Wunderlist
``````
sudo cp -R Wunderlist/ /opt
``````
sudo chmod -R 770 /opt/Wunderlist
``````
sudo chown -R YOURUSERNAME /opt/Wunderlist
``````
sudo cp /opt/Wunderlist/Resources/wunderlist.png /usr/share/pixmaps/
``````
gksudo gedit /usr/share/applications/wunderlist.desktop
```Paste this and save it

> [Desktop Entry]
Encoding=UTF-8
Name=Wunderlist
Exec=/opt/Wunderlist/Wunderlist
Icon=/usr/share/pixmaps/wunderlist.png
Terminal=false
Type=Application
Categories=Application;Office;
StartupNotify=false
```
sudo apt-get install curl
``````
sudo apt-get install libnotify4
``````
sudo cp /usr/lib/x86_64-linux-gnu/libnotify.so.4.0.0 /usr/lib/libnotify.so.1
``````
sudo apt-get install libffi6
``````
sudo cp /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0 /usr/lib/libffi.so.5
``````
sudo apt-get install libxss1
```You should now be able to open the Unity dash and type Wunderlist.

Click and it should open.

If it fails

Open terminal and run it manually to see what errors you get
```

cd /opt/Wunderlist/
``````

./Wunderlist
```

---

### Post by skullmunky on 2012-07-28
I had the same problem in Kubuntu 12.04 - I can run Wunderlist using sudo, but not as a regular user.  I solved it by launching once with sudo, then copying the preferences directory over to my normal user account.

First, I followed these instructions:

[http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html](http://www.webupd8.org/2012/01/how-to-install-wunderlist-in-ubuntu.html)

Launching as a regular user gave a segmentation fault:

```

ben@B-MBP-i7:/opt/Wunderlist-1.2.4$ ./Wunderlist 

(process:13382): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (32) on option of arg-type 4 in entry (null):updatefile

(process:13382): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (32) on option of arg-type 1 in entry (null):type

(process:13382): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (32) on option of arg-type 0 in entry (null):sudo

(process:13382): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (32) on option of arg-type 5 in entry (null):
Gtk-Message: Failed to load module "canberra-gtk-module"

(installer:13382): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(installer:13382): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Segmentation fault (core dumped)

```

However, running as root works fine:

```

cd /opt/Wunderlist-1.2.4/
sudo ./Wunderlist

```

messing around with file permissions didn't solve anything, but instead I found that copying over the Wunderlist prefs that got created when I ran as root made it work.

```

sudo cp -r /root/.titanium ~
sudo chown -R skullmunky:skullmunky ~/.titanium

```

obviously edit the chown command to be your username, otherwise I owns yr wunderlist :)

---

