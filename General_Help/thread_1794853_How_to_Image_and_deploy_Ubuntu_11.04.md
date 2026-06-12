---
title: "How to Image and deploy Ubuntu 11.04"
date: 2011-07-01
forum: General Help
---

### Post by pinkfloyd65 on 2011-07-01
I work for an independent school where most of our computers run Windows 7 and Mac OS X. I've started installing Ubuntu (11.04) on some of our older machines, thus introducing Linux to our environment and recycling computers which would otherwise be candidates for the garbage truck.
While I am familiar with imaging and deploying Windows and Mac OS, I am lost when it comes to Linux. I have set up a computer with all of the settings and applications that I would like the other computers to have. 

Could you please provide (step-by-step) instructions on how can I image that reference machine and then transfer that image onto another PC?

Thank you in advance for your help,

---

### Post by Habitual on 2011-07-01
RemasterSys and/or Clonezilla for starters.

---

### Post by ClientAlive on 2011-07-01
> **Habitual said:**
> RemasterSys and/or Clonezilla for starters.


Yes. +1.

I haven't used remastersys but I have used clonezilla litely. It's worked well for what I've used it for and they claim some pretty fantastic capabilities - cloning/ deployment wise. It's text based but easy enough/ intuitive enough to follow.

[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

---

### Post by pinkfloyd65 on 2011-07-02
Thanks for the advice. I will look into those options and give it a try. I wish that Linux had an easy way to image and distribute customized images like Windows and Mac have...I would definitely help push Linux into enterprises rather than just keep it in the Server room or on individual (geeky) users desktops.

---

### Post by Roasted on 2011-07-02
Give FOG a try. I use FOG for imaging Windows systems at work, and as we begin to move into Ubuntu on our systems I plan to use FOG for it as well.

Windows has no good way to distribute images. It just doesn't. I went to a deployment conference in regard to Server 2008 and it crashed on stage and they were never able to show us how it worked. I continued to use FOG and until this day, it's worked beautifully. Sure, some road bumps, but nothing I couldn't figure out.

FOG is Linux based, so it has to run on a Linux server of some sort. I run it on Ubuntu 11.04 and 10.04 just fine. It can not run on Windows, even though its primary focus was to image Windows, however, like I said it does have Linux imaging capability.

Clonezilla is fantastic. Let me rephrase. Clonezilla LIVE is fantastic. Clonezilla Server is something I never got fully set up. That was my original intention until I found FOG. I spent weeks trying to set up Clonezilla Server. I even posted exact step by step directions on my setup. If I clicked the mouse or typed a keystroke, I documented it. I sent the steps to the developers and they said they duplicated my setup and it worked great. My setup? It didn't work. That's when I found FOG and I haven't looked back since.

Nothing beats Clonezilla Live for single instances of imaging.
Nothing beats FOG for multiple instances of imaging over the network.

Both I highly recommend. Good luck with wherever you end up.


> **pinkfloyd65 said:**
> ...rather than just keep it in the Server room or on individual (geeky) users desktops.


Hey hey hey there! I know quite a few Linux users who are the last thing from computer literate and/or geeky. It's really a great platform for any user of any level to use now-a-days. :)

---

### Post by pinkfloyd65 on 2011-07-02
Roasted,

Thanks for the informative reply. 

My plan is to give Clonezilla Live a try at first, since I have only about a handful of old (Windows) machines which I want to "convert" to Linux. If I see that it catches on, and I decide to expand our Linux base, I will definitely look into the FOG solution that you mention. 

BTW, you said that for FOG, I need a Linux server...Would it work even if that Linux server is a virtual server (running on a Windows host machine)?

Thanks

---

### Post by ClientAlive on 2011-07-02
[http://news.netcraft.com/archives/2011/03/09/march-2011-web-server-survey.html](http://news.netcraft.com/archives/2011/03/09/march-2011-web-server-survey.html)

---

### Post by Roasted on 2011-07-02
> **pinkfloyd65 said:**
> Roasted,

Thanks for the informative reply. 

My plan is to give Clonezilla Live a try at first, since I have only about a handful of old (Windows) machines which I want to "convert" to Linux. If I see that it catches on, and I decide to expand our Linux base, I will definitely look into the FOG solution that you mention. 

BTW, you said that for FOG, I need a Linux server...Would it work even if that Linux server is a virtual server (running on a Windows host machine)?

Thanks

Clonezilla Live is truly beautiful for small setups. We have about 2,000 systems though, so Clonezilla Live for us to mass deploy is a little difficult. :) Give it a shot though. I love CZ Live. But like I said, once you begin to get a little larger, try out FOG... I love both projects.

I'm not sure about using a virtual server. I don't think it's recommended, as you need a lot of disk space. Quite honestly, the Linux server doesn't need a lot. My laptop acts as a mobile imaging server that I take to other buildings. On top of that, my main imaging server is a 3.0ghz Pentium 4 single core with 1GB of RAM. The key thing is to have a gigabit network port. If you have a gigabit network port and *some* processing power, it'll do the job beautifully. A FOG server does not need a lot of horsepower at all, besides the gigabit network port.


> **ClientAlive said:**
> [http://news.netcraft.com/archives/2011/03/09/march-2011-web-server-survey.html](http://news.netcraft.com/archives/2011/03/09/march-2011-web-server-survey.html)

Forgive me if I sound naive, but what were you getting at with this link?

---

### Post by ClientAlive on 2011-07-02
> **pinkfloyd65 said:**
> 
BTW, you said that for FOG, I need a Linux server...Would it work even if that Linux server is a virtual server (running on a Windows host machine)?
Thanks


It should.

---

### Post by ClientAlive on 2011-07-02
> **Roasted said:**
> 
Forgive me if I sound naive, but what were you getting at with this link?


It sounded as if the op had a question about Linux use in industry. I thought I would be helpful and offer him some data on the subject.

:)

---

### Post by pinkfloyd65 on 2011-07-02
ClientAlive,

Thanks for the Clonezilla recommendation and also for the graph re: Linux in industries. Although I am a Windows certified professional, I use Macs extensively and consider myself a Linux newbie, starting to like Linux more and more and getting more interested in it.

However, the graphs in the link you provided show merely the ubiquity of the Apache platform on the Internet and that is a well know (and appreciated) fact. But this does not in any way testify to the acceptance of Linux in the enterprise, corporate environment (at least in the US...). Linux and its web server, Apache are confined to the server room, while the desktop is ruled largely by Windows (despite some inroads made by Macs). 

Take a look at this report from Feb. 2009: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121")
For 2011, this is the count: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y")

Windows is by far the most used OS, with Mac a distant second and Linux barely visible.

Personally, I would love to introduce Linux in the enterprise more and that is why I want to deploy it at my school, slowly, in phases and hope that it will catch on. But to become more accepted, Linux must become as easy to use as Macs and as intuitive for administrators as Windows.

Cheers

---

### Post by ClientAlive on 2011-07-02
> **pinkfloyd65 said:**
> ClientAlive,

Thanks for the Clonezilla recommendation and also for the graph re: Linux in industries. Although I am a Windows certified professional, I use Macs extensively and consider myself a Linux newbie, starting to like Linux more and more and getting more interested in it.

However, the graphs in the link you provided show merely the ubiquity of the Apache platform on the Internet and that is a well know (and appreciated) fact. But this does not in any way testify to the acceptance of Linux in the enterprise, corporate environment (at least in the US...). Linux and its web server, Apache are confined to the server room, while the desktop is ruled largely by Windows (despite some inroads made by Macs). 

Take a look at this report from Feb. 2009: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121")
For 2011, this is the count: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y")

Windows is by far the most used OS, with Mac a distant second and Linux barely visible.

Personally, I would love to introduce Linux in the enterprise more and that is why I want to deploy it at my school, slowly, in phases and hope that it will catch on. But to become more accepted, Linux must become as easy to use as Macs and as intuitive for administrators as Windows.

Cheers


Right on. Thanks for the links.

:)

