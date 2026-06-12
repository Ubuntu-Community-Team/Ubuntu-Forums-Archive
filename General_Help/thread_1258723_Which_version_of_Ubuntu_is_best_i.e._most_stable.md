---
title: "Which version of Ubuntu is best? i.e. most stable?"
date: 2009-09-05
forum: General Help
---

### Post by jukingeo on 2009-09-05
Hello all,

As the title says I am looking for the overall best version of Ubuntu that is the most stable.  To put things in perspective, I want to use Ubuntu for audio and video editing work.  I have Ubuntu Studio version 8.04 (Hardy) currently.  I had my fair share of troubles setting it up.  While it runs fine on my system, I am looking to set up a video/audio editing system on an older Pentium 3 (prior Windows 98) systems.  Most of these computers are around a 1 ghz processor and about 1 gig ram.

My current machine that I use for testing is a Dell Dimension 4600 with a 2.8ghz processor and 2 gig ram.

The programs I intend to use are: Ardour, Mixxx, Blender, VLC, OpenShot, Cinelerra (occasionally).

USB support should be good for both audio and memory stick usage.

The candidates are:

Ubuntu (currently using), Kubuntu, Xubuntu, Icebuntu (Spri), and Lubuntu

The versions are all of the above on these versions:

6.10, 7.10, 8.04 (currently using), 8.10, 9.04

I am looking for which combination of type/version is the most stable for the task mentioned above. (Yes, I am aware that Icebuntu and Lubuntu are new and the earlier version numbers do not apply).

Thank You,

Geo

---

### Post by DJonsson2008 on 2009-09-05
One factor is what video card you have, as some 8.4 users 
(including myself) are not having fun with problems with
Nvidia and other brand name cards. As well I'm told 
newer versions work better with Intel chipsets.

---

### Post by Liolikas on 2009-09-05
Xubuntu 8.04 **LTS** is not resource hungry as ubuntu and most stable from Ubuntu line.

---

### Post by snowpine on 2009-09-05
8.04 is the "long term support" release and the most stable. I personally like to use a lightweight windows manager (like Fluxbox or Openbox) when I'm doing AV editing.

No version is "the best". :)

---

### Post by NoaHall on 2009-09-05
I'd use Lubuntu 9.04 - if you're going to do RAM extensive stuff .

---

### Post by CatKiller on 2009-09-05
> **jukingeo said:**
> I am looking to set up a video/audio editing system on an older Pentium 3 (prior Windows 98) systems.  Most of these computers are around a 1 ghz processor and about 1 gig ram.

If you're going to do workstation things, you need workstation-class hardware. If you're just editing a WAV file now and then, then fair enough, but multi-track audio work is not going to be fun on those machines. It's the same for video editing work.

LXDE is a nice lightweight desktop environment, but you don't have to only pick one. I log into LXDE when I'm doing audio work and use Gnome the rest of the time. You can install different desktop environments through Synaptic, the same as any other application. You just choose which one you want to use for a session from the login screen. All the Ubuntu Studio applications are in there too.

You might need to do a similar shuffle with the kernel that you use. Ubuntu Studio uses the (experimental) realtime kernel for low latencies. Proprietary drivers won't necessarily work with the realtime kernel, which means that Blender won't necessarily work that well either. You can install both the realtime and generic kernels though, and select which one you boot with from the GRUB menu. Or you might just find that the generic kernel offers sufficiently low latencies to be able to use that all the time.

If you're planning to do serious work on a machine, then it's worth investing in getting a machine that's up to the task. If you're being paid for the work that you do, the investment will pay for itself in no time. If you aren't being paid, it will still pay off in productivity gains and end results. I haven't done much video work, but for audio you're looking at a decent sound card and decent monitors as essential, and plenty of RAM and fast reliable storage as being things that will make life significantly easier for you. Your choice of desktop environment is really secondary to having a machine that's good enough.

