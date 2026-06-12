---
title: "A real command line ubuntu distro"
date: 2010-07-19
forum: General Help
---

### Post by linux18 on 2010-07-19
DOWNLOAD LINK BELOW!!
NOW AVAILABLE IN 32-BIT!

SUMMARY:
There were a few threads a while back asking for support in creating a command line ubuntu, however those threads died out pretty quickly. I intend to have a new version of my console-based distribution every week, uploaded to dropbox for all to download. My first versions will install the exact same system as the CLI-only install option in the alternate install CD's only with a smaller ISO and faster install. To avoid thread stagnation updates will be constant and edited into this post, but it is mainly up to you people reading this to determine whether or not this project will continue.

OBJECTIVES:
-All the features you want in a cli, out-of-the-box 
-A new version or program released every week

RELEASES  x86_64:
7/25/2010 - version 1.0 64-bit ( 467 MB, exact same install as the command line option on the alternate install CD )
8/03/2010 - version 1.1 64-bit ( 399 MB, exact same install as the command line option on the alternate install CD )
8/08/2010 - version 1.1 64-bit ( 355 MB  same as 8/03 except the iso is compressed, just a tiny fraction away from being half the size of a normal ubuntu iso) 

RELEASES x86:
8/10/2010 - version 0.9 32-bit ( 375 MB similar to 1.1_64-bit, it's the first 32 bit version of my OS still in beta phase )

UPDATES:
-version 1.1 is HERE!! download link below
-version 0.9 32-bit is here!! download link below

_________________________________________________________________________________________________________________________
SYSTEM REQUIREMENTS (x86_64):
-testing in virtualbox, I have found the minimum and recommended system requirements(version 1.1):

RAM: 
-absolute minimum amount of ram before kernel panic: 60MB   
-recommended absolute minumum: 96MB
-128MB of ram installs 25% faster than 96MB
-160MB of ram installs 20% faster than 128MB 
-196MB of ram installs 15% faster than 160MB (recommended ) 
-256Mb+ installs 5% faster than 196 

CPU:
-any 64-bit cpu

HARD DISK:
-600MB (no swap)
-1GB (recommended) 

SYSTEM REQUIREMENTS (x86):

RAM:                                                                                                                                    
-absolute minimum amount of ram before kernel panic: 40MB 
-recommended absolute minumum: 80MB
-128MB of ram installs 30% faster than 80MB
-160MB of ram installs 20% faster than 128MB
-196MB of ram installs 10% faster than 160MB (recommended )                                       
-256Mb+ installs 5% faster than  196MB

CPU:
                                          -133mhz 80486 or better  

                                                                  HARD DISK:
-600MB (no swap partition)
                                                                                     -1GB+ (recommended)
______________________________________________________________________________________________________________________________

PERFORMANCE:
-7% faster than the alternate CD when installing from a CD
-4% faster than the alternate CD when installing from a DVD
-3 more megabytes of free ram during installation

STATUS:
-working on some documentation
-working on version 1.2, which promises more improvements 

TODO:
-I need collaboration between anyone interested
-the final iso is still too big @ 399 MB and needs tweaking to reduce size
-still haven't added anything yet, just cut the iso size and made some scripts 

WHAT YOU CAN DO:
You don't need to be a computer expert to help the project, we still need testers, shell script writers, a name for the project, maybe people to bump the thread:), the list goes on and on. If you think something could be improved we would like to hear it! Lastly, we are NOT accepting monetary donations ( however time and code donations are welcome )

CURRENT VERSIONS: 1.1 compressed 64-bit, 0.9 compressed 32-bit 

DOWNLOAD shell script (VERSION 1.1 COMPRESSED 64-bit):
```

#!/bin/bash
wget --progress=dot http://download676.mediafire.com/kdwxwogd24yg/i02e6kc7g6gt8n9/cli-1.1.7z.001
wget --progress=dot http://download935.mediafire.com/s4rfzrie36bg/9753lpskndjmnfc/cli-1.1.7z.002
wget --progress=dot http://download216.mediafire.com/c5bj3h5h12tg/mxg2l6w3t6rit5t/cli-1.1.7z.003
wget --progress=dot http://download708.mediafire.com/hhh73uat99qg/ovecrc11u3740ev/cli-1.1.7z.004
wget --progress=dot http://205.196.122.8/n82w07tk1kyg/1nzqtw8peaqoery/cli-1.1.7z.005
wget --progress=dot http://download346.mediafire.com/gj4ccb40xfxg/ca82g6l7pl2s5ee/cli-1.1.7z.006
wget --progress=dot http://download90.mediafire.com/0y4t4w0b5zig/ton8ame025wcykr/cli-1.1.7z.007
wget --progress=dot http://download735.mediafire.com/uxpf161kd1eg/3gcf89ec769784e/cli-1.1.7z.008
echo "done, just decompress the first archive and it will turn into an iso"



```DOWNLOAD shell script (VERSION 0.9 COMPRESSED 32-bit):
```
 
#!/bin/bash
wget --progress=dot http://download10.mediafire.com/92gf3fbjm0tg/mvtco68k3j27ezc/cli_32-0.9.7z.001
wget --progress=dot http://download622.mediafire.com/4i7c7z4rqnmg/yxhsnmv5wlqzdmf/cli_32-0.9.7z.002
wget --progress=dot http://download721.mediafire.com/ifbkxjhmd5zg/e49ntwfqlyjy50t/cli_32-0.9.7z.003
wget --progress=dot http://download932.mediafire.com/82aaxa7igbug/yn33sanjbj0s5xj/cli_32-0.9.7z.004
wget --progress=dot http://download467.mediafire.com/u78bijdsc9qg/3mr7az23vvg5bqc/cli_32-0.9.7z.005
wget --progress=dot http://download38.mediafire.com/mkkjo3xfchwg/o9utcp6aj9j8hx7/cli_32-0.9.7z.006
wget --progress=dot http://download1022.mediafire.com/7e2kvw5poang/bh123f5to3b1m3n/cli_32-0.9.7z.007
wget --progress=dot http://download147.mediafire.com/hc343c4y7jvg/i1g53z30o2q660x/cli_32-0.9.7z.008
echo "done, just decompress the first archive and it will turn into an iso"

 
 
```DOWNLOAD OLD VERSION HERE (64-bit):
[http://dl.dropbox.com/u/9144169/cli-1.0__00](http://dl.dropbox.com/u/9144169/cli-1.0__00)  part 1 [250MB]
[http://dl.dropbox.com/u/9144169/cli-1.0__01](http://dl.dropbox.com/u/9144169/cli-1.0__01)  part 2 [197MB]

BUILD (old version only):
to turn the files into an ISO, cd to the dir and " cat cli-1.* > cli-1.1.iso "

---

### Post by cariboo on 2010-07-19
Why not use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"). just type cli at the boot prompt.

---

### Post by WorMzy on 2010-07-19
[http://www.ubuntu.com/server]("http://www.ubuntu.com/server")

?

---

### Post by linux18 on 2010-07-19
[@WorMzy ]("http://ubuntuforums.org/member.php?u=1062896")The server version is a little too bloated for easy downloading and that bloat slows down cd-based installation because the cd has to skip over all the packages that won't be installed.

@[[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") The mini-iso is a full day's work of downloading and installing packages, when I was doing my fluxbox + minimal install it took over six hours, its better if you can have the same result but with a faster install.

In either case, your only left with a basic command line that still needs a lot of packages to get it just right and a little polish to the UI wouldn't hurt ( just because it's a command line doesn't mean it can't have a spiffy UI )

I can already tell this is going to be an uphill battle.

---

### Post by tgm4883 on 2010-07-19
> **linux18 said:**
> [@WorMzy ]("http://ubuntuforums.org/member.php?u=1062896")The server version is a little too bloated for easy downloading and that bloat slows down cd-based installation because the cd has to skip over all the packages that won't be installed.

@[[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") The mini-iso is a full day's work of downloading and installing packages, when I was doing my fluxbox + minimal install it took over six hours, its better if you can have the same result but with a faster install.

In either case, your only left with a basic command line that still needs a lot of packages to get it just right and a little polish to the UI wouldn't hurt ( just because it's a command line doesn't mean it can't have a spiffy UI )

I can already tell this is going to be an uphill battle.

So... you want a complete ubuntu install with all the packages such as open office, firefox, etc, but in a command line version?

---

### Post by WorMzy on 2010-07-19
I just don't see a market for it. If you want a barebones CLI setup, install Arch by netinstall. Minimal download, minimal system, and CLI right out of the box.

---

### Post by Simian Man on 2010-07-19
> **WorMzy said:**
> I just don't see a market for it. If you want a barebones CLI setup, install Arch by netinstall. Minimal download, minimal system, and CLI right out of the box.

I agree.  The subset of people who like Ubuntu, don't want a user interface and don't want to install and tweak things themselves has got to be incredibly small.

---

### Post by linux18 on 2010-07-19
Ok, defining a "real" cli ubuntu:

all of the command line packages you normally use already installed ( cli -only, mini.iso, netinstall, etc. omit many packages you normally use in the command line, gnucoreutils for example)


I'm not looking for a market, but lots of users enjoy using only the command line for as long as possible. If certain parts of the setup ( wifi ) were easier then it could make a huge difference to the appeal of the command line.

---

### Post by tgm4883 on 2010-07-19
> **linux18 said:**
> Ok, defining a "real" cli ubuntu:

all of the command line packages you normally use already installed ( cli -only, mini.iso, netinstall, etc. omit many packages you normally use in the command line, gnucoreutils for example)


I'm not looking for a market, but lots of users enjoy using only the command line for as long as possible. If certain parts of the setup ( wifi ) were easier then it could make a huge difference to the appeal of the command line.

Ah, you are looking for this then [https://build.reconstructor.org/](https://build.reconstructor.org/)

---

### Post by AlanR8 on 2010-07-19
I really DON'T understand the concept!

Users want and need a GUI. End of.

Geeks like to play with the OS. There's room for both in the wonderful world of Linux!

Enjoy your creation.

---

### Post by MattBD on 2010-07-19
I think someone beat you to it with INX:
[http://inx.maincontent.net/](http://inx.maincontent.net/)
It's well worth getting a copy of INX and having a play with it though - it taught me a lot about how to use the command line.

---

### Post by marshag63 on 2010-07-19
+++++1 for INX!  A totally awesome CLI live CD, which can be installed with persistence to a USB flash drive.  Its definitely teaching me a lot with tutorials of the basic of linux.  It has a wifi manager (ceni) which works great with my rt73 adapter, lots of options for playing music and ripping CDs, text browser, IRC chatting, email, viewing pictures, using screen, package management, even a game or two.

MarshaG.

---

### Post by linux18 on 2010-07-20
well what I was trying to do was make an inx clone that is fully binary compatible with ubuntu and uses the same repositories. I guess the world isn't ready yet.

---

### Post by MattBD on 2010-07-20
> **linux18 said:**
> well what I was trying to do was make an inx clone that is fully binary compatible with ubuntu and uses the same repositories. I guess the world isn't ready yet.

INX is based on Ubuntu (albeit Hardy Heron) as far as I recall and I'm pretty sure it uses the Ubuntu repositories.

---

### Post by sisco311 on 2010-07-20
> **linux18 said:**
> well what I was trying to do was make an inx clone that is fully binary compatible with ubuntu and uses the same repositories. I guess the world isn't ready yet.

I like the idea. What applications do you plan to include?

---

### Post by MattBD on 2010-07-20
> **linux18 said:**
> well what I was trying to do was make an inx clone that is fully binary compatible with ubuntu and uses the same repositories. I guess the world isn't ready yet.

If you want to do that, I suggest you check out [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) - it looks complicated but it really isn't that hard. I've built a few custom Ubuntu respins myself, based on Ubuntu Mini Remix - one I fondly recall was a somewhat tongue-in-cheek attempt to create a distro that looked as "hackerish" as possible. It's a very interesting way to learn more about Linux.

---

### Post by borth92 on 2010-07-20
the  GUI is like the #1 thing worked on by most, if not all but a few, users. The speed decrease is not that bad to have a good GUI like gnome...

---

### Post by linux18 on 2010-07-20
> **sisco311 said:**
> I like the idea. What applications do you plan to include?
Finally someone who likes the idea! 
First, I want to optimize the server or alternate install ISO to create a lightweight base.
Once that's working and stable, I will include some popular command line packages ( cvlc, links2, etc )
Then try to work on a similar interface to INX, and work on some scripts ( wifi ) for easy setup

---

### Post by MattBD on 2010-07-20
> **linux18 said:**
> Finally someone who likes the idea! 
First, I want to optimize the server or alternate install ISO to create a lightweight base.
Once that's working and stable, I will include some popular command line packages ( cvlc, links2, etc )
Then try to work on a similar interface to INX, and work on some scripts ( wifi ) for easy setup

For wifi, I believe the excellent Wicd wifi manager has a curses-based version you could use. Not sure if it's in the Ubuntu repositories - it may be in Launchpad though. I can also recommend mutt or pine for email, irssi for IRC, and finch for IM.

I'd love to know how you get on with this.

---

### Post by limestone on 2010-07-20
Just download the alternate cd and in the cd boot screen press f4 and shoes command-line install, this will install only ubuntu core (command-line)

---

### Post by jmsgz on 2010-07-20
for my money i would install
 either 
  1. ubuntu stripped down server with alternate install then build from     there or
  2. download and play with opendbsd which has great security and minimal initial install.

jmsgz

---

### Post by Mortesins93 on 2010-07-20
I agree with AlanR8, i don't see the point

---

### Post by andrew.46 on 2010-07-24
Hi Matt,

> **MattBD said:**
> For wifi, I believe the excellent Wicd wifi manager has a curses-based version you could use.

Indeed it does, although at least the appearance could do with some polish :).

Andrew

---

### Post by v1ad on 2010-07-24
> **wormzy said:**
> [http://www.ubuntu.com/server]("http://www.ubuntu.com/server")

?

+1

also inx is a little overdone (imo)

if you are working on 1 i would recommend that you install pianobar into it.

---

### Post by linux18 on 2010-07-25
bump

just updated the page, the iso can be in your hard drive tommorrow.
needs to be lightened before anything is added

---

### Post by linux18 on 2010-07-26
IT'S here! the first version is here.
it's a little underwhelming right now, but it works great in virtualbox.

---

### Post by limestone on 2010-07-26
Why don't just download Ubuntu alternate cd and chose the command-line install... That will install only a command-line ubuntu with no extra applications.

---

### Post by sisco311 on 2010-07-26
> **pont.andersson said:**
> Why don't just download Ubuntu alternate cd and chose the command-line install... That will install only a command-line ubuntu **with no extra applications**.

I guess, you answered your own question.

---

### Post by Calash on 2010-07-26
> **pont.andersson said:**
> Why don't just download Ubuntu alternate cd and chose the command-line install... That will install only a command-line ubuntu with no extra applications.

I believe the point is not to find the easiest solution to the issue but to create something new that is not out there and in the process for the OP to learn more about the operating system and give back to the community.

---

### Post by linux18 on 2010-07-26
> **Calash said:**
> I believe the point is not to find the easiest solution to the issue but to create something new that is not out there and in the process for the OP to learn more about the operating system and give back to the community.
exactly, plus I want to do a little better than the bare-bones cli of the alternate install. if you want you can test it out in virtualbox and report bugs and stuff, I'm working on the first patch and documentation, due out by the end of next week

---

### Post by linux18 on 2010-08-02
bump

uploading version 1.1, which promises further speed improvements and a smaller ISO size

---

### Post by MCVenom on 2010-08-07
Love the idea! (Honestly, I don't see why people seem so discouraging here.) :D

Don't know why this is in General Help though.

---

### Post by deserthowler on 2010-08-07
Why not Debian with netinstall?  NetBSD?  OpenBSD?  FreeBSD?  Add emacs.  I'm not trying to discourage, just understand.

Earl

---

### Post by linux18 on 2010-08-07
> **deserthowler said:**
> Why not Debian with netinstall?  NetBSD?  OpenBSD?  FreeBSD?  Add emacs.  I'm not trying to discourage, just understand.

Earl
there's not much to understand - a ubuntu based distro based on the command line that has a smaller iso size and easy configuration scripts. I bet if I made a 32-bit version everyone would be praising it.

---

### Post by linux18 on 2010-08-08
32-bit Bump!
by popular demand, I'm uploading the 32-bit version now. enjoy!

---

### Post by corrytonapple on 2010-08-08
I think he understands their are other cli out their. I support your idea in 64-bit. Do you have plans on having a disk utility app?

---

### Post by linux18 on 2010-08-09
Ok, the 32-bit version is ready for download, I think some documentation and scripts will be the main focus of the next release.

---

### Post by corrytonapple on 2010-08-09
Still trying to get some media. Will check prices.............

---

### Post by Zanthir on 2010-10-04
> **tgm4883 said:**
> Ah, you are looking for this then [https://build.reconstructor.org/](https://build.reconstructor.org/)
 
Um, that didn't work, but [http://build.reconstructor.org](http://build.reconstructor.org) seemed ok.

---

### Post by Lt.Leo on 2010-10-04
There is really not much need for this in my eyes. Though it would be nice, you can just go to Accessories > Terminal > Full-screen and you will have what you want. I could see why some people would enjoy CLI only though.

---

### Post by KdotJ on 2010-10-04
> **WorMzy said:**
> I just don't see a market for it. If you want a barebones CLI setup, install Arch by netinstall. Minimal download, minimal system, and CLI right out of the box.

This. 
However I don't see why people insist on making so many "minimal CLI" versions of ubuntu where there is one readily available

---

### Post by corrytonapple on 2010-10-04
> **KdotJ said:**
> This. 
However I don't see why people insist on making so many "minimal CLI" versions of ubuntu where there is one readily available
Is it as advanced as this one (Our CLI Ubuntu) is going to be? A text web browser, something like Open Office, and other apps like it? If there is, then I agree with you. But, there is always room for improvement.:)

---

### Post by ToFue on 2010-10-05
I really don't see why this isn't a good idea: yes you can install a cli-only install, but where's functionality? and yes you can do a stock server install with a Lot of bloat compared to what's actually used..

Sure there's other projects that have a similar aim, but do those projects actually install from Ubuntu repos and have niether too much or too little in extra function? It appears that the OP is trying to make a Goldie Locks cli that offers solid, not-quite-basic, Ubuntu-based features.. I would even enjoy if it could do an install from source compiling like gentoo or lfs, but whatever, that's me. I like text too, not just representational pictures and patterns of colour. Maybe I just like things that Do what i tell it to do, no matter its presentation.

As far as comments that every user needs a gui- I find that to be misleading. Not everyone opts for gui's, which is why cli installs exist in the first place - even if it Is just for nastalgia. (that or graphics can't render on a system for whatever reason)

I like the idea that testing is done for low mem deployments, which has potential for mobile devices and such- I would sure like it if I had full gnu/linux support on my evo, for instance.. 

And there is the learning experience as a whole- each new perspective has its place, and i like new perspectives. Sure it's easier to pick something that's been done, but that leads to 'path of least resistance' stagnation. The community would have yet another resourse for whatever purpose.  

It makes me want to rant when people try to (purposefully or otherwise) stifle the efforts of others instead of enabling them. The whole point of free software is to allow for this sort of adventuring. Why negate that?

If you don't see the point in exloration, then stay indoors with the world you already know.

.. just my two cents ..

---

### Post by egalot on 2010-10-19
I executed the script with the wget statements and all I got was an currupt archive around 800K in size. I am interested in an installer that only has the libraries required for a CLI install. I am working on a custimized installer using preseeding and isolinux.cfg. It is currently working well out of the Alternate CD, however I am interested in reducing the ISO size as much as possible. I tried the mini.iso but after several hours of trying for some reason it does aknowledge the preseed file, it just ignores it.

If you could post another link to download this CLI only iso I would greatly appreciate it.

---

### Post by J05HYYY on 2010-10-29
What is needed is a cli version of Ubuntu which doesn't use the internet to download lots of stuff and has an ISO which doesn't contain all the GUI programs which come on all of the current Ubuntu cds.

That would be something worth making. Is this what your attempting to do?

[[IMG]http://brainstorm.ubuntu.com/idea/26306/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/26306/)

---

### Post by munkeh on 2010-11-05
Hi, Thanks Linux18 for your endeavour. I'm new to Cli -only. I have just gotten your 32-bit version which I am looking forward to having a exploratory go of. I am sure though if I cannot get it to work it shall be my lack of computerness that will be at fault.  Thanks again.

---

