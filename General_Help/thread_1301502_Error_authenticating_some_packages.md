---
title: "Error authenticating some packages"
date: 2009-10-26
forum: General Help
---

### Post by alunparry on 2009-10-26
Hi

I am having a problem with update manager in Ubuntu 9.04. 

It now tells me that it can only attempt a partial update. 

Yet when it tries it says "Error authenticating some packages."

It then lists the unauthenticated packages as follows:

ffmpeg
libavcodec-unstripped-52
libavdevice-unstripped-52
libavfilter-unstripped-0
libavformat-unstripped-52
libavutil-unstripped-50
libpostproc-unstripped-51
libswscale-unstripped-0
libx264-76

Can anyone help get my system back to the point where it was happily updating.

One additional bit of information is that this only happened when I installed the OpenShot Video Editor ([http://www.openshotvideo.com/](http://www.openshotvideo.com/))

I installed using the deb instructions.

I have since removed the OpenShot package via Synaptic Package Manager but the problems above remain.

Please can you help?

Grateful in advance.

Al

---

### Post by phillw on 2009-10-26
Hi,

there's a great thread on the matter here ....

[http://ubuntuforums.org/showthread.php?t=812008&page=10](http://ubuntuforums.org/showthread.php?t=812008&page=10)

Don't let it blow your mind-up, take your time & follow the recommendations. It does cover various things happening !!!

Regards,

Phill.

---

### Post by alunparry on 2009-10-26
hi phill

thanks for that.

the thread goes on for 10 pages there and I'm a newbie at this relatively so it's a bit scary for me.

can you point out the particular post which is the one that you'd recommend following

thanks very much

al

---

### Post by phillw on 2009-10-26
1st off, try marking the affected items for re-installation using synaptic package manager.

Let me know what it says & I'll try to mirror it on my system for you.

Phill.

---

### Post by alunparry on 2009-10-26
Thanks Phill

Just went to do that and started with ffmpeg.

The right click menu brings up the following options:

Unmark
Mark For Installation
Mark For ReInstallation
Mark For Upgrade
Mark For Removal
Mark For Complete Removal

Unfortunately though, installation and reinstallation are greyed out so I've gone and fell at the first hurdle. Doh! :-)

What would you advise?

Thanks again

Al

---

### Post by alunparry on 2009-10-26
Oh, also, there's a little star in the box in the S column for the ffmpeg package. So its not just coloured in, but has a little gold star on the top right.

---

### Post by alunparry on 2009-10-26
More info: oddly enough the checkbox for libavdevice-unstripped-52 isn't coloured in at all.

---

### Post by phillw on 2009-10-26
okies - the ones you are refering to are the 'extended' versions of the ones that ubuntu uses by dafault.

e.g.

libadevice52    is a ubuntu instal (has the ubuntu symbol next to it)
libadevice-unstripped-52 is the unrestricted version.

As both are on the same release code - I'd stick with the ubuntu version.

Phill.

---

### Post by alunparry on 2009-10-26
Ok. Why is ubuntu trying to update things which aren't installed. Sorry if that's a dim question.

Am starting to struggle :-/

Shall I do a complete removal of ffmpeg and then reinstall it?

---

### Post by phillw on 2009-10-26
> **alunparry said:**
> Ok. Why is ubuntu trying to update things which aren't installed. Sorry if that's a dim question.

Am starting to struggle :-/

Shall I do a complete removal of ffmpeg and then reinstall it?


Don't worry.

Leave it with me a few minutes - let me go and have a 'play' with what you were trying to install :P

Phill.

---

### Post by alunparry on 2009-10-26
Thanks Phill. Really appreciate you taking the time to help me out.

Al

---

### Post by phillw on 2009-10-26
Head over to this link & follow the instructions there ...

[http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/](http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/)

howtogeek is a good resource & I trust their instructions. :)

I'll keep an eye on this thread, so post back how u get on.

Phill.

---

### Post by alunparry on 2009-10-26
Hi Phill

I can't see any info there on this issue, only how to install the program and then how to use it. Have I missed something really obvious.

I'm still puzzled why Synaptic Package Manager would be attempting to authenticate a package that is not installed eg libavdevice-unstripped-52

Al

---

### Post by phillw on 2009-10-26
I *think* synaptic may have gotten confused. Try fully installing it & see if the error goes away - My only thought is that you 'used' to need extra files to compile the package with - You don't now.

Once you get it running, we can see if synaptic is still complaining.

Phill.

---

### Post by alunparry on 2009-10-26
Ah ok, so if I try to install all the things that it says it's having a problem with and see if it goes away

---

### Post by alunparry on 2009-10-26
Actually, could this be a different ffmpeg that openshot uses? Is that a daft question?

The PPA instructions (which I tried at first when installing but shifted to deb when nothing seemed to have happened) says this:

WARNING: Our PPA uses a special version of FFmpeg, which does not work with VLC & Totem, and a few other movie players. This is due to how we are packaging FFmpeg in our PPA. We are working to fix this, but if you install via the PPA, you will not be able to run VLC at this time. 

See [http://www.openshotvideo.com/2008/04/ppa-instructions.html](http://www.openshotvideo.com/2008/04/ppa-instructions.html)

Also ffmpeg in Synaptic does not have the ubuntu logo next to it.

If this is the case, shall I completely remove it. 

Then how do I get the original (non special) version back again?

Al

---

### Post by phillw on 2009-10-26
Yeah,

That's my reasoning (and hope - lol)

Phill.

---

### Post by alunparry on 2009-10-26
I did something else instead.

I went to System/Software Sources

Then chose third party sources tab.

Then I clicked each of the openshot ppa lines and clicked remove.

Then I went to the update manager.

Its now updating as we speak 15 new updates, and hasn't said anything now about partial upgrades.

Hopefully what it's doing now has no nasty side effects :-/

But I think it looks like it was only attempting to update these other packages because I had them listed in the Third Party Sources.

Now I've removed them, it is updating without the previous messages.

Once it's updated I'll let you know if the update has done anything nasty to my machine or not :-/

Fingers crossed!!

---

### Post by phillw on 2009-10-26
It's pretty hard to 'break' your installation via synaptics - unless you do something like deleting the linux kernel that you're using !!!

:)

Phill.

---

### Post by alunparry on 2009-10-26
Woohoo!!

The update demanded a restart.

I did as I was told (I'm very obedient).

It restarted.

Then I checked Synaptics Package Manager.

FFMPEG was there, with its Ubuntu logo happily back to show that this is the right version of FFMPEG again.

Thanks loads Phill.

I really couldn't have got to that conclusion without your help.

Plus now I know what the ubuntu icon in synaptic means :-)

Thanks again Phill.

Am really grateful and all is running nicely again now.

Al :)

---

### Post by phillw on 2009-10-26
You're welecome - hopefully, you can go add the package via the link I posted.

Have fun with ubuntu.

Phill.

---