---

### Post by Roasted on 2011-07-04
> **pinkfloyd65 said:**
> ClientAlive,

Thanks for the Clonezilla recommendation and also for the graph re: Linux in industries. Although I am a Windows certified professional, I use Macs extensively and consider myself a Linux newbie, starting to like Linux more and more and getting more interested in it.

However, the graphs in the link you provided show merely the ubiquity of the Apache platform on the Internet and that is a well know (and appreciated) fact. But this does not in any way testify to the acceptance of Linux in the enterprise, corporate environment (at least in the US...). Linux and its web server, Apache are confined to the server room, while the desktop is ruled largely by Windows (despite some inroads made by Macs). 

Take a look at this report from Feb. 2009: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=M&qpsp=121")
For 2011, this is the count: [http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y]("http://marketshare.hitslink.com/report.aspx?qprid=8&qptimeframe=Y")

Windows is by far the most used OS, with Mac a distant second and Linux barely visible.

Personally, I would love to introduce Linux in the enterprise more and that is why I want to deploy it at my school, slowly, in phases and hope that it will catch on. But to become more accepted, Linux must become as easy to use as Macs and as intuitive for administrators as Windows.

Cheers

Linux is relatively easy to use by default as it is. The thing is, far too many people confuse what's familiar and what's easy to use. People know Windows, and thereby think that's easy to use. 

I like how you notated "at least in the US." That's very important. We're late to the game. Period. But I'm excited to say my place of work (school district) and a lot of the districts in the area are in the process of either transitioning to Linux or already transitioned to Linux. It'll be interesting to see how the next year or so pans out.

So far, so good.

---

### Post by pinkfloyd65 on 2011-07-07
> **Roasted said:**
> Linux is relatively easy to use by default as it is. The thing is, far too many people confuse what's familiar and what's easy to use. People know Windows, and thereby think that's easy to use. 

But the question should be "Why do people perceive Mac and Windows to be easy to use?" Because they are intuitive, hands on, GUI-based, no dreaded command line or complicated un-tar.gz crap to deal with. You just double click and....BOOM! stuff gets installed. 
To be accepted in school, the corporate environment and every where else, Linux must loose some of its geeky image and get on with the program. As an IT guy, I like to mess around with command line and all kind of other stuff, but for the majority of the users, that is an intollerable drag. One doesn't have to know mechanics in order to drive a car - I agree with this! 

