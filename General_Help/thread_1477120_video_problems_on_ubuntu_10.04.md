---
title: "video problems on ubuntu 10.04"
date: 2010-05-08
forum: General Help
---

### Post by shayli147 on 2010-05-08
yesterday i upgraded my ubuntu to 10.04 LTS - the Lucid Lynx, and today i faced with a problem watching videos on the Internet. i already tried reinstalling the Adobe Flash Player i have in many ways... nothing helped and i actually think it isn't even related to the flash player... what can it be, and how can it be fixed?

thanks for helpers:)

---

### Post by shayli147 on 2010-05-08
well maybe that is related to flash because flash games aren't working too..
help please T-T

---

### Post by lidex on 2010-05-08
Try this in a terminal="Applications->Accessories->Terminal"```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
```
Restart your browser and go here to use the flash installer:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by shayli147 on 2010-05-09
i've done all the sudo commands, but i don't understand the link... i tried to download these but wasn't successful... i see a software icon, and when i try to open it, nothing happens..
what is this link? how should i use it? why doesn't it work? (i'm sorry for asking so much..)

---

### Post by shayli147 on 2010-05-11
i tried to install flash player normally once again, still doesn't work. help please.. what else can i try?

---

### Post by shayli147 on 2010-05-11
i gotta have this flash soon, i use it in my projects which i have to hand by may 20th.... can somebody help me please?....

---

### Post by kokonobs on 2010-05-11
Are u running the 64bit version? If you are then use this, I had issues too: 

[http://mattrudge.wordpress.com/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/](http://mattrudge.wordpress.com/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/)

I dont know your proficiency level but just follow the instructions. Where it says execute the script just type:

./native-64bit-flash-installer.sh

---

### Post by shayli147 on 2010-05-11
> **kokonobs said:**
> Are u running the 64bit version? If you are then use this, I had issues too: 

[http://mattrudge.wordpress.com/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/](http://mattrudge.wordpress.com/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/)

I dont know your proficiency level but just follow the instructions. Where it says execute the script just type:

./native-64bit-flash-installer.sh
thank you! it is working now:) i didn't know what version i was running... but if it worked i guess it's 64bit :)
again, thank you very much!

---

### Post by shayli147 on 2010-05-11
ok... i have no idea what went wrong, but i cant use flash once again. tried to do the same once again, didn't work, tried to download from the website once again, didn't work. it is really important that flash would work for me... really

---

### Post by kokonobs on 2010-05-12
Oh... Sorry...

I'm a noob myself so i wont try to offer any more solutions. The best thing i'll say is this. Give more details about your system configuration so the experts can be of better help. And try to find out whether you are actually using the 64bit version.

From my noob perspective, using synaptic or the ubuntu software store, remove all instances of the flash player before you follow the earlier steps again. and make sure your browser is closed when you do.

---

### Post by shayli147 on 2010-05-12
> **kokonobs said:**
> Oh... Sorry...

I'm a noob myself so i wont try to offer any more solutions. The best thing i'll say is this. Give more details about your system configuration so the experts can be of better help. And try to find out whether you are actually using the 64bit version.

From my noob perspective, using synaptic or the ubuntu software store, remove all instances of the flash player before you follow the earlier steps again. and make sure your browser is closed when you do.
no you are not a noob, this isnt your fault i have this bug OO i still really appreciate your help :)
i don't know about my system much, and don't know how to find out... i'm new to linux heh

---

### Post by kokonobs on 2010-05-13
There is the ubuntu manual here:

[https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)

You can then get a package called Sysinfo which can tell you more about your system.

---

### Post by shayli147 on 2010-05-14
wow thank you for your help, i appreciate it:) i tried to download and i faced with a msg:
[B]
"Access forbidden![/B]
            You don't have permission to access the requested object.     It is either read-protected or not readable by the server.      
  If you think this is a server error, please contact the [EMAIL="webmaster-vrac@iastate.edu"]webmaster[/EMAIL].  
  **Error 403**
    [www.vrac.iastate.edu]("http://www.vrac.iastate.edu/")
  Apache/2.0.52 (Red Hat)"

which wasn't so nice to meet heh...
i guess i'll just have to ask for more time to hand my project and wait untill Ubuntu will release a formal solution:) and i think i have 32 bit btw hehe

