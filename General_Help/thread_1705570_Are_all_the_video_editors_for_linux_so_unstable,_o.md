---
title: "Are all the video editors for linux so unstable, or is it my pc?"
date: 2011-03-12
forum: General Help
---

### Post by colobix on 2011-03-12
Hey. I want to use linux instead of windows to create my videos, but all the video editors are so unstable that they are not possible to use at all.
At first I Thought it was my hardware or something but I tried on my laptop as well. They all crash randomly every time I try to do stuff.
I have tried OpenShot, VLMC, Pitivi, OpenMovieEditor, Avidemux, Kino, LiVES, Cinelerra and Kdenlive.
How come I never have problems like this in windows?
I know Linux sometimes sucks when it comes to brand new hardware, but seriously though. All the video editors are crashy.

This is soo frustrating, so please help me.
Thanks in advance.

---

### Post by andrewthomas on 2011-03-12
I use avidemux all the time and it has never crashed once.  

System specs, ubuntu version?

---

### Post by colobix on 2011-03-13
Ubuntu 10.10 AMD 64
Memory: recognizes 2.9 gb of 4.0 gb.
Kernel: 2.6.35.27
Processor (2): Intel Atom 230 1.60ghz
And I have a Nvidia Core graphics card. I don't know what model.

---

### Post by colobix on 2011-03-14
bump

---

### Post by 3Miro on 2011-03-14
Why is your system recognizing only 2.9GB of RAM. Check the BIOS settings for memory address remapping, there is no need for you to not be able to see all the RAM.

I have been using Avidemux myself and I find it very stable. To try and figure out the problem, you should run it form the terminal, Apps -> Access -> Terminal, the command is
```
avidemux2_gtk
```

Use it and wait fro it to crash, then you should see an error message. Post the error message here.

---

### Post by SeijiSensei on 2011-03-14
> **3Miro said:**
> Why is your system recognizing only 2.9GB of RAM. Check the BIOS settings for memory address remapping, there is no need for you to not be able to see all the RAM.

He's not running a 64-bit or -pae kernel.

---

### Post by 3Miro on 2011-03-14
> **SeijiSensei said:**
> He's not running a 64-bit or -pae kernel.

He said he is:

[QUOTE=colobix]Ubuntu 10.10 AMD 64[/QUOTE]

---

### Post by colobix on 2011-03-14
> **3Miro said:**
> He said he is:
Yes I use 64 bit, but I don't think that has anything to do with this though.
@3Miro, I don't consider avidemux a video editing software since all I can do with it is copy, cut and convert. But no bugs there so far. 
I tried Cinelerra, and here's the error I got from the terminal

signal_entry: got SIGSEGV my pid=3590 execution table size=16:
    mwindow.C: create_objects: 1338
    mwindow.C: create_objects: 1347
    mwindow.C: create_objects: 1353
    mwindow.C: create_objects: 1357
    mwindow.C: create_objects: 1359
    mwindow.C: create_objects: 1361
    mwindow.C: create_objects: 1363
    mwindow.C: create_objects: 1365
    tipwindow.C: create_objects: 152
    tipwindow.C: create_objects: 155
    tipwindow.C: create_objects: 158
    tipwindow.C: create_objects: 163
    tipwindow.C: create_objects: 166
    tipwindow.C: create_objects: 169
    mwindow.C: create_objects: 1372
    mwindow.C: create_objects: 1375
signal_entry: lock table size=14
    0x3a72210 CWindowTool::input_lock CWindowTool::run 
    0x3a97590 TransportQue::output_lock PlaybackEngine::run 
    0x3b60c40 TransportQue::output_lock PlaybackEngine::run 
    0x3b616a0 MainIndexes::input_lock MainIndexes::run 1 
    0x3be6460 ResourceThread::draw_lock ResourceThread::run 
    0x2a3ebd0 BC_Synchronous::next_command BC_Synchronous::run 
    0x3c204a0 BC_Repeater::pause_lock BC_Repeater::run 
    0x3cae820 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x387c550 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3c21e30 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x39bda90 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3a98f80 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3ac7b40 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3b63910 BC_WindowBase::event_condition BC_WindowBase::get_event 
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=0
interrupted (SIGABRT)

---