If I have to go through hoops to install an application, compress or uncompress it, check the version of my OS or access an external HD (do away with the stupid mount!) then I rather work with a Mac where every thing works and it is a secure OS. (just playing Devil's advocate here, guys, don't lynch me, I'm on your side!).

Annyway, that my opinion as a Windows/Mac/Linux user...I welcome yours.

---

### Post by pinkfloyd65 on 2011-07-07
Hey Roasted,

I wanted to follow up and let you know that I used Clonezilla Live as recommended and, after a few false starts and some tinkering around, I was able to clone the Ubuntu HD and restore it successfully to another computer. 

Some of the problems encountered were:
- I wanted to use an external HD to host the image, but Clonezilla did not recognized it (I had to reformat it to ext4)
- The first restore failed, since the external HD where the image was located, was a different size than the computer's HD?!? That never happened to me when imaging/restoring for Windows/Mac. Solution: I repartioned the HD so that the partition containing the image was about the size of the computer HD.
Al worked well after that!:p

Thank you all for the help.

---

### Post by ClientAlive on 2011-07-08
> **pinkfloyd65 said:**
> 
- The first restore failed, since the external HD where the image was located, was a different size than the computer's HD?!? That never happened to me when imaging/restoring for Windows/Mac. Solution: I repartioned the HD so that the partition containing the image was about the size of the computer HD.
Al worked well after that!:p

Thank you all for the help.


That does seem odd. I know clonezilla requires the restore destination to be the same size or greater than the partition or drive (depending on the option you chose) that it was taken from. I've had to deal with that and it's a pain in the rear. For it to have a problem related to the size of the drive you store the image on seems weird though. Wonder where that comes from?
--------------------

Edit:

I've heard that remastersys doesn't do that but I've never used it so I wouldn't know for sure.

---

### Post by kanishkdudeja on 2011-07-08
+1 for Remastersys.

Works wonderfully well..:)

The owner maintains a good forum to help you if you run into any problems.

You can check it out at:

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by pinkfloyd65 on 2011-07-09
> **ClientAlive said:**
> That does seem odd. I know clonezilla requires the restore destination to be the same size or greater than the partition or drive (depending on the option you chose) that it was taken from. I've had to deal with that and it's a pain in the rear. For it to have a problem related to the size of the drive you store the image on seems weird though. Wonder where that comes from?

I used a 40 GB external HD to save the Ubuntu image from a computer with a 20 GB HD. When I proceeded to restore the saved image onto an identical computer (i.e with a 20 GB HD), the process failed with some sort of a message hinting to the fact that there is not enough space on the destination, blah, blah, blah....
That's when I partitioned the 40 GB HD to 2 partions: one included the image, the other one empty of data. During the restore process, I chose the partition with the image as the source and it all went on smoothly. Go figure!

---

### Post by pinkfloyd65 on 2011-07-09
Kanishkudeja,

I followed the URL in your post and read through the site. One thing: in order to install Remastersys, I have to add the remastersys repository to the sources list, but there was no version for Natty (the latest was Lucid)...

---

### Post by kanishkdudeja on 2011-07-10
> **pinkfloyd65 said:**
> Kanishkudeja,

I followed the URL in your post and read through the site. One thing: in order to install Remastersys, I have to add the remastersys repository to the sources list, but there was no version for Natty (the latest was Lucid)...

On the remastersys site, on the ubuntu page( [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html) ), you can see this:

For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

So all versions newer than Lucid will be covered in this option..

---

### Post by ClientAlive on 2011-07-11
> **pinkfloyd65 said:**
> Kanishkudeja,

I followed the URL in your post and read through the site. One thing: in order to install Remastersys, I have to add the remastersys repository to the sources list, but there was no version for Natty (the latest was Lucid)...


Natty can use the repos for the previous vertsion. I used to use Natty for a while and had to deal with that myself.

---

### Post by kanishkdudeja on 2011-07-13
> **clientalive said:**
> natty can use the repos for the previous vertsion. I used to use natty for a while and had to deal with that myself.

+1

---

### Post by pinkfloyd65 on 2011-07-13
> **kanishkdudeja said:**
> On the remastersys site, on the ubuntu page( [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html) ), you can see this:

For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

So all versions newer than Lucid will be covered in this option..

Yeah, but I'm using Natty...I really don't care about the versions "newer than Lucid"....

---

### Post by ClientAlive on 2011-07-15
> **pinkfloyd65 said:**
> Yeah, but I'm using Natty...I really don't care about the versions "newer than Lucid"....


Natty is the newest release of Ubuntu out now. The other's are 'older' releases. Natty does not have repos for everything like it should (whatever the reason) so, sometimes, you have to use the repo for the previous version. It works for Natty too. Just don't try to go way too far back as then you might experience problems. One or two releases back should work fine for Natty (11.04).

:)

---

### Post by bodhi.zazen on 2011-07-15
Remastersys works well for "simple" backups / deployment.

Making a custom iso with the debian-live scripts is far more versatile.

---