---

### Post by DaveTap on 2010-05-15
Try downloading [www.ubuntu-tweak.com](www.ubuntu-tweak.com) it should install almost automatically, has a lot of fixes and also can tell you a lot about your configuration. It can also install repository for latest flash plug-in under "Software Sources"

---

### Post by shayli147 on 2010-05-16
yea... i have Ubuntu-tweak, it doesn't work from there neither :( i  really dunno what that is... whatever that is, it's really annoying.. i  think i'll open another post and ask for more help... this one is too  long, doesn't seem to attract many helpers :(
[U]
thanks to every one who tried to help me until now:)[/U]

it is depressing, why the heck this doesn't work??

---

### Post by lidex on 2010-05-16
You may have conflicting plugins. Go to this thread:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
Follow the instructions in the first post. Still no joy? Read through the thread - there are posts there from any number of people who have had these issues.

---

### Post by shayli147 on 2010-05-16
thanks for the link :) i ran the command -  file /sbin/init  - then i found that i have the 32-bit version, and not the 64-bit version most threads refer to.. :) but still, it doesn't work no matter what i try.. :(

---

### Post by lidex on 2010-05-16
Close your browser (copy this info somewhere first). Run these commands:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove flashplugin-installer
```

Now these:
```
sudo updatedb
locate libflashplayer.so
```

Delete any instances that are still found.
To check they are gone, run the last two commands again. With no libflashplayer.so on your system report back.

---

### Post by shayli147 on 2010-05-16
i tried what you had wrote for me and afterwards installed the flash player once again, flash still doesn't work. maybe are there settings i need to change/fix? should i try the above once again?

---

### Post by Alican Kutlu on 2010-05-18
Hi. My problem is quite different. I could watch videos without any problems which are saved in my computer. On the contrary, I have a restriction videos in web pages. If I minimise the web video page to the panel, after a little time, the video vanished. I see a grey image instead of the video. What is your suggestions?

One more thing. As long as video page is on the top of my screen, I have no problem.

---

### Post by Orange Kingdom on 2010-05-18
> **shayli147 said:**
> i tried what you had wrote for me and afterwards installed the flash player once again, flash still doesn't work. maybe are there settings i need to change/fix? should i try the above once again?


Type in your url bar in firefox: about : plugins (without the spaces) , then hit enter
Then look if there is an instance of the flashplyaer and which version.
If none or not working try this:

copy the libflashplayer.so  to /usr/lib/mozilla/plugins/

$sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

restart firefox


I have Shockwave Flash 10.0 r42  (64bit)

---

### Post by shayli147 on 2010-05-19
as i see from that page i have flash installed:
**Shockwave Flash**
File:  dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so
Version:   Shockwave Flash 10.0 r22

but it doesn't work heh..

i found the libflashplayer.so in /usr/lib/flashplugin-installer, i can't copy it into /usr/lib/mozilla/plugins/ for a reason i don't know..

---

### Post by Orange Kingdom on 2010-05-22
> **shayli147 said:**
> as i see from that page i have flash installed:
**Shockwave Flash**
File:  dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so
Version:   Shockwave Flash 10.0 r22

but it doesn't work heh..

i found the libflashplayer.so in /usr/lib/flashplugin-installer, i can't copy it into /usr/lib/mozilla/plugins/ for a reason i don't know..

I think you have the wrong file (Windows??)
Download the player from adobe (Linux).
Copy the file to /usr/lib/mozilla/plugins  (as root)

---

### Post by shayli147 on 2010-05-23
I did download the right file, for linux O.O
How do i copy it as root?

---

### Post by lidex on 2010-05-23
> **shayli147 said:**
> I did download the right file, for linux O.O
How do i copy it as root?

```
sudo cp /path/to/libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by shayli147 on 2010-05-24
this is what i got:
vava@vava-desktop:~$ sudo cp /path/to/libflashplayer.so /usr/lib/mozilla/plugins/
[sudo] password for vava: 
cp: cannot stat `/path/to/libflashplayer.so': No such file or directory

---

### Post by lidex on 2010-05-24
This section needs to be changed to the actual location of the file
```
/path/to/libflashplayer.so
```

---