None of the releases are more stable than the others in the sense that you mean. Stability is used in its software development sense; programs do not significantly change over time. Crashes and freezes - stability as you mean it - are bugs to be fixed, even if you're using Alpha or Testing software. 8.04 is a Long-Term Support release, meaning that you'll get security updates and bugfixes for three years. The others aren't, meaning that you'll get security updates and bugfixes for18 months. In either case, you won't get new features until you upgrade to the next release. In the software development sense, 8.04 is more stable than the others because it won't change for twice as long. Which one is best depends entirely on which one does what you want it to. There is no one-size-fits-all answer.

Good luck!

---

### Post by jukingeo on 2009-09-05
> **DJonsson2008 said:**
> One factor is what video card you have, as some 8.4 users 
(including myself) are not having fun with problems with
Nvidia and other brand name cards. As well I'm told 
newer versions work better with Intel chipsets.

Quite right...foolish of me not to include that info. Thanx for the heads up.

I have an ATI 9600XT with 256meg ram.  It was the largest card I can fit on my machine without going to a larger power supply.

However the trick is that I would be using machines that have much less power.  Most of my other machines have cards on par with the Nvidia GeForce 5200FX.

Geo

---

### Post by 3rdalbum on 2009-09-05
Use the latest version unless the release notes tell you not to, or you want a "no-unexpected-changes" system (Ubuntu 8.04 LTS).

8.04 is mature, but it's rather behind-the-times, especially for mobile broadband support.

---

### Post by jukingeo on 2009-09-05
> **CatKiller said:**
> If you're going to do workstation things, you need workstation-class hardware. If you're just editing a WAV file now and then, then fair enough, but multi-track audio work is not going to be fun on those machines. It's the same for video editing work.

I will say that overall I would like to do a bit more than the average editing.

For now, I would like to be able to take pictures and video clips of my twin boys (2.5years old now) and put together a video of them growing up.  It is at that level of complexity.

The presentations I am referring to would mostly use VLC and grab a bunch of 'preset' edited files to create a 'show'.

The reason I wanted to use ardour is in the event I would like to mix tracks, make songs longer, make them shorter (with clean mix points).  For now I don't need the full power that Cinelerra offers.

> LXDE is a nice lightweight desktop environment, but you don't have to only pick one. I log into LXDE when I'm doing audio work and use Gnome the rest of the time.

Yes, understood.  I still want to use a desktop based on Ubuntu Studio because that is where I do most of my work from.  However, it is far from lightwight and trouble free and that is what I am looking for on a presentation computer.

>  You can install different desktop environments through Synaptic, the same as any other application. You just choose which one you want to use for a session from the login screen. All the Ubuntu Studio applications are in there too.

So that means I can choose to use KDE or LXDE with my existing Ubuntu Studio (8.04) installation?

> 
You might need to do a similar shuffle with the kernel that you use. Ubuntu Studio uses the (experimental) realtime kernel for low latencies. Proprietary drivers won't necessarily work with the realtime kernel, which means that Blender won't necessarily work that well either. You can install both the realtime and generic kernels though, and select which one you boot with from the GRUB menu. Or you might just find that the generic kernel offers sufficiently low latencies to be able to use that all the time.

Yes, I know that the realtime kernel is experimental and not proven as stable.  I personally don't know why it is taking so long to get Ubuntu Studio's realtime kernel 'right'.  I have had trouble with it.  I have run Ubuntu Studio on a non-realtime kernel and it is more stable, but I do get problems with X-runs when using Jack.  It is really kind of a catch 22.  You have better stability using the regular kernel but can't use some programs because of x-runs.  With the realtime kernel, you don't have the x-runs, but you have trouble getting programs to cooperate with each other.  So all in all Ubuntu Studio is a useless crash-fest if you ask me.  That is why I want to use a lighter weight version of Ubuntu and use a more stable kernel in the hopes that I can improve system stability.

> If you're planning to do serious work on a machine, then it's worth investing in getting a machine that's up to the task. If you're being paid for the work that you do, the investment will pay for itself in no time. If you aren't being paid, it will still pay off in productivity gains and end results. I haven't done much video work, but for audio you're looking at a decent sound card and decent monitors as essential, and plenty of RAM and fast reliable storage as being things that will make life significantly easier for you. Your choice of desktop environment is really secondary to having a machine that's good enough.

