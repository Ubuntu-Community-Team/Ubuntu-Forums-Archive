---
title: "How to download and install packages to a computer w/o internet?"
date: 2009-08-09
forum: General Help
---

### Post by rogueleader12345 on 2009-08-09
Hello. I have recently put Intrepid on my other computer, which is older and cannot connect to the internet. So I was wondering, how do I download the packages for say, Wine, Screenlets, etc. and install them? Is there a way I can just download them off this computer onto a flash drive and then install them on the other computer? Any help would be appreciated.

---

### Post by coldReactive on 2009-08-09
Some packages are released in such a way that they require Internet no matter what (IE: update-manager releases.)

But if you want to (though I don't know where they are downloaded to)

```
sudo apt-get -d install package_name_here
```

the -d option downloads the package, but doesn't install nor unpack it.

---

### Post by rogueleader12345 on 2009-08-09
Just tried that, but it acted like it was going to install it, here's the output.

root@ubuntu:/home/ubuntu# sudo apt-get -d install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 mplayer-skins
  linux-headers-2.6.28-11 libsvga1 mplayer
  libggi-target-x libmp3lame0
  linux-headers-2.6.28-11-generic libggi2
  libgii1 liblzo2-2 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.

---

### Post by burmanabhay88 on 2009-08-09
You can set up an offline repository.

Either google the details of setting one, or read the tutorial below.

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

### Post by coldReactive on 2009-08-09
> **burmanabhay88 said:**
> You can set up an offline repository.

Either google the details of setting one, or read the tutorial below.

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

What if you constantly need to update every week and don't have any RW disks?

---

### Post by rogueleader12345 on 2009-08-09
I was reading that and I just have a few packages I need, and that gives you EVERYTHING. Updates would be nice, but aren't necessary seeing how I have to use Intrepid.

---

### Post by P4man on 2009-08-09
This might be more practical than creating a complete offline ubuntu repo:

[http://basicubuntu.blogspot.com/2009/02/install-on-ubuntu-without-internet.html](http://basicubuntu.blogspot.com/2009/02/install-on-ubuntu-without-internet.html)

---

### Post by burmanabhay88 on 2009-08-09
> **coldReactive said:**
> What if you constantly need to update every week and don't have any RW disks?

you can set up offline repositories on a flash drive as well.

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by coldReactive on 2009-08-09
> **burmanabhay88 said:**
> you can set up offline repositories on a flash drive as well.

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

This is the last hijack post I'm posting.

I would rather see you be able to stream updates/repos from a computer on the internet through W/LAN to an offline computer connected through the W/LAN but not to the Internet.

---

### Post by rogueleader12345 on 2009-08-09
Can't do that. My other computer has no modem, and the LAN port is shot. No way it's getting online. Plus it's older than dirt.

---

### Post by rogueleader12345 on 2009-08-09
I would just like to find a way to get the .debs for the packages and get it over with, but I downloaded thw wine .deb and I tried to install it and it said missing dependency somethingsound or something like that.

---

### Post by rogueleader12345 on 2009-08-09
Tried making the repository, but it didn't work. Any one else have any ideas?

---

### Post by jaxxstorm on 2009-08-09
You can do 
```

sudo aptitude download packagename

```

It downloads the deb file to your home directory, you'll need to make sure you grab the dependencies with it too.

---

### Post by rogueleader12345 on 2009-08-09
Thank you all! I used [www.packages.ubuntu.com](www.packages.ubuntu.com) and now everything works splendidly! Again, thanks!!!!

---

### Post by coldReactive on 2009-08-09
> **rogueleader12345 said:**
> Thank you all! I used [www.packages.ubuntu.com](www.packages.ubuntu.com) and now everything works splendidly! Again, thanks!!!!

And for those who get a domain not found, or a DNS error:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by rogueleader12345 on 2009-08-09
Oops, yeah. Thanks.

---

### Post by mac9416 on 2009-08-10
> I would just like to find a way to get the .debs for the packages and get it over with, but I downloaded thw wine .deb and I tried to install it and it said missing dependency somethingsound or something like that.

rogueleader12345, packages.ubuntu.com is actually the hard way to do it. In order to get the dependencies and sub-dependencies, you have to click through a multitude of links and download a multitude of packages by hand.

The easy way is to use [Keryx]("http://keryxproject.org/"). You take Keryx to your online computer, download the software you want (it automatically gets the dependencies for you), and take it back to your offline machine to install them.

You still have to install the .debs by hand (or create a local repository, with the LocalRepo-Add.py script include with Keryx), but that will be changed in the coming Keryx 1.0.

Hope that helps you out!

---

### Post by P4man on 2009-08-10
Hmm, that Keryx looks interesting. one question though: is it possible to have that program detect and import debs already downloaded and in apt's cache on the "internet" pc ?

---

### Post by mac9416 on 2009-08-10
No, but that is an interesting idea. The easiest way to do that would be to simply copy the files into a project's "packages" directory. However, since Keryx does not have the ability to install the software for you, it's probably best to just copy the .debs directly out of the cache onto a flash drive and install them on your offline computer.

---

### Post by P4man on 2009-08-10
> **mac9416 said:**
> No, but that is an interesting idea. The easiest way to do that would be to simply copy the files into a project's "packages" directory. However, since Keryx does not have the ability to install the software for you, it's probably best to just copy the .debs directly out of the cache onto a flash drive and install them on your offline computer.

I'm not sure Im understanding you here... You mean copying the debs 'by hand' ? id really prefer to see your app (I think its yours?) determine if the needed packages are already in apt's cache, and only download them if they are not. Would save me a ton of bandwidth :) 

FWIW, now I use apt-cache, which works quite well on my own lan, but sometimes I go help out friends or ppl with slow or capped internet, and it would be neat if I could prepare a stick with new software / updates I want to install there. Even neater if I didn't have to download them yet again :)

---

### Post by mac9416 on 2009-08-10
Actually [Excid3]("http://ubuntuforums.org/member.php?u=289809") runs the project, but I'm a developer. :-)

Now I see. Have Keryx only download files that aren't in the cache, just like APT. That's a very good idea, and one I haven't thought of. I'll talk to Excid3 about putting that in the next release.

For right now, you can copy the .debs from your cache into a Keryx project's package folder. Keryx would then skip those files when downloading new software.

I hope that helps! :-)

