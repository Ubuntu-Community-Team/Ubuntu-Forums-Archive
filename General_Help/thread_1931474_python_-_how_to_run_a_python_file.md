---
title: "python - how to run a python file?"
date: 2012-02-25
forum: General Help
---

### Post by dockalek on 2012-02-25
Hi, could anyone please look at the script below? I coppied some python script that should solve my problem with skype, but somehow I can't run it. Please have a look if i am doeing that properly. As seen, I should be in the right directory, so tell me, where the mistake is,

georgi@georgi-Studio-1537:~$ cd ~/Templates
georgi@georgi-Studio-1537:~/Templates$ ls
 skyppe.py   skyppy.py~
georgi@georgi-Studio-1537:~/Templates$ python skyppe.py
python: can't open file 'skyppe.py': [Errno 2] No such file or directory
georgi@georgi-Studio-1537:~/Templates$ 

Thanx

ps. I have it downloaded ok

georgi@georgi-Studio-1537:~$ sudo apt-get install python
[sudo] password for georgi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
georgi@georgi-Studio-1537:~$

---

### Post by Khayyam on 2012-02-25
dockalek ..

Are you sure its a python file. What does the following show:

```
cat skyppe.py | head -1
```

It should show something like "#!/usr/bin/env python" or "#!/usr/bin/python" or "#!/usr/bin/python2".

It's possible that you downloaded a html file (404 or something) rather than the file itself, or its pointing to the wrong "python".

HTH ... khay

---

### Post by dockalek on 2012-02-25
well it says the same
georgi@georgi-Studio-1537:~$ cat skyppe.py | head -1
cat: skyppe.py: No such file or directory

I copied it from here 
[http://ubuntuforums.org/showthread.php?t=1011348&highlight=skype+single+instance](http://ubuntuforums.org/showthread.php?t=1011348&highlight=skype+single+instance)

Could you tell me how to actually download that so that it would be a python file? That would be great.

---

### Post by baumanno on 2012-02-25
dockalek,

copy the code from the forum-post, fire up gedit/kate/<your-favourite-text-editor> and paste the code into that, then save it as .py

Then do
```

$ chmod +x skyppe.py
$ python skyppe.py

```

Any luck?
PS: [This]("http://ubuntuforums.org/showthread.php?t=1851256") was recommended in the link you gave us, so just bear that in mind...

---

### Post by dockalek on 2012-02-25
baumanno,

sorry for such stupid question, but does "fire up" mean the same thing as "open"?:)  Shall I just open gedit and coppy that? Because that's what I did last time.

---

### Post by WorMzy on 2012-02-25
Are you sure the file exists in your home directory?

```
ls ~
```

---

### Post by baumanno on 2012-02-25
Yeah, it means open :)
Well, thats strange... I just did the following:
1. copied the code from the link you supplied
2. opened gedit, pasted the code in and 'save as...' skype.py
3. and running 'python skype.py' gives me an instance of skype...

---

### Post by dockalek on 2012-02-25
baumanno,
All right, it works now. The bad thing is that still it doesn't launch and says there's another instance running. Thank you though. Hopefully tmrw i will manage the rest of it.

---

### Post by baumanno on 2012-02-25
To tackle that, just do a
```

$ killall skype

```
to get rid of all running instances; then run the .py-script again.
Glad to be of service :)
Cheers

---

### Post by dockalek on 2012-02-26
Hi again,
still no success. I coppied the script to usr/lacal/bin when I run it, it still has the same problem, that there might be another instance. There is not though. I killall skype, look in the system monitor, and it seems there's no skype, but then I run the python file and it is just the same as before. any ideas? thanks 

