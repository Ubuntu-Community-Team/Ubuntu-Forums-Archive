---
title: "I can't download from YouTube anymore :("
date: 2011-03-13
forum: General Help
---

### Post by WlaadDyaab on 2011-03-13
I used to be able to wait for a YouTube video (that I'm interested in) to fully buffer, then I would go to Places-Computer-File System-tmp

Then I would normally find it there

But now I can't find it there :(

Is there another easy method to download YouTube videos?

I don't know if this is helpful but I've been using Chromium for a very long time and maybe two days ago the Flash player had to be updated and there were (for me) problems with downloading of the Flash player(s):confused:

---

### Post by WlaadDyaab on 2011-03-13
I forgot to mention that I've stopped using Chromium Internet browser, and now I use Seamonkey Internet browser

If you want to know why I can't use Firefox: [http://ubuntuforums.org/showthread.php?t=1705520](http://ubuntuforums.org/showthread.php?t=1705520) > The problem with Firefox is that I'm scared of it Lol. I've never opened Firfow since on the date of this thread - one of my threads: [http://ubuntuforums.org/showthread.php?t=1647731](http://ubuntuforums.org/showthread.php?t=1647731)

---

### Post by ron999 on 2011-03-13
Hi
Think about using **youtube-dl**.

Install it:-
```
sudo apt-get install youtube-dl
```

Then update it:-
```
sudo youtube-dl --update
```

Then learn about it:-
```
youtube-dl --help
```

---

### Post by WlaadDyaab on 2011-03-13
Thanks a lot, I'll search that up now on YouTube tutorials

---

### Post by WlaadDyaab on 2011-03-13
Thank you very much ron999

I done the following:

- Applications > Accessories > Terminal (or ctrl + alt + T)

- On Terminal I copy/paste > sudo apt-get install youtube-dl

- Pressed "Enter" (or "Return")

...

- I copy/paste > sudo youtube-dl --update

- I viewed this tutorial on YouTube: [http://www.youtube.com/watch?v=pRDSqzZXDrI](http://www.youtube.com/watch?v=pRDSqzZXDrI)

- I then went on Terminal again

- I typed > youtube-dl then I copy/paste [http://www.youtube.com/watch?v=pRDSqzZXDrI](http://www.youtube.com/watch?v=pRDSqzZXDrI) right next to "youtube-dl"

- I got this from Terminal > [1] 2542
("My username")-HP-ProBook-4510s:~$ [youtube] Setting language
[youtube] (...........): Downloading video webpage
[youtube] (...........): Downloading video info webpage
[youtube] (...........): Extracting video information
ERROR: unable to download video (format may not be available)

- I pressed "return"

- Got that as extra > [1]+  Exit 1                  youtube-dl [http://www.youtube.com/watch?v=pRDSqzZXDrI](http://www.youtube.com/watch?v=pRDSqzZXDrI)


- I done what you suggested ron999 on this forum: > sudo youtube-dl --update

- Entered my password and pressed "return"

- Got that on Terminal: > Updating to latest stable version...
Updated to version 2011.02.25c

- Again, I entered > youtube-dl in Terminal then I copy/paste [http://www.youtube.com/watch?v=pRDSqzZXDrI](http://www.youtube.com/watch?v=pRDSqzZXDrI)

- This is what showed up in Terminal: > [1] 2761
("My username")-HP-ProBook-4510s:~$ [youtube] Setting language
[youtube] (...........): Downloading video webpage
[youtube] (...........): Downloading video info webpage
[youtube] (...........): Extracting video information
[download] Destination: (...........).flv
[download] 100.0% of 13.16M at   53.38k/s ETA 00:00

In order to get 100%, it shows on Terminal how it loaded from 0% to 100%

(For everyone who's not used to such detailed explanations I apologise, but we have to to present Linux as if the newbies are watching it as we explain the process to them. I was one of the people who learned the hard way; through not getting the fullest of the fullest details, and had to work my way through it. Some people are like that and we have to show them how truly easy it is to use things like command lines for example and that trouble shooting isn't hard)

Next step is to find out where exactly am I going to find my newly downloaded YouTube video

There's two ways:

1. Places > Home Folder

- Then search for the Thumb nail with weird letters and numbers   ending with ".flv"

If you still can't find the YouTube video file there's another way

2. Places > Search for Files...

- Then copy/paste (in my case) > [download] Destination: (...........).flv
[download] 100.0% of 13.16M at   53.38k/s ETA 00:00

(That was listed earlier above) > [1] 2761
("My username")-HP-ProBook-4510s:~$ [youtube] Setting language
[youtube] (...........): Downloading video webpage
[youtube] (...........): Downloading video info webpage
[youtube] (...........): Extracting video information
[download] Destination: (...........).flv
[download] 100.0% of 13.16M at   53.38k/s ETA 00:00

I hope the next person having the same problem benefits from this :)

---

### Post by kenbo on 2011-03-14
Easier way:
With youtube still open:
Open System Monitor
Right click Chrome and select 'Open Files'

You get:
[IMG]http://i53.tinypic.com/334uqdg.png[/IMG]

now use the proc ID (of chrome) and the FD of FlashXX* (deleted)

to cp it where ever you want like so:

[IMG]http://i51.tinypic.com/a15xjc.png[/IMG]

---

### Post by Kirboosy on 2011-03-14
For Firefox users there is an add on called [Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/") which give you a nice button in your Firefox that can download flash videos from many websites. Its also cross platform compatible which is extremely nice. :)

Also FlashAid works really well for FireFox Browsers :) (I'm assuming SeaMonkey has addons? I've never tried it)

---

### Post by scouser73 on 2011-03-14
You can find Youtube videos in the cache folder.  So for users of Firefox it would be in **/home/username/.mozilla/firerfox/6gpfavh9.default/cache**

**6gpfavh9.default** is an example**[COLOR="Red"]**[/COLOR]**

---

### Post by WlaadDyaab on 2011-03-15
> **kenbo said:**
> Easier way:
With youtube still open:
Open System Monitor
Right click Chrome and select 'Open Files'

You get:
[IMG]http://i53.tinypic.com/334uqdg.png[/IMG]

now use the proc ID (of chrome) and the FD of FlashXX* (deleted)

to cp it where ever you want like so:

[IMG]http://i51.tinypic.com/a15xjc.png[/IMG]

Thanks everyone!...Thank you very much for the great support

kenbo I thought that it's a security risk to show anyone about the name of your/my Linux machine name. You know; the one where you see in Terminal: > .....@.....-desktop:~$

I think that's gonna make you laugh Lol

But do you have to be a programmer who has faith in their ability to show their machine name and be ready to fight any Crackers tries to penetrate your system, or is it just simply not harmful to show your Linux machine name in public?

And btw I thank you very much for showing your way of downloading YouTube videos

---

### Post by jerome1232 on 2011-03-15
your machine name is meaningless. It's just a name that may be used to identify itself with other computers on your network.

Knowing what your machines name would not help someone attempting to compromise it one bit.

---

### Post by WlaadDyaab on 2011-03-16
> **jerome1232 said:**
> your machine name is meaningless. It's just a name that may be used to identify itself with other computers on your network.

Knowing what your machines name would not help someone attempting to compromise it one bit.

How come it has to be respected as "root"? And "root" as I know it (with my over view knowledge - not in depth) is where it has the password that no one should ever know

---

### Post by jerome1232 on 2011-03-16
I'm afraid I don't quite understand your question.

root is a user, it's often called the super user because you have the power to do anything to your system as root, comparable to an administrator account on Windows.

Ubuntu by default locks the root account, you cannot log into an Ubuntu system as root, instead it uses a program called sudo which temporarily grants a user rights with their own password as if they were another user, then drops the rights when the task is complete. Only users in the admin group can use sudo to gain rights as if they were any user on the system, including root. By default Ubuntu puts the first user (the user you setup during installation) in that admin group so that you can do administrative tasks, such as installing software.

If you want more info on Ubuntu's security model check this documentation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Script Warlock on 2011-03-16
if you want a simple yotube dl apps use clipgrab or minitube....

---

### Post by WlaadDyaab on 2011-03-16
> **jerome1232 said:**
> I'm afraid I don't quite understand your question.

root is a user, it's often called the super user because you have the power to do anything to your system as root, comparable to an administrator account on Windows.

Ubuntu by default locks the root account, you cannot log into an Ubuntu system as root, instead it uses a program called sudo which temporarily grants a user rights with their own password as if they were another user, then drops the rights when the task is complete. Only users in the admin group can use sudo to gain rights as if they were any user on the system, including root. By default Ubuntu puts the first user (the user you setup during installation) in that admin group so that you can do administrative tasks, such as installing software.

If you want more info on Ubuntu's security model check this documentation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thank you for your great patience with me Lol

Just now I understood what "root" is. When you mentioned that "sudo" grants a normal person (not the admin, where ever he/she is in the world doing the real control of Linux the open source OS...etc) the temporary privileges of using "root", I understood what it meant, or a considerable amount about the security of Linux

That Linux is more like a CPU somewhere far, and that our computer systems are more like applications

And not systems of their own CPU (or "Kernel")

If my understand is right - thank you ever so much for explaning (using some of your valuable time) :)

Otherwise please correct me

---

### Post by WlaadDyaab on 2011-03-16
> **Script Warlock said:**
> if you want a simple yotube dl apps use clipgrab or minitube....

I tried playing normal YouTube vids but it wouldn't allow me to even do that?!

[ATTACH]186225[/ATTACH]

Is Minitube used for viewing and downloading or just downloading?

---

### Post by Script Warlock on 2011-03-16
you can do both.. clipgrab is for downloading/converting the target youtube files.

---

### Post by Rasa1111 on 2011-03-16
Or..
 If one uses chrome(ium),,
They can simply install this extension in chrome [https://chrome.google.com/extensions/detail/eikdkjbibneomfiolphbiiekinadfaip](https://chrome.google.com/extensions/detail/eikdkjbibneomfiolphbiiekinadfaip)

 It will give all youtube videos a "download" button. 

If you want to keep it, just click "download" , choose your quality, and it will download to your machine.

---

### Post by WlaadDyaab on 2011-03-16
> **Script Warlock said:**
> you can do both.. clipgrab is for downloading/converting the target youtube files.

Heey that's great!

OK here goes:

- I found this YouTube tutorial: [http://www.youtube.com/watch?v=HTA7smqOBUY](http://www.youtube.com/watch?v=HTA7smqOBUY)

- Typed "clipgrab for ubuntu" in Google

- Clicked on the first link that got me to here: [http://www.ubuntugeek.com/clipgrab-download-online-videos.html](http://www.ubuntugeek.com/clipgrab-download-online-videos.html)

- Opened Terminal:
  Applications > Accessories > Terminal (or ctrl + alt + T)

- Copy/paste this in Terminal: > sudo add-apt-repository ppa:clipgrab-team/ppa

- Typed my password (that can't be seen to me)

- Pressed "Enter" (or "return key")

...

- This happened: > Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4496BE64A6BEE4CD4BEEE744D8AD4DE78EEBB0CA
gpg: requesting key 8EEBB0CA from hkp server keyserver.ubuntu.com
gpg: key 8EEBB0CA: public key "Launchpad ClipGrab PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


- Then I copy/paste this command: > sudo apt-get update

...(it done the usual sexy updating codes that I love to see Lol)

- Then I copy/paste this command too: > sudo apt-get install clipgrab

- This happens: > Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavcodec-unstripped-52
The following NEW packages will be installed
  clipgrab libavcodec-unstripped-52
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 242kB of archives.
After this operation, 524kB of additional disk space will be used.
Do you want to continue [Y/n]?

...(I press "y" on my keyboard, then I press the "return key")

- Now this will show: > Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse libavcodec-unstripped-52 i386 4:0.6-2ubuntu3 [43.3kB]
Get:2 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/) maverick/main clipgrab i386 3.1.0.1~maverick1 [198kB]
Fetched 242kB in 0s (642kB/s)                                                
Selecting previously deselected package libavcodec-unstripped-52.
(Reading database ... 274507 files and directories currently installed.)
Unpacking libavcodec-unstripped-52 (from .../libavcodec-unstripped-52_4%3a0.6-2ubuntu3_i386.deb) ...
Selecting previously deselected package clipgrab.
Unpacking clipgrab (from .../clipgrab_3.1.0.1~maverick1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Setting up libavcodec-unstripped-52 (4:0.6-2ubuntu3) ...
Setting up clipgrab (3.1.0.1~maverick1) ...

- To find ClipGrab on my Ubuntu system: I simply watched the YouTube tutorial again Lol [http://www.youtube.com/watch?v=HTA7smqOBUY](http://www.youtube.com/watch?v=HTA7smqOBUY)

- Applications > Internet > ClipGrab

- I open ClipGrab and just click on the "Downloads" tab

- Then I copy/paste this into ClipGrab's URL bar: [http://www.youtube.com/watch?v=HTA7smqOBUY](http://www.youtube.com/watch?v=HTA7smqOBUY)

[ATTACH]186228[/ATTACH]

- Next I edit the following drop-down menu's:
  Format: MPEG4
  Quality: HD (720p) *that's already by default*
  Grab this clip!: You're free to choose whatever directory you want this to do to. I normally choose "Desktop", then click on "Save"

Done!

It'll download to your directory. And in my case: I check my Desktop and there it is!

[ATTACH]186229[/ATTACH]

Note: I'm doing these detailed step-by-step instruction for future reference. For people who are new to Linux so they can learn and see how simple Linux is :)

---