### Post by 3Miro on 2011-03-14
> **colobix said:**
> 
@3Miro, I don't consider avidemux a video editing software since all I can do with it is copy, cut and convert. But no bugs there so far. 
I tried Cinelerra, and here's the error I got from the terminal


Avidemux is the only one that I have used. In your initial post, you listed the issue not as "there are no video editors with enough features", but rather, "all video editors are unstable". This is not a problem inherit to the video editing software since many of us can use those programs just fine, the issue is with your settings/drivers/hardware, and we need more information to help.

What you have posted is not a result of a crash, you need to start any editor from the terminal and then use it until it crashes. After it crashes, you can post the error here.

---

### Post by colobix on 2011-03-14
> **3Miro said:**
> 
What you have posted is not a result of a crash, you need to start any editor from the terminal and then use it until it crashes. After it crashes, you can post the error here.
That's what I did. this message came up in the terminal when it crashed, not before it crashed or during the startup.

---

### Post by junapp on 2011-03-14
not sure what type of editing you are doing, but you may want to look into blender.

Example of a video with edited with Blender. Blender has a steep learning curve, but look around for some video tutorials, and the basics come pretty quickly. Video toward the bottom of:

[http://troy-sobotka.blogspot.com/2009/02/right-where-it-belongs.html](http://troy-sobotka.blogspot.com/2009/02/right-where-it-belongs.html)

---

### Post by colobix on 2011-03-16
Thanks but blender is more for presentation and text effects and such. I use the effects in VLMC, OpenShot and Curella.
I make Youtube Poops is you know what that is.
So I have to use a lot of effects and video clips.
I don't understand why this is such a huge problem for me in linux, when it windows everything work just fine.
The last time I used openshot and it crashed, the terminal said something about memory error. I don't remember the message but it sounds very odd.
Windows is installed on the same pc btw.
EDIT: I should also mention that HD videos can be very jerky sometimes.
But again, not in windows. ANy idea?

---

### Post by colobix on 2011-03-17
bump

---

### Post by colobix on 2011-03-20
bump

---

### Post by colobix on 2011-03-21
**bump**

---

### Post by Grenage on 2011-03-21
Have you run a memcheck?  Video editing generally uses a lot of source data, which will be stored in memory where possible.

It can't hurt to rule it out.

---

### Post by colobix on 2011-03-22
I ran the memcheck from grub. It gave me no errors.
But I'm starting to think this is a hardware problem, as I said in my first post. So if that's the case, what PC should I buy instead?
I don't wanna have any more crashes or freezing problems, and especially when I'm doing video editing.
And where can I see if hardware is the problem here?
If I need a new pc, then money is not a problem. I just want the best and most powerful 64bit PC out there.

---

### Post by Grenage on 2011-03-22
> **colobix said:**
> I ran the memcheck from grub. It gave me no errors.
But I'm starting to think this is a hardware problem, as I said in my first post. So if that's the case, what PC should I buy instead?
I don't wanna have any more crashes or freezing problems, and especially when I'm doing video editing.
And where can I see if hardware is the problem here?
If I need a new pc, then money is not a problem. I just want the best and most powerful 64bit PC out there.

Have you tried a fresh install?  It always seems like a bit of a 'cop out', but if the machine is crashing with every video editor, it will at least rule out the install before you shell out a fortune on a new PC.

---

### Post by colobix on 2011-03-22
> **Grenage said:**
> Have you tried a fresh install?  It always seems like a bit of a 'cop out', but if the machine is crashing with every video editor, it will at least rule out the install before you shell out a fortune on a new PC.
Yea, like a million times.

---

### Post by Grenage on 2011-03-22
> **colobix said:**
> Yea, like a million times.

Probably excessive, but I think we can be sure after that many.  Are you using the restricted drivers (listed under *additional drivers*)?

Is this a netbook/laptop?

---

### Post by coldraven on 2011-03-22
Try cleaning out the fluff and dust from your PC, it could just be overheating.
```
sensors
```
Will show how hot you're getting.

---

### Post by kaizokuroof on 2011-03-22
I have found most of the Video Editors I've tried on Linux to be quite unstable, almost unusable. If you are doing this for "Youtube Poops" I suggest you reinstall windows, as I've had no luck with the editing software.

I found "Kdenlive" to be most stable - Used it for a school project. Although it is a KDE app, it will run on a gnome session without a hitch (may take a little longer to load.)

Anyways good luck. K.R

---

### Post by colobix on 2011-03-23
> **Grenage said:**
> Probably excessive, but I think we can be sure after that many.  Are you using the restricted drivers (listed under *additional drivers*)?

Is this a netbook/laptop?
Yes, I use "current driver (recommended)"
It's a Desktop.


> **kaizokuroof said:**
> I have found most of the Video Editors I've tried on Linux to be quite unstable, almost unusable. If you are doing this for "Youtube Poops" I suggest you reinstall windows, as I've had no luck with the editing software.

I found "Kdenlive" to be most stable - Used it for a school project. Although it is a KDE app, it will run on a gnome session without a hitch (may take a little longer to load.)

Anyways good luck. K.R

Pretty much the same as what I have to deal with.
Also, I don't like kdenlive. It's not much of an editor, but more like basic stuff such as paste/cut and convert.

But guys, please tell me if this is a problem I can't solve by having the right hardware.
Because as I said, everything works fine in windows (Sony Vegas and Final Cut), so, is it my pc or can I actually use a video editor in linux if I only have the right hardware?

I really don't wanna waste money on a new PC if I'll end up with the same results as now.
I really wanna use Openshot, OpenMovieEditor and Cinelerra without getting worried about crashes and freezing problems.

---

### Post by Grenage on 2011-03-23
Well you said that you were after a powerful x64 machine, I can tell you now that Atom is really not the way to go in terms of CPU power.

That said, if your video editing works in Windows, I'd use Windows for video editing.  It beats shelling out for a new PC; unfortunately I have nothing else to suggest as to the Linux crashes.

---

### Post by colobix on 2011-03-23
True, but I wanna get rid of windows. It takes up space, and I barely use it.

---

### Post by Hero1969 on 2011-03-23
I so wanted kdenlive to work for me, but the project / clip preview window just would not display properly.  It did not want to play nice with my video card.  Other than that, it is a very good choice and there is supposed to be a new version this month.  Maybe I'll give it another shot.

---

### Post by colobix on 2011-03-23
> **Hero1969 said:**
> I so wanted kdenlive to work for me, but the project / clip preview window just would not display properly.  It did not want to play nice with my video card.  Other than that, it is a very good choice and there is supposed to be a new version this month.  Maybe I'll give it another shot.

For me it doesn't even come so far. it crashes when I try to add a clip.
From what you guys have been saying, I assume that video / audio editing is just not a thing you can do in linux.
But if that is correct, then why do people make these programs?
If these programs will only work with a few PCs, then I'm sorry but I can't really see a point in even trying.
SO can someone plz verify for me if it's worth it or not?
And if it is, what new pc is the best and has the best hardware and all that to run these programs without crashing and freezing every time I try?
As I said above; if it's not worth it, it's not worth it.
And creating software that doesn't work on your PC doesn't sound fair to me. I know it's free and all, but to me that's not an excuse. I don't mind paying for software. If I have to buy a new PC now and I'll have the same stupid bugs on that computer, then why should I even try? 

So please tell me now what to do here.
I believe in Linux, but ONLY If it WORKS, and doesn't crash on me all the time!
And as I said. if you recommend me a new pc, then money is not a problem. I just want things to work 100 percent stable, smoothly, fast and all that.

---

### Post by Grenage on 2011-03-23
> **colobix said:**
> From what you guys have been saying, I assume that video / audio editing is just not a thing you can do in linux.

Oh no, the vast majority of us don't have a problem with it.  I've only had an editor crash on me once, when trying to work with a corrupted file.

As for a PC that works well with Ubuntu, you're usually best off sticking with manufacturers such as Intel/Nvidia.  My current PC is a Phenom II x4, with a GeForce 8400 GS and 8GB RAM; it's been incredibly reliable.  Ultimately, nobody here can say 'If you buy this, this, and this, it will _definitely_ work'.  We couldn't say that for any OS on any computer; the problems you are getting are peculiar, and make me suspect hardware.

---

### Post by colobix on 2011-03-23
That's what I thought. Well, my graphics card is nvidia, and my CPU is intel. So I don't know why I am having these problems them.

---

### Post by coldraven on 2011-03-23
go here [http://novacut.com/](http://novacut.com/)
read the page
watch the trailer, the link is on the top left
read what they used
it worked for them!

---

### Post by kelvin spratt on 2011-03-23
I use cinelerra with out any problems at all you need a  Amd processor as they will run continuous at 100% and cinelrra is very demanding   intels stutter as they have a low duty cycle as they boost more power than they can maintain. Also the most probable reason for your loss of ram is the graphics card is sharing your mainboard ram. You must remember its your graphics card that does all the work with video. look at my sig

---

### Post by colobix on 2011-03-24
Yes I already use ubuntu 10.10 amd64.
But that obviously doesn't help me much.
I really don't think I can blame the computer at all here since it's only a few months old.
OK so this whole crash / freeze thing is a cpu issue, right?
My windows 7 is a 32 bit, and runs like a charm.
My brand new installed ubuntu 10.10 is a 64 bit, but video and audio editor programs are either freezing or crashing for no reason. I Had even more freezing and crashing on my 10.04 32bit version.
This doesn't make any sense to me.
How come windows work so much better for me?
I thought linux was suppose to be better.
People are contently saying that Linux is the future.
Ok, I know windows supports more hardware and all that, but as I said my PC Is new.

---

### Post by Canime on 2011-03-24
I just want to chime in here and add that i have had issues with installing the right drivers for nVidia in the past, and currently have a browser that is crashing continuously on any flash related media. Also as default, none of the media players will even read a DVD and play them.

---

### Post by colobix on 2011-03-24
Ok I bought a new pc today.
One with a much better nvidia card and a better processor.
I assume this is a graphics thing though, because these programs crashes more often when I have Compiz enabled, which I always have actually.
So I hope this new pc will do the job. It was the most expensive PC they had on that site.
It was an acer pc btw.

---

### Post by colobix on 2011-03-25
bump

---

### Post by kellemes on 2011-03-25
Personally when using resource hungry apps or procedures I always startup some light window manager like Fluxbox.
For video-editing I want all the resources my machine has to offer and not have a gazillion unnecessary  daemons running..
So working from a bloated environment like Gnome (with Compiz) is out of the question for me..

I have the best experiences with Kdenlive.

---

### Post by colobix on 2011-03-25
Disabling compiz every time? 
Well, I need compiz because of the zoom feature.
So disabling compiz is out of the question for me :)

---

### Post by kellemes on 2011-03-25
> **colobix said:**
> Disabling compiz every time? 
Well, I need compiz because of the zoom feature.
So disabling compiz is out of the question for me :)

