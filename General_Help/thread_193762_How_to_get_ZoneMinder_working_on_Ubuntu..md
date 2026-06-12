---
title: "How to get ZoneMinder working on Ubuntu."
date: 2006-06-10
forum: General Help
---

### Post by solarwind on 2006-06-10
Hello everyone,

I need to get ZoneMinder working on Ubuntu. I got so far as to configure, make and make install without errors. (I had to get some depencies along the way. But when I try to start it up, I get errors. Can anyone write a short tutorial to get ZoneMinder working on Ubuntu? Has anyone ever done it?

---

### Post by BrownieMan on 2006-06-22
[QUOTE=solarwind]Hello everyone,

I need to get ZoneMinder working on Ubuntu. I got so far as to configure, make and make install without errors. (I had to get some depencies along the way. But when I try to start it up, I get errors. Can anyone write a short tutorial to get ZoneMinder working on Ubuntu? Has anyone ever done it?[/QUOTE]

If you can post the steps you went through tog et Zoneminder on 6.06 working that would help a lot. Also post the errors you get. I havn't been able to get the thing make install to work yet, so right now you're further than most.

Post as much information as you possibly can, the more the better.

---

### Post by davekelly1979 on 2006-07-18
I was able to get it to install on 6.06 and the services start without error.  However, from there I'm stumped.  I point my web browser to my IP. my loopback, "localhost" and still nothing.  I don't know what else I need to do to configure Zoneminder and actually do anyhing!  Probably something dumb I overlooked, but it those things tend to drive me nuts till I find 'em...  :)  Anywho, here's what I did to get the install off without a hitch (sort of).  

I modified the repositories per this page:
[http://www.spic.net/zoneminder/](http://www.spic.net/zoneminder/)
and ran Synaptic and searched and found a "zm" package.  Coolbeans...  However, it depends on libcodec2, and couldn't be installed.  So, I installed  that by going here for useful info:
[http://www.ubuntuforums.org/showthread.php?t=17356](http://www.ubuntuforums.org/showthread.php?t=17356)
and I followed kokotero's instructions:
[I]I found an libavcodec2 package for ubuntu googleing at this address:
[http://search.belnet.be/packages/ubu...erse/f/ffmpeg/](http://search.belnet.be/packages/ubu...erse/f/ffmpeg/)

You may require to fill some dependencies, in my case i executed:
$ sudo apt-get install libfaad2-0 libimlib2 liblame0 libungif4g

Install libavcodec2 (after downloading it). I get the one for x86, install what best fits your architecture:
sudo dpkg -i libavcodec2_0.4.9-pre1-0.2_i386.d[/I]eb

I did download the package, but running the first set of commands (above from kokotero) said that libcodec2 installed, so I didn't have to run the downloaded package...  Hey, as long as it works.  :)

Anyway, then I was able to do the "sudo apt-get install zm" command and it downloaded & installed just fine.  The services started without error at the end.  However, nothing happens in the web browser (as  previously mentioned), just a page not found (or something like that).  I rebooted (a Windows throwback manuver...), and still nothing.  By Googling around, I found that to start zoneminder, I need to issue: "zmpkg.pl start"  but I'm still back to the start, nothing...

I assume I have to run a configuration script, but what do I need to run? Any help would be awesome.  I'm running an OLD Zoneminder LiveCD installation on another box and I want to throw Ubuntu on it and then zoneminder (and then forget about it.)  8) So, I'm testing it on my main box first.

---

### Post by mrezmu on 2006-07-30
My first post to any forum ever.
Thanks to all who have contibuted to ubuntu, zoneminder and related forums.I have been using ubuntu about four months I've tried several distro's in that time. Ubuntu was the one that seemed to have the most stuff working on install. I'm sorry I can't be much help here but...
I have ubuntu updated to 6.06 running on two machines one amd 64 and one x86 with ati video cards. Zoneminder 1.21.3 on the x86 runs ok but I don't know how to get around in linux and I can't say exactly how I got it all working except that I had to read almost every result from google seaching zoneminder +ubuntu and zoneminder +debian and mostly following the debian
instuctions(and I didn't understand a thing just copy and paste).The zoneminder I used is a debian package posted in a forum. So anyone trying to get zoneminder on ubuntu it can be done. I am a NOOB and would like to stay one so switched from xp to ubuntu now I'm being called a geek cause I can do in ubuntu what I couldn't in xp.I run a recording studio and if firewire audio would work with the firepod and I could get my access data base working I could quit windoz. Now I'm trying to figure out how to upgrade zoneminder
but I'm finding nothing.I don't know what info I could post to help others but I'll try and watch for requests, unfortunately I don't read these forums religiously. Zoneminder works great but seeing the guy break in to your friends car when you're not there
doesn't stop him, evan with signs and visible cams. 
Thank to everyone involved in open sourse.
Cheers for the end of microsoft.

---

### Post by BrownieMan on 2007-01-26
This threat might be helpful to you:

[http://www.ubuntuforums.org/showthread.php?t=234135&highlight=zoneminder]("http://www.ubuntuforums.org/showthread.php?t=234135&highlight=zoneminder")

---

