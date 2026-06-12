---
title: "I want to Destroy my Windows Install, but need help first :)"
date: 2006-05-30
forum: General Help
---

### Post by deejross on 2006-05-30
Hello everyone,

Like many, I am looking to move to a completely Linux-based environment. However, I have seen alot of questions about office programs and email programs and all the rest of the general computing stuff. I, on the other have done my fair share of research on alternatives to programs I use everyday on Windows and I couldn't find much. Most of the things I need either don't exist (to my knowledge), could not get to install, or were impossible to use and didn't contain the required features.

So I need some opinions on software for Linux that can replace my Windows apps. These might be a challenge, since we all know writing a "hello world" console app is NOT real programming any more than making a snare drum loop over and over is NOT real music production. This is my list of absolute requirements:

**Absolutly have to have**

[LIST]
[*]VB.NET / C# Programming Environment
[/LIST]
[INDENT]I use Microsoft Visual Studio 2005. I know you can use the Mono framework and MonoDevelop. When I tried the first time, it didn't support VB.NET, which is what all my projects are written in.[/INDENT]

[LIST]
[*]Multitrack Audio Production Software (loop-based if possible)
[/LIST]
[INDENT]I use Sony ACID. For those that don't know, Sony ACID is a loop-based multitrack audio production tool. There is Audacity, but I need to be able to quickly and easily match samples to the same tempo. I also tried Agnula (ardour) or whatever it's called, but found it impossible to use. And yes, I read the documentation. Which is more than incomplete anways. I couldn't time-stretch any samples and all I could import were wav files. Everything I have is OGG or MP3 and it's a pain to decode those to wav when you are working on a remix with 100+ samples.[/INDENT]

[LIST]
[*]Video Editing Tools
[/LIST]
[INDENT]Right now, I use Sony VEGAS, but only because I need to create titles and overlay audio tracks and all. But I use VirtualDub for fixing audio sync and cutting frames out of AVI files. I like to use it for simple tasks like that because you don't have to decompress and recompress and entire video file just to cut a few frames out of it. As for the video editing suite (I guess you would call it) I tried jashaka, but to be honest, I'd be better off printing the frames to my printer and glueing them all together to make a movie rather than use that thing. I didn't even load my video files.[/INDENT]

