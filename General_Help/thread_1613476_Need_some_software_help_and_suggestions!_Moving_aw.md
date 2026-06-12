---
title: "Need some software help and suggestions! Moving away from Windows."
date: 2010-11-04
forum: General Help
---

### Post by ivarn on 2010-11-04
Ok so I use these programs in Windows that I can't find any linux alternatives for.
So here's my list of programs I use in windows, and what I need is linux alternatives to these programs. And yes, they must have the same functionality, options and stuff.

Jesc Animation Pro 3 (live gif and avi animation)
Macromedia Flash 8 or Sothink SWF Quicker (flash programming / designing)
Sothink SWF Decompiler (extract swf files to images and sound files etc.)
Sling Player (Streaming tv from my slingbox tuner)
UltraIso (make fake cd rom drivers for iso files)
Url Snooper (Snif all http/rtsp/mms/ftp links) (the firefox add ons can't sniff from flash players or encrypted links).
Windows Media Recorder 11 (automatically capture streaming media and record them)
Acoustica Audio Converter Pro (rip cds and convert between formats like mp3, flac, ogg, wma and wav)
MP3 DJ Pro (live mixing mp3s with tempo and pitch (bpm) controlls and turntable)

Programs and functions I can live without:
adobe audition 4 (audio editing) (audacity is too basic)
DVDVideosoft (Mini programs to download and convert from youtube video to audio)
I could also use a DVD/BluRay creator that will let me create the menus and such.

If I can do all these things in linux with either scripts or apps, I can finally get rid of windows for good.
I guess the reason why I can't find programs to do these things is because the software center / synaptic only gives you the free applications.
But no, money is not a problem as long as I can do these things in linux. then I can get rid of windows and it's waste of space.

And thank you so much in advance for and to take your time helping me with this. It really means a lot!

---

### Post by hlalm on 2010-11-04
One option is to use wine

I picked two of the programs on your list and they look like they would work fine

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9786](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9786) Flash
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11311](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11311) UltraISO

