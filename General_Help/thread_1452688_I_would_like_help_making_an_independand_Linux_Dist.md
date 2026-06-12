---
title: "I would like help making an independand Linux Distribution based on Ubuntu"
date: 2010-04-12
forum: General Help
---

### Post by gosalia on 2010-04-12
Hello. I do not have much time so I will get into the question straight away.

I have change the variables inside the file lsb_release in etc/lsb_release to my needs. I have found that in doing so I cannot access the sources in synaptic or in Software Sources applications due to a TEMPLATE NOT FOUND error.

The error in return is something like this:- 
> removing transaction from pool :  "/201_edabcebd_data"      
removing transaction from pool :  "/202_abdeeacd_data"                          
Error: "/var/tmp/kdecache-ronakraj" is owned by uid 1000 instead of uid 0.      
Error: "/tmp/kde-ronakraj" is owned by uid 1000 instead of uid 0.               
Traceback (most recent call last):                                              
  File "/usr/bin/software-properties-kde", line 122, in <module>                
    app = SoftwarePropertiesKDE(datadir=data_dir, options=options, file=file, attachWinID=attachWinID)                                                          
  File "/usr/lib/python2.6/dist-packages/softwareproperties/kde/SoftwarePropertiesKDE.py", line 70, in __init__                                                 
    SoftwareProperties.__init__(self, options=options, datadir=datadir)         
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__                                                        
    self.reload_sourceslist()                                                   
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist                                             
    self.distro.get_sources(self.sourceslist)                                   
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
Error: "/var/tmp/kdecache-ronakraj" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ronakraj" is owned by uid 1000 instead of uid 0.
Traceback (most recent call last):
  File "/usr/bin/software-properties-kde", line 122, in <module>
    app = SoftwarePropertiesKDE(datadir=data_dir, options=options, file=file, attachWinID=attachWinID)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/kde/SoftwarePropertiesKDE.py", line 70, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)
AttributeError: 'NoneType' object has no attribute 'get_sources'
Error: "/var/tmp/kdecache-ronakraj" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ronakraj" is owned by uid 1000 instead of uid 0.
Traceback (most recent call last):
  File "/usr/bin/software-properties-kde", line 122, in <module>
    app = SoftwarePropertiesKDE(datadir=data_dir, options=options, file=file, attachWinID=attachWinID)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/kde/SoftwarePropertiesKDE.py", line 70, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)
AttributeError: 'NoneType' object has no attribute 'get_sources'

I want to know how I can create my own template for my Linux Distribution. What is involved? and What do I need to do to make this available on Gnome and KDE etc. Help would be much appreciated, thank you.

---

### Post by falconindy on 2010-04-12
Clearly, the package manager you're piggybacking off of is checking /etc/lsb_release during the update process. Unexpected data causes unexpected results.

If you wanted to create an **independent** distro, wouldn't one of the first steps be to use your own repositories?

---

### Post by 98cwitr on 2010-04-12
does Gosalia differ from gOS, to me one looks like Windows 7 and the other like a Mac (respectively)?

---

### Post by nixclusive on 2010-04-12
> .
.
Error: "/var/tmp/kdecache-ronakraj" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ronakraj" is owned by uid 1000 instead of uid 0. 
.
.

I suppose you have a file ownership issue here :)

---

### Post by nixclusive on 2010-04-12
> **falconindy said:**
> Clearly, the package manager you're piggybacking off of is checking /etc/lsb_release during the update process. Unexpected data causes unexpected results.

If you wanted to create an **independent** distro, wouldn't one of the first steps be to use your own repositories?