Also, that guy here [http://ubuntuforums.org/showthread.php?t=1851256](http://ubuntuforums.org/showthread.php?t=1851256)
recomends to edit main menu and add a connection. I have no idea, what he means. But anyway, that would be the next step, and the main problem is not solved for me.

---

### Post by baumanno on 2012-02-26
Hey,

have you tried
```
$ ps aux | grep skype 
```
to see whether there really are no processes? Optionally, a good old
```
$ sudo killall skype
```
would take care of any rogue instances.
If that doesn't do the trick, I'm totally lost :confused:

---

### Post by dockalek on 2012-02-26
It is all the same: 
georgi@georgi-Studio-1537:~$  ps aux | grep skype
georgi    3157  0.0  0.0  13448   900 pts/0    S+   20:23   0:00 grep --color=auto skype
georgi@georgi-Studio-1537:~$ sudo killall skype
[sudo] password for georgi: 
skype: no process found
georgi@georgi-Studio-1537:~$ cd ....
bash: cd: ....: No such file or directory
georgi@georgi-Studio-1537:~$ cd ..
georgi@georgi-Studio-1537:/home$ cd ..
georgi@georgi-Studio-1537:/$ cd usr
georgi@georgi-Studio-1537:/usr$ cd local
georgi@georgi-Studio-1537:/usr/local$ cd bin
georgi@georgi-Studio-1537:/usr/local/bin$ python skype.py

But I tried to remove skype and install it again, and in the ubuntu software centre there it is twice, the same skype, two icons just next to each other, and if you click on one of them, then in the "installed software" there are two icons of skype again. Could't this be the problem? Or is there some good reason why it is there twice?

---

### Post by baumanno on 2012-02-26
```

$ sudo apt-get purge skype

```

This removes skype and global configuration. Then see whether

```

$ dpkg --get-selections | grep skype

```
lists any occurences.

---

### Post by dockalek on 2012-02-26
georgi@georgi-Studio-1537:~$ sudo apt-get purge skype
[sudo] password for georgi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libkrb5-3:i386 libk5crypto3:i386 libstdc++6:i386
  libqt4-declarative:i386 liblcms1:i386 libwrap0:i386 libsamplerate0:i386
  libqt4-script:i386 libqt4-network:i386 libqt4-dbus:i386
  libjack-jackd2-0:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386
  sni-qt:i386 libexpat1:i386 libqt4-xmlpatterns:i386 libavahi-common-data:i386
  libjson0:i386 libxcb1:i386 libxau6:i386 libcups2:i386 libqtcore4:i386
  libkrb5support0:i386 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386
  libgcrypt11:i386 libkeyutils1:i386 libqt4-sql:i386 libasound2:i386
  libflac8:i386 libxrender1:i386 libvorbisenc2:i386 libqt4-xml:i386
  libasyncns0:i386 libxss1:i386 libtiff4:i386 libpng12-0:i386 libjpeg62:i386
  libqtgui4:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libsm6:i386 libpulse0:i386 libgssapi-krb5-2:i386 libxi6:i386
  libvorbis0a:i386 libaudio2:i386 libxt6:i386 libxv1:i386 libxext6:i386
  libavahi-common3:i386 libsndfile1:i386 libmng1:i386 libasound2-plugins:i386
  libgpg-error0:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  skype:i386*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 29.9 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 154658 files and directories currently installed.)
Removing skype:i386 ...
Purging configuration files for skype:i386 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
georgi@georgi-Studio-1537:~$ dpkg --get-selections | grep skype
georgi@georgi-Studio-1537:~$

---

### Post by dockalek on 2012-02-26
There's one new thing I found out though. When I tried it from standart account, it worked. With problem described in other threads but it worked at least. So maybe I will just work in the starndart account and log in in administrative to do the software administrative only.

---

### Post by baumanno on 2012-02-26
So that at least got rid of skype...
In general, it is no good practice to keep working as root, use it wisely and only when neccessary.
But what's the status now? As the 'normal' user, can you run the python-script or skype successfully after reinstalling it via 
```
$ sudo apt-get install skype
```
? If you're happy with the result please mark this thread as solved with the thread tools.

Cheers

---

### Post by dockalek on 2012-02-27
baumanno,
Yes it works. So the python part is solved indeed. THANK YOU. I keep having problems with the rest, so if you fancy helping me, I keep asking here: 
[http://ubuntuforums.org/showthread.php?t=1931911](http://ubuntuforums.org/showthread.php?t=1931911)
thanx for your patience

---