You can try to find the others here [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

---

### Post by ivarn on 2010-11-04
Thanks but I want it to be fully stable.
UltraIso won't recognize the cd rom driver in ubuntu.
Obviously because the location isn't the same from windows.
Flash and dreamweaver are both ok in wine, but since I need these programs to do a fully stable job with both audio and video coding, I can't use Wine for obvious reasons.
Wine is a great alternative when it comes to games and less important things.
Also, I am a bit against Wine since it helps on slowing down linux programming and developing since people rely on wine every time they can't find the software or game in linux format.

---

### Post by Mark Phelps on 2010-11-04
> **ivarn said:**
> ... And yes, they must have the same functionality, options and stuff.

Such restrictions will pretty much rule out EVERY Linux alternative -- except in the few rare cases that some intentionally set about to "clone" a Windows app -- and that is generally what is NOT done.

Rather than use doing your homework, why don't you go to the link below and check out the apps yourself -- since only you know what you really want from each one:

[http://www.linuxalt.com/]("http://www.linuxalt.com/")

---

### Post by ivarn on 2010-11-05
Thanks. I didn't literally mean same options and functionality. As long as I can do the same stuff with them I am happy.
Ok so I found a couple of the software I needed on that link you gave me (thanx alot btw).
But I still need a few programs, so I'll give you a list over the programs I couldn't find an alternative for. OH and I know the list was very uncomplete cuz I know a few software I didn't see there.

Jesc Animation Pro 3 (live gif and avi animation)
Macromedia Flash 8 or Sothink SWF Quicker (flash programming / designing)
Sothink SWF Decompiler (extract swf files to images and sound files etc.)
Sling Player (Streaming tv from my slingbox tuner)
UltraIso (make fake cd rom drivers for iso files)
Url Snooper (Snif all http/rtsp/mms/ftp links) (the firefox add ons can't sniff from flash players or encrypted links).
Windows Media Recorder 11 (automatically capture streaming media and record them)

Too bad that list didn't explain what the programs are about.
Are there more websites like that around, but with a more detailed list, or a list over all available (or almost ever) software for linux and with a short description about the program?

---

### Post by Verbeck on 2010-11-05
> **ivarn said:**
> 
UltraIso (make fake cd rom drivers for iso files)

you can use brasero to create an iso images and then use the archive mounter that comes by default to mount the iso (right click>open with>archive mounter)

or run in terminal :
```

sudo mkdir /media/iso
sudo mount -t iso9660 /link/to/iso/ubuntu.iso /media/iso -o loop

```

---

### Post by ivarn on 2010-11-05
> **Verbeck said:**
> you can use brasero to create an iso images and then use the archive mounter that comes by default to mount the iso (right click>open with>archive mounter)

or run in terminal :
```

sudo mkdir /media/iso
sudo mount -t iso9660 /link/to/iso/ubuntu.iso /media/iso -o loop

```
Thanks but I know how to make an iso image but that's not what I use it for.
As I said, I use it as to run a fake cd rom driver.
There are other programs like that, such as ALcohol 192½

---

### Post by oldos2er on 2010-11-05
> **ivarn said:**
> Windows Media Recorder 11 (automatically capture streaming media and record them)


Vlc can do this, and probably mplayer can too.

---

### Post by nothingtoprove on 2010-11-05
*Acoustica Audio Converter Pro (rip cds and convert between formats like mp3, flac, ogg, wma and wav)*

I've been using dBpoweramp via Wine for a couple of years now with no probs. I'm guessing it does the same as Acoustica.

---

### Post by ivarn on 2010-11-05
> **oldos2er said:**
> Vlc can do this, and probably mplayer can too.
Really? wow thanks a lot :)

> **nothingtoprove said:**
> *Acoustica Audio Converter Pro (rip cds and convert between formats like mp3, flac, ogg, wma and wav)*

I've been using dBpoweramp via Wine for a couple of years now with no probs. I'm guessing it does the same as Acoustica.

I'll check it out. Thank you so much :) But as I said, I don't like Wine and I wanna keep my linux as clean as possible.

BTW, Scratch the iso app. I found GMountISO. Works like a charm.

---

### Post by frank cox on 2010-11-05
The animation tools in the Power Point like Presentations in  Softmaker Office for Linux  are very good and the whole Office suite is superior to Microsoft Office. It is super fast and for 70.00 you get 3 licenses!

Here are some links that might help, I am confident there are tools in Linux to replace all of your MS apps but there are so many it takes time to find them. I suggest typing in the type of software + Linux + forum and see if you can find a Linux community that is into what you are.

[http://www.softmaker.com/english/ofl_en.htm](http://www.softmaker.com/english/ofl_en.htm)

[www.**linux](www.**linux)**questions.org/**linux**/.../**LINUX**_**ALTERNATIVES**_HOWTO

[http://www.linuxalt.com/](http://www.linuxalt.com/)

[www.**linux](www.**linux)**.ie/newusers/**alternatives**.php

**alternative**to.net/ 

laptoplogic.com/.../top-50-**linux**-**alternatives**-to-popular-apps

**linux**appfinder.com/[B]alternatives

[/B]lxer.com/module/newswire/view/131294/index.html
jjmacey.net/blog/?p=179

[www.overclock.net/](www.overclock.net/)**linux**.../527756-**linux**-**alternatives**-common-windows-programs.html
 
[www.makeuseof.com/.../](www.makeuseof.com/.../)**linux**appfinder-**linux**-**alternative**-to-windows/ 

ldn.**linux**foundation.org/.../**linux**-**alternatives**-windows-sbs-part-two

---

### Post by Verbeck on 2010-11-06
> **ivarn said:**
> Thanks but I know how to make an iso image but that's not what I use it for.
As I said, I use it as to run a fake cd rom driver.
There are other programs like that, such as ALcohol 192½

thats what i just said :| you dont need a separate program to mount iso's . ubuntu comes in default with "archive mounter" which creates a *fake cd rom*. the terminal command does the same. see thee attachment

EDIT : nvm that, glad you found an alternative :D

---

### Post by arnavk007 on 2010-11-06
verbeck is right
if you dont have any blank cd in your cd drive just click on the iso and ubuntu will mount it

---

### Post by Verbeck on 2010-11-06
> **arnavk007 said:**
> 
if you dont have any blank cd in your cd drive just click on the iso and ubuntu will mount it
AFAIK, having a blank cd does not have anything to do with mounting an iso. the mount points will be different

---

### Post by I'mGeorge on 2010-11-06
> **ivarn said:**
> 
BTW, Scratch the iso app. I found GMountISO. Works like a charm.

In Linux you don't really need a special software to mount .iso images. Iso images can be easily made in most CD burning software, for mounting them just open your terminal and do "sudo mount -o loop /path_to your_iso_image /media/cdrom" and that's about it. If you have .nrg or .bin CD images, you need convertors that would transform those images in iso files,through simple commands like "nrg2iso name_of_ISO",  which can be found and installed with synaptic.

---

### Post by frank cox on 2010-11-06
While it is true that you can do all this easily from the command line I found a little gui I really like .

It sounds a lot like the one mentioned here already but it is called  gIsoMount instead of   GMountISO .

I was trying to do a md5checksum in xUbuntu 10.10 for the first time ans the command line method I have been using in Ubuntu 9.04 did not work - cd  /whereever/the/fileis then md5sum filename.iso.

I assumed the checker was not installed by default being that  xUbuntu is a leaner distro so I  went to synaptic to get it and this came up first  and since this one was so small I went ahead and installed it to try it out. It made it a lot quicker to run the md5sum and has a setting for mounting iso's , cd's and to browse them and edit them if they are setup to do so and calls up Gnomes burnuing wizard as well . It is a cook kittle program, as was said there is another way but I hate to type. Usually the CL is much faster but not in this case. Md5sum took 3 seconds,

Of course it is Applications-Systems-Stnaptic and then just type gisoMount in the search and install it.
It is only about 300 k's.

I think you'll like it!

---

### Post by ivarn on 2010-11-11
Thanks guys. And thank you [frank cox]("http://ubuntuforums.org/member.php?u=934524"), I'll check out the links you gave me. Too bad some of those links are messed up thanks to /../ but I'll see if google will help me there.
I am sure that there are linux alternatives for everything I can do in windows but I just need to find all the correct programs to be sure.
I mean, after I have deleted windows there is no turning back.
So that's why I simply MUST find perfect linux alternatives.
And again, thank you so much. 
I wish more people could make websites like linuxalt, since that's really what us "Windows" people need.

---

### Post by Verbeck on 2010-11-12
> **ivarn said:**
> 
I wish more people could make websites like linuxalt, since that's really what us "Windows" people need.

[http://www.osalt.com/](http://www.osalt.com/)

might be of some help ;)

---

### Post by ivarn on 2010-11-13
Thanks a lot :)
My list gets shorter and shorter now.

Here's the only apps I need alternatives for now.

Jesc Animation Pro 3 (live gif and avi frame by frame animation)
Sothink SWF Decompiler (extract swf files to images and sound files etc.)

**Not that important**
Sling Player (Streaming tv from my slingbox tuner)

---