Ubuntu is built on Debian FYI. See [this page](http://www.ubuntu.com/community/ubuntustory/Debian).

---

### Post by MCVenom on 2010-04-12
Just curious, but how does your distro differ from Ubuntu, or Linux Mint for that matter? :p

---

### Post by falconindy on 2010-04-12
> **nixclusive said:**
> Ubuntu is built on Debian FYI. See [this page](http://www.ubuntu.com/community/ubuntustory/Debian).
Correct, but Ubuntu and Debian host and maintain their repositories separately. This is not clearly stated in your link, but it's evident if you go poking around sources.lst and compare it to that of a Debian release. It would have been better to point at a distro like Mint which uses Ubuntu's repositories. I'm not sure why this behavior is accepted, but it is. I can only assume that a deal was made behind the scenes between the developers of both camps.

---

### Post by ubiquitousblake on 2010-04-12
Hi! May I be so bold as to presume that you are assisting in the development of Gosalia? If so, I have to commend you on your customizations to the interface. However, when I went to boot the OS, it took quite a great deal of time! Also, many of your window labels, like your welcome center, still remain named Ubuntu.  
Just commenting, nothing malicious or demeaning. 

The Idea of a very Windows-esque UI without having to change a thing would be quite appealing to those Windows users of whom consider converting to Linux and are just too scared or lazy to either feel their way around a default layout or customize it. This look is more modern (windows 7) than in a distro like Linux Mint (XP) from the beginning, and Simulating the Superbar is wonderful. But other than the initial glance, it wont differ much from Linux Mint. And in fact, I believe that Mint is much more responsive. Buggy in my opinion, but since it's still in the beta stages I won't dare complain too blatantly (its not like I'm the one developing and putting my hard work into it). Good luck with your question! I wish I had a technical fix for you.

---

### Post by gosalia on 2010-04-13
> **BlackOtaku said:**
> Just curious, but how does your distro differ from Ubuntu, or Linux Mint for that matter? :p

Its faster, safer and easier to manage and handle. Currently are in BETA stage so STILL UNDERCONSTRUCTION obviously. But you can find out more at [www.gosalia.org](www.gosalia.org) and click TAKE THE TOUR.

---

### Post by gosalia on 2010-04-13
> **falconindy said:**
> Clearly, the package manager you're piggybacking off of is checking /etc/lsb_release during the update process. Unexpected data causes unexpected results.

If you wanted to create an **independent** distro, wouldn't one of the first steps be to use your own repositories?

Yes I agree, however I am only a simple coder at The Gosalia Enterprise and I want to astonish the boses of the project with knowing how to create repositories as I have been put on that task. I don't know how I can create my own repository, so if you do please tell me. And please don't go about telling me I am a noob, I am only a simple coder who has never been inside a real Operating System PROJECT.

---

### Post by gosalia on 2010-04-13
> **98cwitr said:**
> does Gosalia differ from gOS, to me one looks like Windows 7 and the other like a Mac (respectively)?
Ofcoarse it does. The Gosalia Enterprise's designers purposely created BETA 1 to look like Windows 7 for making it easy for Windows users who switch. BETA 2 will have KDE which will enable ease of access for Macintosh users aswell as Windows, and eventually we will have a third edition where it will be a desktop environment of our own with easy tools for ease of access.

We believe computing should be as easy as possible.

---

### Post by gosalia on 2010-04-13
> **nixclusive said:**
> I suppose you have a file ownership issue here :)

How can I fix this? I looked around that folder but found no root command. I know there is a command such as sudo chmod xxx, but what is the variable for the x pronumeral?

---

### Post by gosalia on 2010-04-13
> **nixclusive said:**
> Ubuntu is built on Debian FYI. See [this page](http://www.ubuntu.com/community/ubuntustory/Debian).

and the point is?

---

### Post by gosalia on 2010-04-13
> **falconindy said:**
> Correct, but Ubuntu and Debian host and maintain their repositories separately. This is not clearly stated in your link, but it's evident if you go poking around sources.lst and compare it to that of a Debian release. It would have been better to point at a distro like Mint which uses Ubuntu's repositories. I'm not sure why this behavior is accepted, but it is. I can only assume that a deal was made behind the scenes between the developers of both camps.

Are you sure? I thought MINT had its own repository.

---

### Post by gosalia on 2010-04-13
> **ubiquitousblake said:**
> Hi! May I be so bold as to presume that you are assisting in the development of Gosalia? If so, I have to commend you on your customizations to the interface. However, when I went to boot the OS, it took quite a great deal of time! Also, many of your window labels, like your welcome center, still remain named Ubuntu.  
Just commenting, nothing malicious or demeaning. 

The Idea of a very Windows-esque UI without having to change a thing would be quite appealing to those Windows users of whom consider converting to Linux and are just too scared or lazy to either feel their way around a default layout or customize it. This look is more modern (windows 7) than in a distro like Linux Mint (XP) from the beginning, and Simulating the Superbar is wonderful. But other than the initial glance, it wont differ much from Linux Mint. And in fact, I believe that Mint is much more responsive. Buggy in my opinion, but since it's still in the beta stages I won't dare complain too blatantly (its not like I'm the one developing and putting my hard work into it). Good luck with your question! I wish I had a technical fix for you.

Thank you for your comment, I will pass it on to the heads. I am glad you like the Windows interface, we are soon to put in KDE with loads of functions for both Macintosh and Windows Users. Also you mention that it is not different from Linux Mint or Ubuntu, can I ask you, out of curiosity, what do you think is not different and what do you think we should do?

This would help our team and I WILL pass your comments. Thanks in advance.

---

### Post by Frak on 2010-04-13
> **gosalia said:**
> Its faster, safer and easier to manage and handle. Currently are in BETA stage so STILL UNDERCONSTRUCTION obviously. But you can find out more at [www.gosalia.org](www.gosalia.org) and click TAKE THE TOUR.

> **gosalia said:**
> Yes I agree, however I am only a simple coder at The Gosalia Enterprise and I want to astonish the boses of the project with knowing how to create repositories as I have been put on that task. I don't know how I can create my own repository, so if you do please tell me. And please don't go about telling me I am a noob, I am only a simple coder who has never been inside a real Operating System PROJECT.

> **gosalia said:**
> Ofcoarse it does. The Gosalia Enterprise's designers purposely created BETA 1 to look like Windows 7 for making it easy for Windows users who switch. BETA 2 will have KDE which will enable ease of access for Macintosh users aswell as Windows, and eventually we will have a third edition where it will be a desktop environment of our own with easy tools for ease of access.

We believe computing should be as easy as possible.

> **gosalia said:**
> How can I fix this? I looked around that folder but found no root command. I know there is a command such as sudo chmod xxx, but what is the variable for the x pronumeral?

> **gosalia said:**
> and the point is?

> **gosalia said:**
> Are you sure? I thought MINT had its own repository.

> **gosalia said:**
> Thank you for your comment, I will pass it on to the heads. I am glad you like the Windows interface, we are soon to put in KDE with loads of functions for both Macintosh and Windows Users. Also you mention that it is not different from Linux Mint or Ubuntu, can I ask you, out of curiosity, what do you think is not different and what do you think we should do?

This would help our team and I WILL pass your comments. Thanks in advance.

C-C-C-COMBO BREAKER

Work on not infinity-posting. Anywho, on another forum that I won't name, we gave you some advice on what to do before you push a distribution as professional. You should seriously stick to those before marketing.

---

### Post by gosalia on 2010-04-13
> **Frak said:**
> C-C-C-COMBO BREAKER

Work on not infinity-posting. Anywho, on another forum that I won't name, we gave you some advice on what to do before you push a distribution as professional. You should seriously stick to those before marketing.

Sorry that was our head of Coding you were talking to. I am the graphical designer and all rounder.

---

### Post by clanky on 2010-04-13
> **gosalia said:**
> Sorry that was our head of Coding you were talking to. I am the graphical designer and all rounder.

And the two are different people?

---

### Post by gosalia on 2010-04-13
> **clanky said:**
> And the two are different people?

We have a universal account on many forums under the name - Gosalia. Who is on each account depends on the time people have to surf the internet. In this case, yes I and the person who went on the other forums previously mentioned, are two different people.

---

### Post by MCVenom on 2010-04-13
'Gosalia is one of the only Linux distributions in the world that supports... [various codecs]'

That's a bit misleading, I realize you're trying to push a product, but maybe you could say one of the only ones that provides out of the box support?

---

### Post by MCVenom on 2010-04-13
> **gosalia said:**
> Are you sure? I thought MINT had its own repository.
Mint uses an exclusive repo for some of the software unique to Linux Mint (ie: Mint Menu, Software/Update Manager, etc.) For everything else Mint uses Ubuntu repos.

---

### Post by gosalia on 2010-04-13
> **BlackOtaku said:**
> 'Gosalia is one of the only Linux distributions in the world that supports... [various codecs]'

That's a bit misleading, I realize you're trying to push a product, but maybe you could say one of the only ones that provides out of the box support?
Yes that is what we said, I believe, when we created the CREDITS page. We gave CREDITS to the vast software utilities we used, we have not created any softwares ourselves yet, but have enhanced and incorporated those of others to create an Distribution packed with "others" work, with full credits as deserved ofcoarse.

[http://www.gosalia.org/index.php?option=com_content&view=article&id=78&Itemid=59](http://www.gosalia.org/index.php?option=com_content&view=article&id=78&Itemid=59)

---

### Post by nixclusive on 2010-04-13
> **gosalia said:**
> We have a universal account on many forums under the name - Gosalia. Who is on each account depends on the time people have to surf the internet. In this case, yes I and the person who went on the other forums previously mentioned, are two different people.

I'm breaking my oath of not posting anything that does not help at all just to say you'll have an identity crisis :P
Anyways, back to your error, I'm not sure what you need to change to fix that error. However, it looks like changing ownership of the files being used to uid 0 should help.

```
chown 0:0 <filename>
or
chown 0:0 <directoryname> [-R]
```
-R flag to do it recursively.

Regards.

---

### Post by Søren on 2010-04-13
*Makes mental note to avoid gosalia*

---

### Post by ubiquitousblake on 2010-04-13
> **gosalia said:**
> Thank you for your comment, I will pass it on to the heads. I am glad you like the Windows interface, we are soon to put in KDE with loads of functions for both Macintosh and Windows Users. Also you mention that it is not different from Linux Mint or Ubuntu, can I ask you, out of curiosity, what do you think is not different and what do you think we should do?

This would help our team and I WILL pass your comments. Thanks in advance.

Over all, the theme and idea of this system are well formed. They incorporate the power and popularity of the GNU Linux platform, as well as the elegance of current proprietary systems that most people currently use. However, to differentiate your product from that which you derive it, you must have a very profound point. A simple UI modification would not be sufficient to necessitate your product, as appealing as the idea of native system elegance may be. 

For example, Ubuntu's purpose is to give Debian Linux a more frequent and stable release cycle, as well as to make it more simple and more user friendly. With the backing of Canonical and the community, this is largely achieved. Linux Mint prides itself on being almost totally community driven. Though Ubuntu has a larger community overall, Linux Mint has a larger ratio of users actively participating in the community and developing. Even other systems such as Ubuntu Studio and Kubuntu have a main focus. Now, I'm not saying you don't have one, but I am saying that it is difficult to perceive. 

If you were to differentiate your product from other similarly derived Linux distributions, I may suggest that you target a specific platform. I find great need for battery optimization on Linux running on laptops. Netbooks have software that is optimized for their form factor, while laptops run the same version of the OS designed for desktops. Horrible battery management ensues. Mac OS X is able to ensure long battery life because Apple manufactures both the hardware and the software. Making managing battery life very native to them.

With Linux, and Windows, this luxury does not exist. Perhaps, however, you could make a very laptop friendly distribution targeting mobile users that need the power of a desktop with the battery life of a netbook. This is where your distribution owuld be highlighted. Make a distribution that focuses on something like battery life, and you are guaranteed a large user base. With the power and versitility of GNU Linux coupled with its large software base and already large community, all you have to do is bring the elements togeather. 

In retrospect, if you could target laptop users who need battery life and powerful software resources, I could not only see the necesity of your distrobution but I would actively support it. However, as I previously stated in my original post, you have quite a bit of work to do. In Ubuntu 10.04, HAL is totally removed from system boot-up. This decreases boot time largely. Couple this quick start time with highly effecient battery managment, as well as a very optimized UI for proprietary users, and you have a very well planned OS. Again, this is an example of a point that you utilize in building your system. Others exsist, but in my opinion, there lays a large base of users that would migrate to you should you tap into their craving for battery managment on the larger laptop platform. 

Best of luck in your ventures!!! =D

---

### Post by ubiquitousblake on 2010-04-13
> **BlackOtaku said:**
> 'Gosalia is one of the only Linux distributions in the world that supports... [various codecs]'

That's a bit misleading, I realize you're trying to push a product, but maybe you could say one of the only ones that provides out of the box support?


Totally agree here. The statement is misleading. Installing codecs is super simple and easy. However, users probably wont know which to install if they're not very savvy with computers in general. Make these codecs standard with the installation and you'll have a valid marketing point!

---

### Post by Søren on 2010-04-13
I thought sabayon came read to rock 'n roll with all that stuff?

---

### Post by gosalia on 2010-04-14
> **ubiquitousblake said:**
> Over all, the theme and idea of this system are well formed. They incorporate the power and popularity of the GNU Linux platform, as well as the elegance of current proprietary systems that most people currently use. However, to differentiate your product from that which you derive it, you must have a very profound point. A simple UI modification would not be sufficient to necessitate your product, as appealing as the idea of native system elegance may be. 

For example, Ubuntu's purpose is to give Debian Linux a more frequent and stable release cycle, as well as to make it more simple and more user friendly. With the backing of Canonical and the community, this is largely achieved. Linux Mint prides itself on being almost totally community driven. Though Ubuntu has a larger community overall, Linux Mint has a larger ratio of users actively participating in the community and developing. Even other systems such as Ubuntu Studio and Kubuntu have a main focus. Now, I'm not saying you don't have one, but I am saying that it is difficult to perceive. 

If you were to differentiate your product from other similarly derived Linux distributions, I may suggest that you target a specific platform. I find great need for battery optimization on Linux running on laptops. Netbooks have software that is optimized for their form factor, while laptops run the same version of the OS designed for desktops. Horrible battery management ensues. Mac OS X is able to ensure long battery life because Apple manufactures both the hardware and the software. Making managing battery life very native to them.

With Linux, and Windows, this luxury does not exist. Perhaps, however, you could make a very laptop friendly distribution targeting mobile users that need the power of a desktop with the battery life of a netbook. This is where your distribution owuld be highlighted. Make a distribution that focuses on something like battery life, and you are guaranteed a large user base. With the power and versitility of GNU Linux coupled with its large software base and already large community, all you have to do is bring the elements togeather. 

In retrospect, if you could target laptop users who need battery life and powerful software resources, I could not only see the necesity of your distrobution but I would actively support it. However, as I previously stated in my original post, you have quite a bit of work to do. In Ubuntu 10.04, HAL is totally removed from system boot-up. This decreases boot time largely. Couple this quick start time with highly effecient battery managment, as well as a very optimized UI for proprietary users, and you have a very well planned OS. Again, this is an example of a point that you utilize in building your system. Others exsist, but in my opinion, there lays a large base of users that would migrate to you should you tap into their craving for battery managment on the larger laptop platform. 

Best of luck in your ventures!!! =D

Hey thank you so much for your feedback. I forwarded it to our heads and they confirmed the idea. I think we are going to create BETA 2 with a Desktop Download and also with a Laptop Download. The Laptop Download will have fast bootup and will be battery-efficient. If you want to help us more, which would be highly appreciated by us, please goto our forums at [www.gosalia.org/forums](www.gosalia.org/forums) and send your ideas. At this rate, we believe your ideas will be highly prioritized and I think the heads will most likely work on your ideas. Thank you so much for your help.
:)

---

### Post by gosalia on 2010-04-14
> **ubiquitousblake said:**
> Totally agree here. The statement is misleading. Installing codecs is super simple and easy. However, users probably wont know which to install if they're not very savvy with computers in general. Make these codecs standard with the installation and you'll have a valid marketing point!

What do you mean, can you specify more please.

---

### Post by ubiquitousblake on 2010-04-15
> **gosalia said:**
> What do you mean, can you specify more please.

Of course. 

When we Ubuntu users try to play a media file with its respective player, and the codec of said file does not exist on the system, the system reaches out to the repositories to find the correct codec(s). Usually these codecs are named such things as gstreamer plugins-ugly (or something of the sort). Now, because most current Linux users know which codecs they may or may not need, doesn't mean that proprietary users will or wont. But with ***new** *Linux users, there are two put-offs: First, GStreamer (they'll wonder what GStreamer is); Second, the word ugly is in the plugin. Now this is very ridiculous, but if they're already unsure what they're installing then this will make them totally reconsider installing anything without some form of instruction. 

My first proposition is to include GStreamer plugins for audio playback (mp3, m4a, ogg) My second proposition is to include VLC as the standard video player. In this respect two birds will fall with one stone: no video codecs will be required (though they're usually coupled with the audio codecs); no DVD decoding libraries will need to be installed by the user (or developers)! I use this combination when installing Ubuntu on any computer for anyone. I've always received satisfaction from each and every person for whom I've done this so far. 

Perhaps you could also consider a more powerful audio player? I love Rhythmbox because it's light-weight and very well integrated with Ubuntu. However, a more universal audio player like SongBird would probably be more appealing to a wider user base. It has a very appealing UI, large add-on library, and very powerful tools like a built in browser. Though, the add-ons take the cake in the limelight. Also, it's available for Windows and Mac OS X. Windows and Mac users are either already stuck to SongBird or iTunes (most probably one of these two) because of their power. To see this as the default on Gosalia would probably make the transition that much easier to them. 

One last thing! Include flash from install! Some users have had problems with flash on Linux. Configuring this to work out-of-the-box would save users the hassle of poorly attempting to configure it themselves should anything go awry. Of course, this means respective configuration of flash for the 32bit and 64bit architectures, but I believe that this would even impress many other distribution users. That you would take the time and care to ensure such surreal usability is pleasurably appealing. 

The fact is, that the majority of people don't want to configure their system in any way. They NEED everything to work natively because they're too lazy to learn to do things themselves. People who have never heard of Linux will be ill with the fear of the unknown. More over, people who have heard of Linux and have strong feelings against it feel so because, supposedly, "...a user should never have to open a damned bash terminal to configure anything...". This is something that SUSE is quite well known for, and is highly applauded for. 

Looking back, I've written quite a bit! But in brief, the workload is not so much compared to the potential gains. Install codecs, change the audio and video default players, and include flash. Simple enough in theory. Many Linux users may feel differently towards these ideas. 'Why make an open source variant conform to proprietary standards?' Well, that's where the people are. We want to show them that Linux is not only horrendously fast, infamously stable, and almost infinitly customizable. But we want to show them that it can be just as simple and easy to operate as the proprietary systems that they've grown comfortable with! 

The task before you is daunting! An unwavering resolve is needed to challenge the "Evil Empire"! But together, I'm confident that Linux can become the dominant OS on both the consumer and buisness computing platforms together! 

Again, good luck with Gosalia! =P

---

### Post by nixclusive on 2010-04-15
> **ubiquitousblake said:**
> ... Install codecs, change the audio and video default players, and include flash. ...

Don't forget to inform your users the various licenses they need to accept before using proprietary codecs and flash :)

---

### Post by ubiquitousblake on 2010-04-15
> **nixclusive said:**
> Don't forget to inform your users the various licenses they need to accept before using proprietary codecs and flash :)

Of course! How could I forget to mention that? This is a most important thing to include in this.

---

### Post by gosalia on 2010-04-15
> **ubiquitousblake said:**
> Of course. 

When we Ubuntu users try to play a media file with its respective player, and the codec of said file does not exist on the system, the system reaches out to the repositories to find the correct codec(s). Usually these codecs are named such things as gstreamer plugins-ugly (or something of the sort). Now, because most current Linux users know which codecs they may or may not need, doesn't mean that proprietary users will or wont. But with ***new** *Linux users, there are two put-offs: First, GStreamer (they'll wonder what GStreamer is); Second, the word ugly is in the plugin. Now this is very ridiculous, but if they're already unsure what they're installing then this will make them totally reconsider installing anything without some form of instruction. 

My first proposition is to include GStreamer plugins for audio playback (mp3, m4a, ogg) My second proposition is to include VLC as the standard video player. In this respect two birds will fall with one stone: no video codecs will be required (though they're usually coupled with the audio codecs); no DVD decoding libraries will need to be installed by the user (or developers)! I use this combination when installing Ubuntu on any computer for anyone. I've always received satisfaction from each and every person for whom I've done this so far. 

Perhaps you could also consider a more powerful audio player? I love Rhythmbox because it's light-weight and very well integrated with Ubuntu. However, a more universal audio player like SongBird would probably be more appealing to a wider user base. It has a very appealing UI, large add-on library, and very powerful tools like a built in browser. Though, the add-ons take the cake in the limelight. Also, it's available for Windows and Mac OS X. Windows and Mac users are either already stuck to SongBird or iTunes (most probably one of these two) because of their power. To see this as the default on Gosalia would probably make the transition that much easier to them. 

One last thing! Include flash from install! Some users have had problems with flash on Linux. Configuring this to work out-of-the-box would save users the hassle of poorly attempting to configure it themselves should anything go awry. Of course, this means respective configuration of flash for the 32bit and 64bit architectures, but I believe that this would even impress many other distribution users. That you would take the time and care to ensure such surreal usability is pleasurably appealing. 

The fact is, that the majority of people don't want to configure their system in any way. They NEED everything to work natively because they're too lazy to learn to do things themselves. People who have never heard of Linux will be ill with the fear of the unknown. More over, people who have heard of Linux and have strong feelings against it feel so because, supposedly, "...a user should never have to open a damned bash terminal to configure anything...". This is something that SUSE is quite well known for, and is highly applauded for. 

Looking back, I've written quite a bit! But in brief, the workload is not so much compared to the potential gains. Install codecs, change the audio and video default players, and include flash. Simple enough in theory. Many Linux users may feel differently towards these ideas. 'Why make an open source variant conform to proprietary standards?' Well, that's where the people are. We want to show them that Linux is not only horrendously fast, infamously stable, and almost infinitly customizable. But we want to show them that it can be just as simple and easy to operate as the proprietary systems that they've grown comfortable with! 

The task before you is daunting! An unwavering resolve is needed to challenge the "Evil Empire"! But together, I'm confident that Linux can become the dominant OS on both the consumer and buisness computing platforms together! 

Again, good luck with Gosalia! =P

WOW! Wherever you come from, God bless that place. Your incredible. Just spectacular. I would just like to take this time into saying, "THANK YOU" once again, your just marvellous and a great addition to Gosalia, Ubuntu and the whole wide Linux itself. 

Into your suggestions, I would like to alert you, that eventhough we did not publicise it as much as we should have, we do have codecs for all popular media outlets, even including mp4 and wma. Also, we will look into SongBird, I think I like its UI aswell, and as a default player in Gosalia, it would uniformly fit very nicely with Gosalia's sustainable desktop.

Also, you will be pleased to know, that should you need flash, you will be able to immediatelly access it in BETA 1. We have included and installed Flash onto Gosalia and you can view flash sites, videos etc. As I said before, these minor things have not been publicized enough, and obviously, they are vital and would help make Gosalia stand out, will be used when implementing advertisement ways of exposing this incredible advantage in Gosalia - like no other Linux Distribution.

---

### Post by ubiquitousblake on 2010-04-15
> **gosalia said:**
> WOW! Wherever you come from, God bless that place. Your incredible. Just spectacular. I would just like to take this time into saying, "THANK YOU" once again, your just marvellous and a great addition to Gosalia, Ubuntu and the whole wide Linux itself. 

Into your suggestions, I would like to alert you, that eventhough we did not publicise it as much as we should have, we do have codecs for all popular media outlets, even including mp4 and wma. Also, we will look into SongBird, I think I like its UI aswell, and as a default player in Gosalia, it would uniformly fit very nicely with Gosalia's sustainable desktop.

Also, you will be pleased to know, that should you need flash, you will be able to immediatelly access it in BETA 1. We have included and installed Flash onto Gosalia and you can view flash sites, videos etc. As I said before, these minor things have not been publicized enough, and obviously, they are vital and would help make Gosalia stand out, will be used when implementing advertisement ways of exposing this incredible advantage in Gosalia - like no other Linux Distribution.


I'm flattered. Truly! However, in comparison to the hard working developers I'm nothing. I'm not the one making a new distribution- you are. I support any software that promotes open source ideals. Especially software that IS open source. I will help you to the best of my ability should you care to allow me.            

Best of luck! =)

---

### Post by gosalia on 2010-04-16
> **ubiquitousblake said:**
> I'm flattered. Truly! However, in comparison to the hard working developers I'm nothing. I'm not the one making a new distribution- you are. I support any software that promotes open source ideals. Especially software that IS open source. I will help you to the best of my ability should you care to allow me.            

Best of luck! =)

Ofcoarse the technical side is upto us, but we need brains like yours. Without innovative ideas such as yours, we are nothing.

We definetely allow you, speak as you will about Gosalia, I give you my word. :)

---

