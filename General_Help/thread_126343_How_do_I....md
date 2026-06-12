---
title: "How do I..."
date: 2006-02-06
forum: General Help
---

### Post by chopsbuntu on 2006-02-06
Hello everyone! Yes, I'm new here and I am fairly new to Linux as well.

Just a little about me...

I have been into computers for about 20 years now, have been building them for myself, family, friends, and even for work for about 10 of those years. However I have only ever used Microsoft. <--- I know, YUCK! LOL 

I have tried various versions of Linux over the past 4-5 years, including Red Hat, Suse, KDE, Mandrake, etc, etc, and now Ubuntu. But I never kept with them because of the difficult task of installing software, drivers, whatever. So with that, I have always reverted back to Windows.

So my question is, since I do not have a clue... How in the world do you install software and drivers and anything else on this OS?

I have looked and looked through the Synaptic Manager, but I don't know what I'm looking at. I don't know what "repositories" are, or what multiverse and universe repositories are. 

If possible, I would really like to download and install the mobo drivers, video drivers, Opera web browser, some kind of virus software, and possibly some spy/add removal software.

I would eventually like to be able to install/uninstall anything. I'm assuming that all software installs pretty much the same way? Once I get over this hurdle, I think I'll really be enjoying Linux much more. 

So with that, do you think I have any hope at learning how to do any of this? Also, is Kubuntu an upgrade? And if so, is it easy enough to upgrade to, or do you need to do a totally new install?

Any help will be greatly appreciated! Trust me. ;)

---

### Post by carlosqueso on 2006-02-06
Software installation is very different on Linux, and actually varies a bit from disto to distro.  That's the bad news.  The good news, is that for most software, it's really easy.  
A repository is a collection of software put out by your distribution that is easy to install and to get security updates for.   The Universe and Multiverse repositories are software that's disabled by default because the ubuntu developers do not directly support them (although if you have problems with them, ask here because us forum folks aren't picky).  You can enable them by typing ```
sudo gedit /etc/apt/sources.list
``` in a terminal to edit your sources list and making yours look like mine: ```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

Once that's good to go, make sure you're connected to the internet, fire up synaptic, and you can search for, and pick out what programs you want.  just click the checkbox and choose "Mark for Installation".  Then click "Apply".  If you want even easier installation and you know the name of the package (program), just type ```
sudo apt-get install <package name>
```.  If you're having any problems, or need help with a specific program, post back and we'll be happy to help.

---

### Post by tntc1978 on 2006-02-06
> How in the world do you install software and drivers and anything else on this OS?

If you find something you want to install in synaptics, just right-click and press install. Then finish of by applying the changes. It is so easy and convenient. :-D 

> is Kubuntu an upgrade?

No Kubuntu is just using the KDE interface instead of the Gnome. See more if you search the forums. Found this:
[http://www.ubuntuforums.org/showthread.php?t=125976&highlight=kde+gnome](http://www.ubuntuforums.org/showthread.php?t=125976&highlight=kde+gnome)
[http://www.ubuntuforums.org/showthread.php?t=125831&highlight=kde+gnome](http://www.ubuntuforums.org/showthread.php?t=125831&highlight=kde+gnome)

And many more...

Find more information on multiverse, universe etc. here:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by chopsbuntu on 2006-02-06
[QUOTE=carlosqueso]Software installation is very different on Linux, and actually varies a bit from disto to distro.  That's the bad news.  The good news, is that for most software, it's really easy.  
A repository is a collection of software put out by your distribution that is easy to install and to get security updates for.   The Universe and Multiverse repositories are software that's disabled by default because the ubuntu developers do not directly support them (although if you have problems with them, ask here because us forum folks aren't picky).  You can enable them by typing ```
sudo gedit /etc/apt/sources.list
``` in a terminal to edit your sources list and making yours look like mine: ```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

Once that's good to go, make sure you're connected to the internet, fire up synaptic, and you can search for, and pick out what programs you want.  just click the checkbox and choose "Mark for Installation".  Then click "Apply".  If you want even easier installation and you know the name of the package (program), just type ```
sudo apt-get install <package name>
```.  If you're having any problems, or need help with a specific program, post back and we'll be happy to help.[/QUOTE]


Well I tried what you posted here. After I copied and pasted the text in that window, I got this when I opened Synaptic... And no, I forgot to make a backup of the original stuff that was in there. Did I just screw up my computer? :cry:

---

### Post by kaamos on 2006-02-06
Try hitting reload in synaptic.

---

### Post by beerorkid on 2006-02-06
[QUOTE=chopsbuntu]

If possible, I would really like to download and install the mobo drivers, video drivers, Opera web browser, some kind of virus software, and possibly some spy/add removal software.

[/QUOTE]

as for opera and video drivers, as well as many other things I would recomend automatix:
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)

the video drivers would depend on what kind of video card you have.  Nvidia is a little easier (especially with automatix) than ATI, ut both are doable.  There are howto's for both if you look around.