Eventually I will look into a better machine.  For now I am doing mostly personal work.  I am also very strapped with cash so I have to make do with older machines.

> 
None of the releases are more stable than the others in the sense that you mean. Stability is used in its software development sense; programs do not significantly change over time. Crashes and freezes - stability as you mean it - are bugs to be fixed, even if you're using Alpha or Testing software. 8.04 is a Long-Term Support release, meaning that you'll get security updates and bugfixes for three years. The others aren't, meaning that you'll get security updates and bugfixes for18 months. In either case, you won't get new features until you upgrade to the next release. In the software development sense, 8.04 is more stable than the others because it won't change for twice as long. Which one is best depends entirely on which one does what you want it to. There is no one-size-fits-all answer.

Good luck!

I didn't think there would be a one size fits all answer, but a push in the right direction is good enough.  It seems like from what you (and others here) are saying, I should stick with version 8.04.

I been leaning towards Lubuntu as well, but thusfar I don't think they have a full install release ready as of yet.  So I have to do a bit more waiting.

Thanx for the info 

Geo

---

### Post by CatKiller on 2009-09-06
> **jukingeo said:**
>  For now, I would like to be able to take pictures and video clips of my twin boys (2.5years old now) and put together a video of them growing up.  It is at that level of complexity.

The presentations I am referring to would mostly use VLC and grab a bunch of 'preset' edited files to create a 'show'.

The reason I wanted to use ardour is in the event I would like to mix tracks, make songs longer, make them shorter (with clean mix points).  For now I don't need the full power that Cinelerra offers.

Those machines should be OK then. 

Audacity is lighter than Ardour, although it doesn't quite do as much - you can't AFAIK use MIDI, for example. You may find that that is sufficient for what you need to do to prepare your soundtracks. It looks a bit clunky, but it is powerful.

> 
So that means I can choose to use KDE or LXDE with my existing Ubuntu Studio (8.04) installation?

Yep. Or Ubuntu Studio from a standard Ubuntu install. It's all in the repositories.

> 
 I have run Ubuntu Studio on a non-realtime kernel and it is more stable, but I do get problems with X-runs when using Jack. 

You can get near realtime performance with the generic kernel. You can also increase the Frames/Period and Periods/Buffer values in JACK to lower the amount of xruns that you get. It increases the latency, but unless you're planning on recording yourself playing along, latency doesn't really matter that much. And even then it's only a pain since you then have to nudge the recording to compensate.

> 
I been leaning towards Lubuntu as well, but thusfar I don't think they have a full install release ready as of yet.  So I have to do a bit more waiting.

