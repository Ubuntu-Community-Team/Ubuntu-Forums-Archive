---
title: "&quot;starter documentation&quot; - newbies, please help!"
date: 2004-10-21
forum: General Help
---

### Post by im_ka on 2004-10-21
being the "computer guy" among my friends, i am always being asked about linux... i've ordered 15 ubuntu cd's to liberate some desktops.

i've installed several distros a i-don't-know-how-many times, so -for me-  installing/setting up ubuntu wasn't an issue at all, and i haven't really used winblows for almost a year. but that doesn't mean that my friends (coming from winblows) won't have any issues. i'm thinking about preparing a little "starter documentation" for them...

this is where you (newbies) come into the picture. tell me what i should include in this lil' doc!

1. have you had problems with setting up dualboot? if yes, what problems?

2. any issues installing ubuntu?

3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult?

4. where do you go on the internet if you need help/info (apart from this forum :))? what websites should i include in "link collection"

5. have you find the linux-equivalents for your "favourite" winblows apps?  talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for?

6. do you still use winblows? if not, how long did it take for you to become "100% open source"?

+1. any other suggestions what the "starter-documentation" should include? any areas you've had/are having difficulties?

thanks in advance for your help!

ps: all the linux gurus out there are also welcome to post suggestions.

---

### Post by adbak on 2004-10-21
I had a little trouble setting up the partitions for dual-booting with WinXP.  I didn't quite know what "automatic partitioning" would do nor any of the other suggestions there were on that screen.  I had previously used only Fedora Core so I wasn't used to not-so-graphical installations, although Ubuntu's was somewhat easy (compared to others, I hear).  When you write about this, make sure to explain what a partition is, what a swap partition is, if you should make a fat32 partition to share files, etc.

Another thing I think your documentation should have is how to install Debian packages (dpkg -i ....) and, if you wish, how to convert rpm's into debs.

Perhaps you could even teach how to use the wiki easier.

---

### Post by im_ka on 2004-10-22
thanks for your ideas.

---

### Post by natefish on 2004-10-22
Im a newbie that made a final switch to "linux" when I installed ubuntu. The only thing that has been a problem is video support as a plug-in to firefox, luckily with some great directions in these forums I was able to install the necessary stuff to get things running right. 

For a newbie the look and feel is important, with most linux installs the cognative overload with all the packages intstalled by default makes the overall experience hard to take in. With unbuntu only a minimal set of packages are installed, making things a lot easier.

---

### Post by im_ka on 2004-10-24
bump :)

---

### Post by negativ on 2004-10-31
> **im_ka]
1. have you had problems with setting up dualboot? if yes, what problems?[/quote]

Yes, but I was able to solve them.

Details:

I have an ABIT KT7A-RAID motherboard.  It has 4 IDE ports said:**
> 2. any issues installing ubuntu?
Apart from the above, the actual installation was effortless.


> 3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult?

Not exactly 'difficult', but at first some of the customization did not seem as obvious as it could have been, particularly compared to Suse.

The only big headache I still have is the fact that I cannot get sound to come through the rear channel of my sound card (Turtle Beach Santa Cruz).  I don't really care if I have "true" surround sound; just copying the front channel to the rear channel would be excellent, but I can't get it to work.

> 4. where do you go on the internet if you need help/info (apart from this forum :))? what websites should i include in "link collection"

this forum, google.com, and the forums at arstechnica.com.


> 5. have you find the linux-equivalents for your "favourite" winblows apps?  talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for?

I still need a good usenet reader... in particular, I would like a Linux clone of Forte Agent.  I haven't really spent a whole lot of time trying out Linux news clients, so maybe there's something out there I haven't found just yet.

I also haven't delved into CD burning, or audio CD ripping just yet.  I use Nero under Windows, and Exact Audio Copy for making Vorbis and MP3 from music CDs.

Really, though, games are 90% of the reason I still use Windows.  


> +1. any other suggestions what the "starter-documentation" should include? any areas you've had/are having difficulties?

A guide specifically for Windows refugees explaining how to do certain things in Ubuntu would be nice, and would help the learning curve along.  I don't mean just simple things like "where's the start button", but things like "is there a Device Manager in Ubuntu", "how do I install / remove / change device drivers", etc.

---

### Post by cacofonix on 2004-10-31
This is a good idea im_ka :) I think what might be a good idea to include is everything an unsure Windows convert takes for granted and to help make the move to linux easier. Some things I had trouble with when I relocated was how to set up a media player including getting the codecs and how to configure them how to configure email programs etc.

---

### Post by Zundfolge on 2004-11-03
[QUOTE=im_ka]1. have you had problems with setting up dualboot? if yes, what problems?[/quote]
Nothing but problems ... Grub just refuses to work ... Finally got LILO to install, but it doesn't give me a menu, just boots Ubuntu (with an "error 0x40", so I think it might be a bios problem). I have Mandrake on my second drive, but will need to put WinXP back on the second drive.

