---
title: "Best way to &quot;clean&quot; or restore a Ubuntu installation ?"
date: 2010-09-22
forum: General Help
---

### Post by kimangroo on 2010-09-22
Basically I've been having on and off (mainly on) problems with streaming video on Ubuntu ever since installation. Right now I can watch pretty much all streams I come across but can't stream or pause them.

After much fiddling about and adding and removing of plugins I did get it to work at one point, only for it to stop working again a little later (I don't remember adding any new programs in the meantime). By this time I had run out of energy to do anything about it and so either watch streams in one go from the beginning to the end or just don't.

Well it's beginning to **** me off mightly again, and it's just embarassing to be using a computer where I can't do such a basic task, so I've decided to have another ago at fixing it. I've come across a number of unresolved threads of people with the same problems and from my experience of asking for help it seems there isn't an obvious answer and it's just some kind of crappy conflict (that really shouldn't exist) and the only approach is trial and error which in my case has often seemed to introduce two new problems for every one solved.

Simplest method seems to be to try and start from the beginning again, but I'd rather not have to completely reinstall Ubuntu. So my question is: is there any way I can see what packages I have installed (that didn't come with the installation) so I can remove them bit by bit to try and solve the problem?

Thanks.

---

### Post by utnubuuser on 2010-09-22
You can check installed packages right through Synaptic by using the filters - installed packages.

Usually installing > sudo apt-get install ubuntu-restricted-extrasfrom a terminal, will pull in most if not all the codec required for videos etc.

If you've done that already, chances are it's something other than codec.

As to "how to clean" an install...

If you've installed with a separate /home partition, you can re-install the entire OS while retaining your data, settings, etc. by selecting to manually partition during installation, and choosing not to format your /home partition.

Link to seperate /home partition how-to: [http://sazeit.com/articles/manually-select-partitions-ubuntu]("http://sazeit.com/articles/manually-select-partitions-ubuntu")

and a link to "adding a seperate /home partition after installation" (not sure if this is for Lucid+ or not": [http://ubuntuforums.org/showthread.php?t=1457542]("http://ubuntuforums.org/showthread.php?t=1457542")

---

### Post by sikander3786 on 2010-09-22
Which streams are you unable to pause? Which media player are you using to view them? You are not talking about flash videos and flash player I believe.

---

### Post by kimangroo on 2010-09-22
Thanks for the replies.

I'll go through synaptic and start removing packages that look streaming related and then reinstall if that doesn't work.

An example of a stream I can't seek or pause can be found here:
[http://www.thalassa.france3.fr/?page=archives&play=yes&id=196](http://www.thalassa.france3.fr/?page=archives&play=yes&id=196)

The direct link to the stream is:
rtsp://a988.v101995.c10199.e.vm.akamaistream.net/7/988/10199/3f97c7e6/ftvigrp.download.akamai.com/10199/cappuccino/production/publication/geoloc/france-dom-tom/Autre/Autre/2010/S37/J6/165011_thalassa_integrale_170910.wmv 

I'm using firefox with the totem plugin. But when I use Vlc and the direct link, I can' pause or seek either. (works fine on XP)

Thing is since I installed ubuntu depending on the packages I installed, sometimes some streams would play, sometimes others, it's been very difficult to specify exactly what isn't working.

---

### Post by kimangroo on 2010-09-25
Update for those who might have similar problems in the future:

I messed about a bit removing and reinstalling a number of codec related packages, trying different combinations to see what errors/problems it gave.

No luck with viewing streams within the totem plugin, it either wouldn't pause/seek, or didn't have the right codec.

However removing the gstreamer bad package which contained the libmms stuff to deal with mms streams, so far has seemed to resolve the problem with watching the streams in Vlc. Before, vlc would stutter constantly when viewing the mms streams and would also have problems with seeking (though not as bad as totem).

So now I'm back to the state I was 6 months or so ago where I load up the page, tell totem not to look for a plugin, and then select view in vlc option to watch the stream.

Last time I got to this stage I remember trying to use the vlc plugin direct in firefox only to find that for some reason it didn't even have a control bar with pause and seek options.

Hopefully this shabby workaround will hold up.

---

### Post by dcstar on 2010-09-25
> **kimangroo said:**
> 
.........
Simplest method seems to be to try and start from the beginning again, but I'd rather not have to completely reinstall Ubuntu. So my question is: is there any way I can see what packages I have installed (that didn't come with the installation) so I can remove them bit by bit to try and solve the problem?


Firstly create a new User account and see if that also has the same problems. If it does not then you know that the issue is just with the configuration of your original account.

---

### Post by ron999 on 2010-09-25
Hi
Those videos play OK for me with Firefox using **gecko-mediaplayer** plugin.
I can pause, but not seek.

When they are playing, I can right-click and 'Copy location'.
Then with VLC it's Media > 'Open location from clipboard'.
Using VLC allows both pause and seek.

Maybe gecko-mediaplayer is the best plugin to use for this type of website.

---