I understand..
My point is that **if** you find Compiz to be the reason of instability (comes to no surprise) you should avoid it.. And if it's a zoom-feature you need, well.. there are alternatives zoom-utilities.

Good luck.

---

### Post by colobix on 2011-03-25
> **kellemes said:**
> I understand..
My point is that **if** you find Compiz to be the reason of instability (comes to no surprise) you should avoid it.. And if it's a zoom-feature you need, well.. there are alternatives zoom-utilities.

Good luck.

Thanks. Does zoom utilities work the same way as with compiz?
I mean with super + mouse scrolling? I really like the xompiz zoom because of that. I need to zoom in when I read something, so that's why I find that function very useful.
Because with most zoom programs I have to deal with one specified size.

---

### Post by kellemes on 2011-03-25
> **colobix said:**
> Thanks. Does zoom utilities work the same way as with compiz?
I mean with super + mouse scrolling? I really like the xompiz zoom because of that. I need to zoom in when I read something, so that's why I find that function very useful.
Because with most zoom programs I have to deal with one specified size.

I'm sorry, I don't have any experience with these apps so I really can't help you here..
But if may be worthwhile to search and try other apps that offer this zoom-thing..

---

### Post by colobix on 2011-03-25
ok, thanks for all your help. I'll continue this thread here when I have the new PC. IF I still have this problem then.