That doesn't matter. ```
sudo apt-get install lxde
```will install all you need to use LXDE on your existing Ubuntu setup. Then you just log out and pick an LXDE session from the login screen. You can still use applications from one environment in another environment.

---

### Post by jukingeo on 2009-09-06
> **CatKiller said:**
> Those machines should be OK then. 

Audacity is lighter than Ardour, although it doesn't quite do as much - you can't AFAIK use MIDI, for example. You may find that that is sufficient for what you need to do to prepare your soundtracks. It looks a bit clunky, but it is powerful.

Different programs.  Audacity is an editor while Ardour is a mult-track mixer/workstation.  Ardour can't do midi either...for that there is Rose Garden.

> 

Yep. Or Ubuntu Studio from a standard Ubuntu install. It's all in the repositories.

I have Ubuntu Studio already.  I did try it out with XFCE this afternoon and Ubuntu DOES use less resources with that gui interface than with Gnome.

Which interface uses more resources, KDE or Gnome?

> 
You can get near realtime performance with the generic kernel. You can also increase the Frames/Period and Periods/Buffer values in JACK to lower the amount of xruns that you get. It increases the latency, but unless you're planning on recording yourself playing along, latency doesn't really matter that much. And even then it's only a pain since you then have to nudge the recording to compensate.

Latency is a pain for me because I wanted a program like Ableton's Live.  I would like real time midi control using an external controller.  So it is kind of a pain in the neck if you have latency.  Also with high lantency comes a lag in VU meters and such.  NOT GOOD!


> 
That doesn't matter. ```
sudo apt-get install lxde
```will install all you need to use LXDE on your existing Ubuntu setup. Then you just log out and pick an LXDE session from the login screen. You can still use applications from one environment in another environment.

GREAT!!  Thanx for the tip off...I will try that out and see what Lxde is like.

This is another thumbs up from me in regards to Ubuntu...you can change the entire gui interface and still keep your programs intact.

I am assuming I can do this with KDE too, right?  If so, then I can do a "top" command in the terminal and compare the resource consumption of each interface.

Edit:

Uh Oh!  Loading LXDE no worky.  This is what happened in my terminal:

geo@home:~$ sudo apt-get install lxde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lxde
geo@home:~$ 

Any idea to what is going wrong?

Thanx Again,

Geo

---

### Post by CatKiller on 2009-09-07
> **jukingeo said:**
> Different programs.  Audacity is an editor while Ardour is a mult-track mixer/workstation.  Ardour can't do midi either...for that there is Rose Garden.

You're right, of course. Confused myself there. Audacity isn't *just* an editor though. It's perfectly capable of doing multi-track stuff - at least to the level that you're using it for; it's not like you're using 96 channels on those computers - you just want to prepare your soundtrack, don't you?

Personally, I only use the computer for processing; I'm a tactile person when it comes to mixing.

> 
Uh Oh!  Loading LXDE no worky.  This is what happened in my terminal:

geo@home:~$ sudo apt-get install lxde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lxde
geo@home:~$ 

Any idea to what is going wrong?

My mistake again; I thought LXDE was in the Hardy repositories, but it's only in the Intrepid and Jaunty ones. You could install Jaunty on one of your lower specced machines and see how LXDE fares there; Pulse Audio support is better in Jaunty than Hardy.

---

### Post by longtom on 2009-09-07
to get lxde in Hardy:

[http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

and for good measure:

[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

---

### Post by jukingeo on 2009-09-07
> **CatKiller said:**
> You're right, of course. Confused myself there. Audacity isn't *just* an editor though. It's perfectly capable of doing multi-track stuff - at least to the level that you're using it for; it's not like you're using 96 channels on those computers - you just want to prepare your soundtrack, don't you?

No, I wasn't aware that Audacity now does multi-track work.  Most of the mixing work I will be doing would be between 3 stereo channels and that does include video and DJ mixing work.  I seriously doubt I would be doing anything with more than 3 stereo channels.  However, coming from an audio background, I sure do want to do some multi-track recording.  That is my desire, but not my need.

Right now, something that mixes up to 3 stereo channels would be fine and if Audacity can do that then it would simplify my setup.

Overall I am looking right now to add mixed audio for video work.  I have TONS of video camera footage that is in the raw right now and I HAVE to do SOMETHING with it.  Also I am working on a movie presentations as well.  Mostly VLC will be the program of choice there, but I will have to do video and audio editing as well.  VLC is just a 'player'.

> Personally, I only use the computer for processing; I'm a tactile person when it comes to mixing.

I am both.  I want to use a computer for processing AND I want to be tactile.  I do want a physical midi controller.  I don't know how controllable Audacity is via MIDI, but I know that in Ardour you can map everything to a controller...hence one reason why I am leaning towards it.  Most of my "DJ Style" mixes will be handled by a program called Mixxx.

> 
My mistake again; I thought LXDE was in the Hardy repositories, but it's only in the Intrepid and Jaunty ones. You could install Jaunty on one of your lower specced machines and see how LXDE fares there; Pulse Audio support is better in Jaunty than Hardy.

So then I can't install LXDE in Hardy?

> **longtom said:**
> to get lxde in Hardy:

[http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

and for good measure:

[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

Oh!  Ok, I guess I will check that out then :).

EDIT:

Ok, the info on that site worked. It loaded up onto my system now.  I just have to log out and check it out!

Thanx for the info guys!

Geo

---

### Post by jukingeo on 2009-09-08
> **NoaHall said:**
> I'd use Lubuntu 9.04 - if you're going to do RAM extensive stuff .

Not that I know of.  My concerns are the CPU usage which sometimes goes through the roof on certain applications.

Geo

---