I am no expert, and think a few might disagree, but you do not need AV or spy/adware protection.  Linux and apple make up such a small percentage of computers in use that evel peeps do not see it as worth their time.  Also with the different distro's different ways of doing things it would be really hard to mess with a linux box that way.

I did see that AVG is offering a free version of its AV for linux.  As of right now it is only for a few distro's and not ubuntu yet.  I guess AV would be handy on a linux box if you were using a P2P software and wanted to make sure the files were clean before you transfered them to a winders box.

Edit:  automatix now includes ATI drivers

---

### Post by DiscoKiller on 2006-02-06
[QUOTE=chopsbuntu] I have only ever used Microsoft. <--- I know, YUCK! LOL 

[/QUOTE]

heh, you`ll find that a lot of the people on these forums are dual booting!! XP is popular for some reason...dont get it myself...that start button is enough for me (EEEW!!)

---

### Post by tntc1978 on 2006-02-06
I use these repositories: [http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672) They're all fine :-) just in case the refreshing doesn't work.

---

### Post by chopsbuntu on 2006-02-06
> kaamos -	Try hitting reload in synaptic.

Thanks! That did it. It also DL'ed some updates as well. \\:D/ 

> beerorkid - as for opera and video drivers, as well as many other things I would recomend automatix:
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)

the video drivers would depend on what kind of video card you have. Nvidia is a little easier (especially with automatix) than ATI, ut both are doable. There are howto's for both if you look around.

I am no expert, and think a few might disagree, but you do not need AV or spy/adware protection. Linux and apple make up such a small percentage of computers in use that evel peeps do not see it as worth their time. Also with the different distro's different ways of doing things it would be really hard to mess with a linux box that way.

Thanks. I'll go check out that link ASAP.

And I guess you're right about the AV software with Linux and Mac. I have heard the same thing from several Mac users as well.

> DiscoKiller - heh, you`ll find that a lot of the people on these forums are dual booting!! XP is popular for some reason...dont get it myself...that start button is enough for me (EEEW!!)

LOL. I don't have to worry about dual booting. This PC is only for Linux. My XP machine is for server duty; web/file/music server to be exact.

My Linux box is just for learning and hopefully for fun! :mrgreen: 

-------------------------
For everyone... How do I know what to install? The stuff listed in Synaptic isn't very descriptive as to what it is or what it's for.

Like I said before, my main thing is getting the mobo drivers installed and getting Opera up and running. The video driver isn't as important at the moment.

---

### Post by Razorback on 2006-02-06
Here is a posting of windows to linux program equivalents:

[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

---

### Post by chopsbuntu on 2006-02-07
Just so you know, I still have not been able to install anything, even Opera, which BTW is NOT in the Synaptic Package Manager anywhere. ](*,)

---

### Post by kaamos on 2006-02-07
Opera is under such a license that it is not legal to add it to the ubuntu repositories (that synaptic uses by default).