> 3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult?
DNS is a pain on every Linux machine I've ever set up ... Windows, Mac OS (9 and X) both seem to be able to autoconfigure, but for some reason I have to screw with the settings six ways from Sunday to get it to work on Linux (although I've gotten much better at that part so it doesn't bother me as much)

> 4. where do you go on the internet if you need help/info (apart from this forum :))? what websites should i include in "link collection"
Other then this forum, I found that just dumping a question into Google would get me an answer 8 times out of 10

> 5. have you find the linux-equivalents for your "favourite" winblows apps?  talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for?

6. do you still use winblows? if not, how long did it take for you to become "100% open source"?
I actually prefer gaim to any other ICQ client I've used (well, Trillian is pretty nice) so I'm using it on my Windows machine at work.

I'm a Graphic Designer, so the one thing that has kept me from going 100% Linux is Adobe (although there was good news on /. about Adobe and Linux today [[click]](http://linux.slashdot.org/linux/04/11/03/159225.shtml?tid=152&tid=187&tid=185&tid=106) )My wife has a Mac, so I can live without Adobe on my Linux machines. I've never liked Gimp (sorry Gimp fans) but Photoshop runs fine under Wine. I'm hoping Wine sets up as easy under Ubuntu as it did under Mandrake.

There just is no substitue for InDesign or Illustrator (no, Scribe isn't even close ... maybe if I went back in time to 1992 with the newest version of Scribe, it might be a little more powerful then QuarkXpress).

> +1. any other suggestions what the "starter-documentation" should include? any areas you've had/are having difficulties?
On Windows and Mac OS I'm pretty much a serious "Power User" ... one of the biggest problems I have with Linux is that I can't "visualize" the file system ... a more detailed explanation of the file system would be nice (I'd like to know what goes where and why) Also I'd like to know if there is some way to invoke root in Nautilus (yes, I'm still a "GUI dependent newbie"  :razz: )


Overall, my impression of Ubuntu is that its almost as newbie friendly as Mandrake but a lot leaner.

---

### Post by im_ka on 2004-11-06
[QUOTE=Zundfolge]Nothing but problems ... Grub just refuses to work ... Finally got LILO to install, but it doesn't give me a menu, just boots Ubuntu (with an "error 0x40", so I think it might be a bios problem). I have Mandrake on my second drive, but will need to put WinXP back on the second drive.


DNS is a pain on every Linux machine I've ever set up ... Windows, Mac OS (9 and X) both seem to be able to autoconfigure, but for some reason I have to screw with the settings six ways from Sunday to get it to work on Linux (although I've gotten much better at that part so it doesn't bother me as much)


Other then this forum, I found that just dumping a question into Google would get me an answer 8 times out of 10


I actually prefer gaim to any other ICQ client I've used (well, Trillian is pretty nice) so I'm using it on my Windows machine at work.

I'm a Graphic Designer, so the one thing that has kept me from going 100% Linux is Adobe (although there was good news on /. about Adobe and Linux today [[click]](http://linux.slashdot.org/linux/04/11/03/159225.shtml?tid=152&tid=187&tid=185&tid=106) )My wife has a Mac, so I can live without Adobe on my Linux machines. I've never liked Gimp (sorry Gimp fans) but Photoshop runs fine under Wine. I'm hoping Wine sets up as easy under Ubuntu as it did under Mandrake.

There just is no substitue for InDesign or Illustrator (no, Scribe isn't even close ... maybe if I went back in time to 1992 with the newest version of Scribe, it might be a little more powerful then QuarkXpress).


On Windows and Mac OS I'm pretty much a serious "Power User" ... one of the biggest problems I have with Linux is that I can't "visualize" the file system ... a more detailed explanation of the file system would be nice (I'd like to know what goes where and why) Also I'd like to know if there is some way to invoke root in Nautilus (yes, I'm still a "GUI dependent newbie"  :razz: )


Overall, my impression of Ubuntu is that its almost as newbie friendly as Mandrake but a lot leaner.[/QUOTE]

great help :)

i'm gonna have to start soon, the shipit cd's shuold be here in a few weeks time

---

### Post by Artiom on 2004-11-06
> On Windows and Mac OS I'm pretty much a serious "Power User" ... one of the biggest problems I have with Linux is that I can't "visualize" the file system ... a more detailed explanation of the file system would be nice (I'd like to know what goes where and why) Also I'd like to know if there is some way to invoke root in Nautilus (yes, I'm still a "GUI dependent newbie"  ) 
same for me.

> 5. have you find the linux-equivalents for your "favourite" winblows apps? talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for? 
getright --> Gwget
bittorent --> Azureus
FTP client --> gFTP
eMule --> xMule
web development --> bluefish


>  3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult? 
Video problems (installing drivers)
Installing MPlayer - after I followed install from FAQ page it worked, but I think it should be available as .deb file or from apt-get. It will be much easier this way.

>  +1. any other suggestions what the "starter-documentation" should include? any areas you've had/are having difficulties?  
Where programs install their files?
How to create symbolic links? Where should I put them if I want to run program, by typing only the name of the program, and not the hole path to it?
Where I should install programs?(to what path?)

---

### Post by Tapeworm on 2004-11-06
[QUOTE=im_ka]1. have you had problems with setting up dualboot? if yes, what problems?[/QUOTE]

Haven't tried dualbooting yet.  Any pointers/HowTo's about configuing GRUB

[QUOTE=im_ka]
3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult?[/QUOTE]

Mounting my NTFS partions so they are available in Ubuntu. Souldn't there be a graphical tool for this type of thing? I used some postings in this forum to help me edit /etc/fstab

I am still trying to get my network card set up and once that is done I can start experimenting with Synaptic.


[QUOTE=im_ka]
5. have you find the linux-equivalents for your "favourite" winblows apps?  talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for?[/QUOTE]

Rythembox ix interesting but I am still looking for something similar to WinAmp

I was scatching my head about burning a CD-R until I figured out it is built into Gnome and all I had to do was put in a black and then drag the files to the CD-R wndow. 

Tapeworm

---

### Post by im_ka on 2004-11-06
[QUOTE=Tapeworm]
Rythembox ix interesting but I am still looking for something similar to WinAmp
[/QUOTE]
try xmms (it's in universe)

thanks for the contribution!

---

### Post by wallijonn on 2004-11-06
You could start a separate 'tips' section which can be easily accessed on line. It could be dynamically updated to reflect the newest package updates. For example you are using XFree86 now, but you may switch to XOrg. All the people who contribute HowTo: info could be distilled into an "essence" which can be downloaded through the HELP utility (just as you have crafted SPM). Ubuntu ought to take all the little tips and incorporate them into the HELP utility - batch file scripts which can be run from within the HELP utility to fix a 'problem'. Need MPlayer running? - hit this button, supply the password, try it now. Need to make a symbolic link? Where from? Where to? It should work like "shortcuts" work under MSWindows.

The greatest fear for newbies must be having to wade through MAN pages. Man pages are fine but tend to change somewhat with certain distros.  Anyone who can come up with a useable GIMP manual will do a great service to the community. 

I still have not figured a way to mount floppies. Why is that so hard when SUSE and Gentoo can automount? Even mounting Fedora like doesn't work. Why? 

Certain utilities can be grouped under gdesklets - like fdutils. You could have a blank dgesklet that when clicked will ask for what function you are interested in doing, like burning a CD or playing an .mp3.

The installer needs a little more work. A friend had to tell me that I could install as Reiser or XFS. 

I love SPM. But a "Security" field should be added under STATUS to immediately show what can be installed or upgraded. I love being able to mark 'something' for 'complete removal'. But SPM can be fluxed and can be as intimadating as searching for rogue files under MSWindows and manually deleteing the offending files to get SPM to once again work correctly. 

I love the ability to show hidden files (something which is lacking in certain other distros). 

The Ubuntu website should link to this forum; prominently.

---

### Post by Vlammend on 2004-11-07
My problems with Linux as a newbie (in general):
- Video drivers 
Unreal Tournament never runs out of the box, updating the drivers or installing drivers to play the game always completly destroys my Linux, this problem is still unsolved (Nvidia)

- installing a single debian package
I learned this now, but would be great to know for such a guide

- The filesystem
lots op maps and lots of files, but very unclear for me.

- Dual Booting
Want to keep windows for some games and wine will not work on my AMD64 install so I will still need XP :-( I am trying to figure this out now, first attempt failed.
edit: now working, things to include in the starter docs: 
correct or preffered partitions (sizes, locations, mountpoints)
the edit of menu.lst to include Windows in the grub list
the correct settings for the vfat drives to read and write to those drives.

- a special chapter about Wine will be a good idea

---

### Post by tekwerx on 2004-11-11
have you had problems with setting up dualboot? if yes, what problems?

Nope, no problems.  All I had to do (when I used Windows) was use Partition Magic to resize my partitions to free some space, then stick in the CD and let it automatically use the free space.  Easy.


2. any issues installing ubuntu?

Again, no, but if I didnt know about Partition Magic, there might have been when it was asking about partitions.  


3. what parts of setting-up-your-system (sound, video, desktop,...) did you find difficult?

The network.  Still working on that one...


4. where do you go on the internet if you need help/info (apart from this forum :))? what websites should i include in "link collection"

Google is your friend.  :)


5. have you find the linux-equivalents for your "favourite" winblows apps?  talking about ms office - openoffice, icq - gaim, winamp - xmms, etc... any app you still need a replacement for?

OpenOffice, gAIM, XMMS, FireFox...yep, got em all.  :)


6. do you still use winblows? if not, how long did it take for you to become "100% open source"?

No, I dont.  For years I have been messing with dual-booting, and finally, I just got tired of using windows for only playing games.  I got Cedega and solved that problem.  Windows is gone. 


+1. any other suggestions what the "starter-documentation" should include? any areas you've had/are having difficulties?

Networking.  Networking, networking, networking.  Networking.  Also, how to share files between your different OS partitions would be excellent.

---