[LIST]
[*]FruityLoops Studio equivelent
[/LIST]
[INDENT]This is also a biggy. I tried using LMMS, which kinda looks like FruityLoops, but it is nothing more than a drum sampler/sine wave creator. I would need to use VST instruments (or equivelent) along with effects plugins (since you can't take a generated sine wave and make it sound like a real instrument).[/INDENT]

If you are still here, I applaud your patience. And I think that's all I would really NEED. Everything else would be conveniece, which I could find or ask about later :) 

I don't mean to be long winded and pickey about everything with my list of requirements, but the fact is, I can't do what I need to do without this stuff, anymore than you can breath without oxygen. I know that there won't be an exact replica of every program I use, and I'm willing to learn new programs. But if they can't do what I need them to do and do it efficiently...again...no oxygen.

In closing, I love Linux. I have made servers at work out of Ubuntu that we have become dependent upon. My hope is that one day, we can replace all our Windows workstations with Linux-based systems that don't crash every 10 minutes. So please help me with this ;)

Thanks

---

### Post by colo on 2006-05-30
I may be able to give you a hint on what to check out if you want to do video-editing on a GNU/Linux-basis. There are 2 big players from what I know, namely "Kino" and "Cinelerra". Just check them out, both are Free Software:

[http://www.kinodv.org/](http://www.kinodv.org/)
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

A VirtualDub-replacement (although with less features and somewhat ugly ;)) even sharing some code with it is in existance under the name "avidemux2".


Can't really help on the other topics, though - sorry.

---

### Post by honeydew on 2006-05-30
maybe audacity for the audio?
[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

---

### Post by deejross on 2006-05-30
I will look into the video editors you suggested. I remember looking at them once, but never actually tried them out. If I recall correctly, though, Kino doesn't support titling or audio overlay.

Audacity, as I mentioned before, is a good audio editor, like CoolEditPro (now Adobe Audition) and like Sony SoundForge. However, these are only editors, not producers. Even though they all allow you to multitrack, it is not true multitracking because you have no control over the mix other than the placement of the tracks. This is good for doing commercials, where you lay voice over music and they don't need to be in sync with each other. I mean, you could in theory (if needed to have tracks sync with each other) take every track and guess the value of the time stretch over and over again until you got it right, but that could take hours upon hours. This goes back to effeciency. Why waste an entire day getting 3 or 4 tracks in sync with each other when I can do the same thing in 5 minutes with ACID?

I'm not trying to shoot anyone down, I'm just making sure you understand that entry-level tools or tools where you could "in theory" do something rarely ever work in the real world.

So far, so good though...keep the ideas flowing! :)

---

### Post by Gomek on 2006-05-31
Mono *should* have VB.NET support...

[http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)

---

### Post by blackjack6.21.91 on 2006-05-31
for the frooty loops/acid you might be interested in a program called wired.  its still in beta, but its fantastic and it's probably worth a try.

[http://www.gnomefiles.org/app.php?soft_id=598](http://www.gnomefiles.org/app.php?soft_id=598)

---

### Post by blackjack6.21.91 on 2006-05-31
also see if *diva* meets your video needs.

[http://www.gnomefiles.org/app.php?soft_id=1335](http://www.gnomefiles.org/app.php?soft_id=1335)

---

### Post by nanotube on 2006-05-31
you could always try running some of those apps with wine, if you end up unable to find a native replacement.
or even run a whole windows under vmware :)

---

### Post by deejross on 2006-05-31
Wired looks very cool. Diva actually looks very cool as well. It's too bad they are both in alpha status.

I think I'm going to end up using Mono for development. They just have to finish their implementation on System.Drawing and it's children before I would be able to port my applications to Linux.

I tried using Wine for something about 4 months ago but couldn't even click the Accept button on the installer to install the application because the fonts were so wacked out. Does anyone know if they have made any leaps and bounds in Wine recently?

I can't help but think that the whole Linux scene is still in it's childhood when it comes to applications like these that the professionals are looking for. Does anyone think that one day projects like these will evolve into mature apps, like OpenOffice?

---

### Post by Master Shake on 2006-05-31
For the fruity loops replacement, try the excellent Hydrogen.  Its in the repos.

---

### Post by blackjack6.21.91 on 2006-05-31
As more people switch to linux, the community will get better and better: open source software will develop at staggering rates.  That's why it's important to grab a friend and introduce him to linux.

As for the two pieces of software I suggested, I'll side with you when I say they probably aren't stable, but keep an eye on them (and maybe even help create them), so that when there is a version that meets your needs, you can destroy your windows partitions.

Anyway, I'm installing hydrogen now, and I'll probably give it a ride later so thanks for the suggestion!

-rugglesworth

---

### Post by nanotube on 2006-05-31
[QUOTE=deejross]Wired looks very cool. Diva actually looks very cool as well. It's too bad they are both in alpha status.

I think I'm going to end up using Mono for development. They just have to finish their implementation on System.Drawing and it's children before I would be able to port my applications to Linux.

I tried using Wine for something about 4 months ago but couldn't even click the Accept button on the installer to install the application because the fonts were so wacked out. Does anyone know if they have made any leaps and bounds in Wine recently?
[/QUOTE]
i don't know what they mean by "recently", but wine works pretty well for me in its 0.9.something incarnation. just install the freshest version from the wine repository (not the default repository) and give it a try... here is their ubuntu instructions: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by honeydew on 2006-05-31
sweet programs.. tis a constant evolution... great community. Im installing dapper rc right now.. hopefuly I will have hydrogen running tonight.. assaulting the world with opensource heavenly beats =]

---

### Post by blackjack6.21.91 on 2006-06-01
Wine will probably never be able to run the majority of mainstream apps out of the box, but for some general tweaking and setup tips, see the following thread.   
[http://ubuntuforums.org/showthread.php?t=149585&](http://ubuntuforums.org/showthread.php?t=149585&)

Also, I looked into hydrogen, and it doesn't do much for the ACID part (I suppose it wasn't supposed to), but it provides a most of the main features of frooty loops.  Though it's not nearly as developed, hopefully it will meet your needs.

-r3as0n_1s_tr3as0n!

---

### Post by Masterj15 on 2007-04-12
In order to get everthing from fl studio to lmms and put prests to that I would sugest using total video converter to convert the .mp3's in the presets to .ogg theirfore, extract the presets from flstudio to lmms after the convertion from .mp3 to .ogg. this will give you everything that you would want from flstudio on lmms.:D

---