For opera, look here -> [http://ubuntuforums.org/showthread.php?t=78468](http://ubuntuforums.org/showthread.php?t=78468)
Spyware: does not exist.
Virus scanner (many people find this unnecessary): [https://wiki.ubuntu.com/ClamAV](https://wiki.ubuntu.com/ClamAV)

---

### Post by beerorkid on 2006-02-07
as far as help on installing different packages that not be "free"  It requires a little searching.  Most if not all major programs have howtos or wiki's.  A search can do wonders.

Also remember that this is one very heavily populated board.  You might have to go a few pages deep to figure out the answer.

There are things like automatix [http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix) that can install a bunch of things for you.  Some argue that it is better for users to find the answers and do the dirty work to get every thing going.  

I must admidt that I learn every day.  I am intrigued by linux every day.  With windows I was bored.

---

### Post by chopsbuntu on 2006-02-07
This is getting pretty freaking ridiculous.

I try doing what **kaamos** linked me to, and it keeps coming up saying that it can only be done by a "superuser", whatever the heck that is. This is supposed to be done in "terminal", right?

Then I try to do the Automatrix thing only to find out that I cannot find it anywhere to be donwloaded. Not like it matters because I wouldn't be able to install it anyway!

I am about two seconds away from formatting this harddrive and throwing windows back on it! This is the whole reason Linux pisses me off so much! :evil: :evil: :evil:

And every time I ask about installing the **motherboard drivers**, everyone keeps referring me to stupid video drivers instead.

---

### Post by beerorkid on 2006-02-07
sorry to see you getting frustrated.  Linux can do that to ya in the beginning.

the main automatix thread: [http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)
the very first post has all of the information you will need to install and use.

For automatix enter in these lines into a terminal:
(to get to a terminal go applications --> accessories --> terminal)
enter each of the three lines seperately and press enter after each
```
sudo apt-get install xterm

wget http://beerorkid.com/automatix/automatix_5.3-3_i386.deb

sudo dpkg -i automatix_5.3-3_i386.deb
```

now the automatix program is installed in applications --> system tools --> automatix

follow the prompts to install stuff, you will every now and then have to enter your user password into a terminal.

Ubuntu is a little different in a few ways.  One would be the way to do things as a "superuser".
Root is disabled on an ubuntu machine.  Use "sudo" in before commands that need superuser/root permissions.

I think "sudo" stands for superuser do.

Do not give up, you will get it.

---

### Post by Brynster on 2006-02-07
[QUOTE=chopsbuntu]This is getting pretty freaking ridiculous.

I try doing what **kaamos** linked me to, and it keeps coming up saying that it can only be done by a "superuser", whatever the heck that is. This is supposed to be done in "terminal", right?

Then I try to do the Automatrix thing only to find out that I cannot find it anywhere to be donwloaded. Not like it matters because I wouldn't be able to install it anyway!

I am about two seconds away from formatting this harddrive and throwing windows back on it! This is the whole reason Linux pisses me off so much! :evil: :evil: :evil:

And every time I ask about installing the **motherboard drivers**, everyone keeps referring me to stupid video drivers instead.[/QUOTE]

1 if you followed Arnieboys instructions on installing Automatix then the program gets populated into the system tools menu. Click on that and it will through up a list of everything it can automatically install for you, one of which i am fairly certian is the latest Opera Browser.

2 Motherboard drivers. Which ones do you need exactly?  I have been running Linux for over 12 months and have installed Ubuntu on a multitude of differing motherboards and have never once need to install motherboard drivers. By motherboard drivers i am refering to things like the Hyperion 4 in 1 drivers or other associated drivers (ie northbridge or southbridge). Network cards and soundcards are on the whole covered by the built in Linux drivers. The only other thing that creates and issue are onboard graphics cars, which are really the only drivers that may need updating/installing

---

### Post by chopsbuntu on 2006-02-07
Thanks once again **berrorkid**!

Not only do I have Opera installed now, but I'm also running Kubuntu now which I like much better. I also installed several apps including a few utilities and even GnomeBaker. That Automatix really is a great help for the nOOb in me. LOL

**Brynster**, those are the drivers I was referring to. Since I guess I no longer have to worry about them, what about the proper driver for my AGP card. I mean, it works and gets me to my full resolution of 1280x1024 @ 75Hz, but everything is slightly soft and fuzzy looking. 

When I switch over to my XP machine, everything is razor sharp, but when I switch back over to Linux, it's not. The video card is an older Riva TNT2 with 32Mb is ram. Any suggestions? 

Also,I would just like to apologize for getting so upset earlier. I just have a short fuse when stuff like that gets to me. Sorry. ;)

---

### Post by gnottage on 2006-02-07
Some more info on drivers (as far as I know, I'm not an expert). Linux is basically a Kernel, and on top of that sits the GNU utilities and Gnome etc. The kernel has (or can have) either compiled in or as modules support for a very wide range of hardware. Ubuntu comes with a kernel full of support, where as other distro's which go for a lean approach don't have so much (and those who get you to build your own kernel, eg Gentoo, allow you to have just what you want). So the drivers for your motherboard are already in the OS. It's like M$ continually updating thier repository of drivers frequently, rather than letting the manufacturer distribute them.

If you want to know what packages to install, let us know what kind of things you want to do/try. Browse these forums and search and uncover the cool things!

---

### Post by chopsbuntu on 2006-02-08
I've got another question for you guys...

Why is it that for ANY of the little weather apps that I put on the desktop never work? 

They come default with Tokyo and they usually work, but once I change them to my location, they stop working. :confused: 

Liquid Weather for one... It worked just fine when I first installed it. Then I was changing the background image of it and loading some new icons for it, and now all it shows is that picture over the water with lightening, and all it says is "loading..." at the bottom. 

Also, how do you go about loading different DL'ed designs for the "Window Behavior" feature?

---

### Post by chopsbuntu on 2006-02-08
Hmm... :-k

---

### Post by beerorkid on 2006-02-08
yeah the weather one might be a subject for another post.  This forum is filled with peeps that love to answer questions, just have to search and ask :)  BTW I get the weather going and set it to my area, then I have to right click, choose update to get it to work.

I use the default "weather report" that can be installed on the pannel (aka task bar)  And living in nebraska it covers my area rather well.

Glad to see you are enjoying the linux environment.  I went back and looked at some of my posts from when I was just getting into it a year ago, and was a little embarrased.  It is the distro specific forums that keep the linux community thriving.

As far as window behaivor, I am thinking that that might be a KDE thing? I hope you have seen the [http://www.kde-look.org/](http://www.kde-look.org/) and [http://www.gnome-look.org/](http://www.gnome-look.org/) before, if not it is a great way to play around with apperances.  Beats the two schemes you can have with XP.

I never used gnome before switching to ubuntu, I do like it though.  I really enjoy how you can install KDE apps.  I use konqueror as my FTP client and so much more.  It is nice that the different desk top environments play nicely with eachother.

Not sure if you know but ubuntu with KDE is kubuntu, same thing just a little more specific when asking questions on the forum.  It is all ubuntu underneath;)

---