---

### Post by colobix on 2011-04-02
Ok so now I'm on my new PC, and it's an awesome pc btw:)
HD quality videos are not lagging now, and things are way faster.
I have a 3d monitor now so I can finally make my videos in 3d.
But as for video editing in linuz ;(
The software I use for this in linux are still crashing while I am doing this. Avidemux crashes on videos higher than 720p, openshot disables compiz all the time which bugs the crap out of me.
Now I understand why linux doesn't have any good video editing software yet. Editing videos in linux is a nightmare, and you'll need the newest of hardware to even be able to edit the videos.
So for now I guess I should just give it up. I have no idea why everything have to work so damn smooth in windows but not in linux. I really wish it wouldn't be like that.
Well, you can at least do simple editing in linux. I will give it that. But when some of you guys say it works like a charm... Yea right. I don't mean to complain here but I'm just pointing out the obvious here.
Someone please give me a call when a REAL video editor is available for linux users.
And after this experience, I do not take a software seriously unless I have to pay for it.
I mean, take a look at some of the best video editors for windows. You got Adobe Premier, Sony Vegas and PowerDirectory.
These are all good video editors I can recommend.
The most stable video editor with a lot of features in linux is KDENLive. But it got its bugs and stuff that makes it frustrating to use. Take the zoom function. The preview stops working when you try to zoom in or out.
In OpenShot, The zooming doesn't even work in the newest version.
THen we have VLMC. Also good but FAAAAR from perfect.
So you see. I'm using 100 effects and stuff at the same time to make the video look and sound as awesome as possible. A lot of fast editing, and such.
So yea, take a look at the 3 Windows video editor examples I gave you above. 
Make something like that for Linux, make it stable as hell, and then we can see if I'm prepared to remove Windows.

Something good came out of this. I bought the best and the most expensive PC ever :)