---

### Post by EXCiD3 on 2009-08-10
I tried to reply to this earlier but received an error each time I tried it. Basically I just wanted to say I love the idea and that it's on the TODO list for Keryx 1.0. The reason we hadn't thought of that was that since Keryx is intended to run on Windows or Mac (something you might use at work or the library etc, it would be more common than linux) you wouldn't be able to do this obviously. Keryx, while it could use an online Linux machine, is intended more for the places where you couldn't use Synaptic download scripts or APTonCD. Obviously that means, Windows and Mac computers, but having a feature like you mentioned would be great for those people using Keryx on a connected computer that runs Linux. Shouldn't be too hard to implement at all, so look for it in the next version :D

---

### Post by bacardiandwatermelon on 2009-08-10
After using  Keryx.. Rather than installing manually, couldn't you just copy them to /var/cache/apt/archives and just then install them using synaptic?

---

### Post by zkriesse on 2009-08-10
NOTE:!!!!!!!!TO INSTALL A PACKAGE THE TERMINAL CODE IS! sudo aptitude install mozilla-thunderbird
for an example.

---

### Post by Cheesehead on 2009-08-10
Take a look at the apt-zip package:

Description: Update a non-networked computer using apt and removable media
 These scripts simplify the process of using dselect and apt on a
 non-networked Debian box, using removable media like ZIP floppies and
 USB keys.
 One generates a `fetch' script (supporting backends such as wget and
 lftp, in a modular, extensible way) to be run on a host with better
 connectivity, check space constraints of your removable media, and
 then install the package on your Debian box.

---

### Post by EXCiD3 on 2009-08-10
And to do all that with apt-zip on Windows without a GUI. Oh it would be so enjoyable...Not. ;)

---

### Post by P4man on 2009-08-10
> **Zachk18 said:**
> NOTE:!!!!!!!!TO INSTALL A PACKAGE THE TERMINAL CODE IS! sudo aptitude install mozilla-thunderbird
for an example.

actually, apt-get is probably the better choice these days. Not that any of this is relevant to this thread or to the OP who clearly knows how to install something.

---

### Post by P4man on 2009-08-10
> **EXCiD3 said:**
> I tried to reply to this earlier but received an error each time I tried it. Basically I just wanted to say I love the idea and that it's on the TODO list for Keryx 1.0. The reason we hadn't thought of that was that since Keryx is intended to run on Windows or Mac (something you might use at work or the library etc, it would be more common than linux) you wouldn't be able to do this obviously. Keryx, while it could use an online Linux machine, is intended more for the places where you couldn't use Synaptic download scripts or APTonCD. Obviously that means, Windows and Mac computers, but having a feature like you mentioned would be great for those people using Keryx on a connected computer that runs Linux. Shouldn't be too hard to implement at all, so look for it in the next version :D

cool, Ill be happy to check it out :)

Also a tip, if you're typing a long reply, make a habit of pressing cltr+A ctrl+C before hitting submit :D

edit: one more question: what do you use a "reference" for the dependencies ? Say I would select "gedit" from the repo's through your app, and Im going to install on a kubuntu machine...? I don't suppose it will prepare all of gnome ?

---

### Post by EXCiD3 on 2009-08-10
> **P4man said:**
> cool, Ill be happy to check it out :)

Also a tip, if you're typing a long reply, make a habit of pressing cltr+A ctrl+C before hitting submit :D


I always try to do that now, but it seems like the only time I don't is when it doesn't work :P

> 

edit: one more question: what do you use a "reference" for the dependencies ? Say I would select "gedit" from the repo's through your app, and Im going to install on a kubuntu machine...? I don't suppose it will prepare all of gnome ?What happens is I use the exact same information that apt-get does. :D You know hthe package lists that you get from an apt-get update? I just copy those over to the flash drive to access them from anywhere, read them through and keep track of doubles (which would be updates to one another) and then I read through the differnet fields:

Depends <- required
Pre-Depends <- required
Recommends <- apt tools like apt-get, aptitude, and synaptic always grab these too, so does Keryx
Suggests <- ignored for now, will add support for downloading these which are basically extra features/plugins

The only problem right now with the latest release is that I took the simple way out for now, some packages have a dependency like the following couple of examples:

packageX (>= 1.0)           - must be newer than 1.0
packageX | packageY       - either one is required to be installed
packageX (>= 1.0) | packageY (>= 1.0)

So what I do with these right now is I just download the latest version of packageX (which will almost always be newer than the restriction unless something wacky is going on) and I only make sure packageX is installed instead of packageX OR packageY because its simpler to do. These obviously need to be changed, but it can get kind of tricky being recursive.

When Keryx looks at packageX (>= 1.0) if it finds that packageX is installed, it moves on, if not, it selects packageX to be downloaded and then it checks packageX for its dependencies to make sure it can be properly installed as well.

The only reason I haven't finished that yet is because I've been really busy with work recently have just haven't had the time. It's my next goal to accomplish in the 0.92 series, while I've got a couple other devs working on the new 1.0 series which will be leaps and bounds better. :D

In short, we just basically mirror how apt tools calculate dependencies. If you select gedit in apt-get and get 11 dependencies, it will be (close to until i finish) the same in Keryx.

(Ctrl-A, Ctrl-C'd before I hit submit :lolflag:)

---

### Post by rogueleader12345 on 2009-08-11
Here guys. I just introduced an idea on brainstorm.ubuntu.com. If you like it, vote for it! 

[http://brainstorm.ubuntu.com/idea/21006/](http://brainstorm.ubuntu.com/idea/21006/)

---

### Post by EXCiD3 on 2009-08-11
The idea is marked as currently implemented, and it really is. The problem with things is that these existing tools must have access to the internet somewhere along the lines, and the list of dependencies can become very lengthy if you don't have the offline machine's status file. Keryx takes care of everything however and fills the gap where apt-zip and synaptic's download scripts don't.

---

### Post by slakkie on 2009-08-11
What about download the alternate cd and using apt-cdrom:

[http://www.debianadmin.com/add-cdroms-to-apts-sources-using-apt-cdrom.html](http://www.debianadmin.com/add-cdroms-to-apts-sources-using-apt-cdrom.html)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