---

### Post by Hedgehog1 on 2011-04-02
colobix,

I still dual-boot Win7 & Ubuntu.  I do it for 2 reasons:

* Sony Vegas (the best video editing software I have ever used)

* Photoshop (GPU processing only works in a real boot, not in a VM)

These are the only reasons I don't run Ubuntu 100% of the time and just use VMs for the odd Windows need.

This is not the fault of Linux - but rather the long standing market that is PC based.  Sony Vegas doesn't even offer a Mac version, it is Windows only.

Until there is a 'critical mass' of Linux users who need full-blown video editing, we will both be dual booting. 

There is some good news - at least the same hardware runs both OSs, so we can dual boot rather than have to have several computers crammed next to each other.

When we see these applications in Linux:

* MS Office
* iTunes

Then the number of folks who will be willing to convert will jump up.

The niche market for high-end video editing may be along time coming to Linux.  ***So we Dual-Boot and live our lives anyway...***

[B][I]
The Hedge[/I][/B]

:KS

---

### Post by colobix on 2011-04-03
True. 
But I'm not so sure when it comes to jumping numbers after MS ofice and iTunes comes to linux.
Maybe iTunes, but Libreoffice and openoffice are more than good enough to beat MS Office.
But I think the main problem about linux is that people expect the software to be open source and free.
To most people, money is not a big deal as long as the software or game kicks ***.
But something that really frustrates me here on this forum is that so many people try to make linux sound like a paradise, instead of being honest.
People have been saying "you need better hardware", and stuff like that.
While that is clearly not the case.
I realize now after I bought the new PC that hardware is not the issue. The issue is free and open source.
If people expect things to always be free and open source, linux will never get the attention it deserves.
We need companies like Adobe and Sony to make software for us. Not free or open source, but awesome software that will "force" people to prefer Linux instead of Windows or Mac.

---

### Post by Hedgehog1 on 2011-04-04
I agree there is a tendency to over sell the free applications at times.

There is also a lack of knowledge when causal users and power users are talking.  Video editors are a good example.  A casual user with basic edit requirements has his/her needs meet by the basic video editing tools available. For power users who does a/b roll video transitions and mix dozens of audio tracks to get the right sound, these tools are not adequate.

Same with libreoffice. Power users of spreadsheets cannot get by on it (yet).  Most companies user MS outlook as shipped with office. Mine does.  I have to use it, no choice.

Some products are available for Linux; Like Nero Burning ROM.

I know that I will be forced to either dual boot or keep a VM of Windows for these other reasons.  I am OK with that.  I have many tools in the garage; and a saw does things a hammer doesn't.  So I use multi OSs and there separate.  Can do.

***The Hedge***

:KS

p.s. iTunes in Linux would be very nice for iPod support.

---

