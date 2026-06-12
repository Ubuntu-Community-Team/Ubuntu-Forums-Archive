---
title: "having trouble with a *.run file."
date: 2011-03-02
forum: General Help
---

### Post by Keypel on 2011-03-02
Ok I have a *.run file on my Desktop. It's a Nvida driver I want to install.

I right clicked the *.run file and marked it as executable. Then I double clicked the file and chose the run in terminal option. the error I got was that I had to run it as root. (ps it never asked me for a pass, it just said I had to run it as root, no option to input pass.)

Then, I started guessing. I opened up a terminal and did a sudo su. then I browsed to my Desktop using ls and cd commands but then I didn't know how to run the *.run file. So I just typed the file name and hit enter but it just said command not found. how do I run the NVIDIA-Linux-x86-260.19.36.run file? I'm lost here.

---

### Post by jwcalla on 2011-03-02
You can run it by typing ./NVIDIA-Linux-x86-blah-blah.run.

If you need admin privileges then try sudo ./NVIDIA...blah blah.  

BUT you should be able to get the latest NVIDIA driver through Synaptic so that it updates automatically.  I ran one of those .run scripts before and naughty things happened, but it could have just been a bad experience on my part.

---

### Post by Keypel on 2011-03-02
Thanks is was missing the "./" 

Now it's complaining that x server is running and I need to shut it down before continuing.

I give up for now.

The whole thing is that I have nvida ion built into my mainboard. according to the back of the box, it has purevideo&#8482; and is capable of 1080p video playback which is a total joke because I can't even play a 720p x264 much less 1080p.

I thought maybe it was a driver issue. I did install the restricted nvida driver when ubuntu asked, so I don't know if this nvida driver is already installed or not but I think it is, but dang does this thing suck for hd video.

my motherboard doesn't have any expansion slots so I can't even add a better video card and even if it did have a slot, my psu is too small and I don't even think they make a bigger one for my mini-itx case.

---

### Post by jwcalla on 2011-03-02
Is there a reason in particular you're not getting updates from Synaptic?  Though they do have a later version of the driver in the repositories (I guess it's a beta).  I think you have to have the [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) PPA added to the software sources.  But it should have done that automatically.

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> Is there a reason in particular you're not getting updates from Synaptic?  Though they do have a later version of the driver in the repositories (I guess it's a beta).  I think you have to have the [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) PPA added to the software sources.  But it should have done that automatically.

Still kind of new to unbuntu. I went to the Synaptic Package manager and did a filter for nvida. I can see Nvida 260.19.06 is already installed. 

I think my onboard Nvida ion is just too wimpy to play anything high def.

I should probably find some Nvida forums to be asking these types of questions on.

---

### Post by jwcalla on 2011-03-03
Don't give up yet.

1) Does it say which version of PureVideo it supports?
2) Processor type?
3) Which video player are you using?

---

### Post by jwcalla on 2011-03-03
I don't know anything about the nvidia ion but if Wikipedia is to be believed, my friend you should have no problem getting flawless 1080p playback.

I suspect your issues might be related to the player you're using or VDPAU support.  You'll need VDPAU activated for hardware accelerated decoding.  Unfortunately I'm not too familiar with VDPAU (I have an older video card that doesn't support it), but do a search maybe on the forums here or the Interwebz for VDPAU and maybe mplayer and smplayer, which I think is one of the better video players.

Even I can get flawless 1080p (but just barely) and I have no hardware acceleration on the video card.  My dual-core 2.2 GHz processor handles it all.

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> Don't give up yet.

1) Does it say which version of PureVideo it supports?
2) Processor type?
3) Which video player are you using?

My CPU is low end. Single core 1.6Ghz

Here is some of my GPU info

cuda cores: 16
Graphics Clock 450mhz
Memory Clock 664mhz
procerror clock 1100mhz
graphics processor: ION	
memory 512mb
merory interface 64-bit

No it doesn't specify which PureVideo it has other than PureVideo HD.

And I was using vlc player. Already checked the vlc player settings and hardware gpu acceleration is already enabled.

---

### Post by jwcalla on 2011-03-03
I'm not sure, but I think VLC is yucky with VDPAU support.  Maybe I misread that somewhere once.

Try popping into Synaptic and installing mplayer (backend) and smplayer (frontend) and then try playing a video in smplayer.  I don't recall if it supports VDPAU by default out of the box or if you have to do something fancy.

---

### Post by jwcalla on 2011-03-03
This thread offers some guidance:

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

I think the VLC player uses VA-API for acceleration by default.  You might need to install another library for VDPAU support, which appears to be in Synaptic.  (But then will you have to reinstall VLC?)

If you want to go the mplayer route, consider this from that thread:  "Once you've got it installed, select Options>Preferences. Click on  the Video tab. Change the output driver to VDPAU. You should now be able  to use Smplayer with the mplayer backend and play all x264 flicks and  standard DVDs with little or no CPU usage. For all other files, Smplayer  will automatically select the appropriate codec."

---

### Post by Keypel on 2011-03-03
[IMG]http://img850.imageshack.us/img850/3391/screenshot.gif[/IMG]

I get this error and it's droping frames like crazy now. I'm getting like 1 frame every 15 seconds.

---

### Post by jwcalla on 2011-03-03
What happens if you select the most recent version from the list?  Or is that the only version listed?

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> What happens if you select the most recent version from the list?  Or is that the only version listed?

I selected the most recent version and the video started playing smoother (still a bit choppy but playing more fps) but lost sound. I'm not sure where the setting is to change it again.

---

### Post by jwcalla on 2011-03-03
Is that with the VDPAU output driver set?  For the audio you might have to select a different output driver on the Audio tab in the Preferences.

I have to go sleepy for now... I'll check back in tomorrow.

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> Is that with the VDPAU output driver set?  For the audio you might have to select a different output driver on the Audio tab in the Preferences.

I have to go sleepy for now... I'll check back in tomorrow.

I have to sleep too lol lmk where the vdpau setting is tomorrow ok? G'Night.

---

### Post by jwcalla on 2011-03-03
> **Keypel said:**
> I have to sleep too lol lmk where the vdpau setting is tomorrow ok? G'Night.

In SMPlayer?

It's under Options -> Preferences -> General (option on left list) -> Video tab -> Output driver.  vdpau should be in that list (mine's at the top)... if not... we have work to do. ;)

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> In SMPlayer?

It's under Options -> Preferences -> General (option on left list) -> Video tab -> Output driver.  vdpau should be in that list (mine's at the top)... if not... we have work to do. ;)

ok, found it.

it's playing "better" than vlc now but somethings still not right. my cpu is maxing out to the point where I can't even move my mouse pointer. using system moninor, I can see both cpu1 and cpu2 screaming at 100%. (btw I'm not sure why it shows 2 cpu's when I just have a regular single core cpu.) 

btw my test video is only 720p x264 mkv

Ok, going to bed now, Gnight.

---

### Post by debd on 2011-03-03
if just wanna install the driver anyway you can follow this method. this is how i installed it.

boot ubuntu in recovery mode.

If you're dual booting, you'll get the Grub menu when you boot up your PC. If you're not dual booting, you'll need to hold down Shift as the PC boots  until you see the Grub menu. 

You should then get to the Recovery Menu. Using your keyboard arrows again, move down to where it says "root" (or you could press "r" on your keyboard). Press Enter.

You should now be a root command prompt.

Type "telinit 3", without the quotes, and press Enter.

You should now get a prompt asking for your normal username, and then your password.

When you've logged in, navigate to where your "NVIDIA*******.run" file is stored.

Once there, type "sudo sh ./NVIDIA*******.run" (without quotes), obviously typing in the proper name of the file.

That should start the install process, but at the 1st go it will ask you to stop the nouveau kernel driver. its ok to stop the driver. now reboot into normal mode.
U'll get a command prompt.
login.
now again type: sudo sh ./NVIDIA*******.run

follow the instructions. mostly you slould select "yes". it should be installed.

keep the nvidia file name and the commands handy.

good luck.

let me know if it worked.

---

### Post by veggen on 2011-03-03
I had some wierd experience with MPLayer and VDPAU. Check [this](http://ubuntuforums.org/showthread.php?t=1664121) thread, maybe it's of some value.

---

### Post by Keypel on 2011-03-03
Thanks for everyones replies. I guess the next step is to just install the newest nvidia driver.

My question is according to my Synaptic Package Manager 260.19.06 is the current version (which is already installed) and the one I downloaded from Nvidia.com is 260.19.[COLOR="Red"]36[/COLOR]

I'd much rather the Synaptic Package Manager install it for me as it seems much simpler. But how do I get 260.16.36 to show up in Synaptic? Reloading the package info doesn't seem to do the trick. Do I have to add something to the repositories or something?

---

### Post by jwcalla on 2011-03-03
Yes... go over here:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And click on the pop-up link that says "Read about installing".  Follow the 3 steps there.

Then go into Update Manager and run the "Check" button.

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> Yes... go over here:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And click on the pop-up link that says "Read about installing".  Follow the 3 steps there.

Then go into Update Manager and run the "Check" button.

Ok, I got the nvidia driver updated to 270.29 by adding the ppa and then using the update manager. Many video related updates were installed.

According to the system monitor my cpu usage is now lower and no longer screaming at 100% and the memory usage is also lower however, the 720p x264 mkv I am using for testing is still playing both audio and video choppy. Mostly the video. It's jerky when panning and is dropping frames. Looks like I'm playing a picture sideshow at times. The vdpau is definitely enabled in smplayer.

Is there a way to see how hard the gpu is working as is it possible to see how many fps the video is dropping?

---

### Post by jwcalla on 2011-03-03
You can try running nvidia-smi -a to check GPU utilization, if your video chip supports it.

---

### Post by jwcalla on 2011-03-03
You could also try running mplayer from the command line just to rule out any potential smplayer issues:

mplayer -vo vdpau your_video_file_name

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> You can try running nvidia-smi -a to check GPU utilization, if your video chip supports it.

user-01@pc-01:~$ nvidia-smi -a

UUID error: 0x8
Failed to initialize NVML: Unknown Error

[QUOTE=jwcalla] 

You could also try running mplayer from the command line just to rule out any potential smplayer issues:

mplayer -vo vdpau your_video_file_name[/QUOTE]

Well, it plays differently. The av sync is way off but the video is dropping less frames and is less jerky when panning.

---

### Post by jwcalla on 2011-03-03
> **Keypel said:**
> user-01@pc-01:~$ nvidia-smi -a

UUID error: 0x8
Failed to initialize NVML: Unknown Error

Yeah I get that too.  We must not be special. :(

> Well, it plays differently. The av sync is way off but the video is dropping less frames and is less jerky when panning.

I'm running out of ideas.  Can you post the output from mplayer?

I wonder if it's a problem related to the sound.

Is it any smoother if you play it with the -nosound option?  mplayer -vo vdpau -nosound your_video_file_name

---

### Post by Keypel on 2011-03-03
Here is the mplayer output

[[IMG]http://img29.imageshack.us/img29/255/nshot1.th.gif[/IMG]](http://img29.imageshack.us/img29/255/nshot1.gif)

It's about the same with and without sound.

One thing for sure, smplayer+vdpau is much faster than anything I was using before. Still... strugles with 720p x264. The back of my mainboard box says it can easily play 1080p but I don't think so.

I'm not sure which generation of purevideo hd it has but I think it's either 2nd or 3rd gen from what I have read on wiki.

I should probably take this discussion to the zotac forums and I appreciate all the help.

---

### Post by jwcalla on 2011-03-03
Hmmm... it doesn't look like mplayer is using the right codec... you could try:

 mplayer -vo vdpau -vc ffh264vdpau your_video_file_name

But I suspect smplayer was selecting the right codec during playback so that might not be it.  (You can check in Options -> File info and properties... -> Video codec -> should be ffh264vdpau for that file.)

Otherwise, consider looking or asking around the nvidia forums:  [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) .  They also have a linux section there.  Something seems wrong because even 720p should play okay.

---

### Post by Keypel on 2011-03-03
Hmmmm.....

now that's interesting

I used mplayer -vo vdpau -vc ffh264vdpau your_video_file_name

by far the best I have seen so far, Ok, maybe a few hicups but still very watchable and the av sync seemed fine. I was very surprised. I'm not noticing many framdrops and is only slightly jerky in some high bitrate seens but at least it's watchable.

I'm not good at command prompt at all, how can I get it to play like this in a gui? vlc, smplayer, etc.

How did you know mplayer was using the wrong codec?

smplayer "is" using ffh264vdpau but playback is jerky and chopy.

---

### Post by veggen on 2011-03-03
This all sounds *very* similar to my problem, that I (mostly) solved. Have you checked out my thread?

---

### Post by jwcalla on 2011-03-03
> **Keypel said:**
> Hmmmm.....

now that's interesting

I used mplayer -vo vdpau -vc ffh264vdpau your_video_file_name

by far the best I have seen so far, I didn't noticed any jerky play or frame dropping at all. Ok, maybe a few hicups but still very watchable and the av sync seemed fine. I was very surprised.

I'm not good at command prompt at all, how can I get it to play like this in a gui? vlc, smplayer, etc.

How did you know mplayer was using the wrong codec?

I noticed in your mplayer output that the video codec it selected was ffh264 rather than ffh264vdpau.

I think there was a bug in SMPlayer that also failed to pass along the -vc codec switch to mplayer, which was fixed in version r2939.  Can you post the output of smplayer -v?

You can also try forcing the codec in SMPlayer to see if that fixes playback:  Options -> Preferences -> Advanced -> Options for MPlayer and paste "-vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau" into the "Options" field.

You can also try installing gnome-mplayer, another frontend for mplayer.  There are some similar config options that have to be setup to specify the output video and audio drivers.

---

### Post by jwcalla on 2011-03-03
BTW if you're playing files with MKV ordered chapters, we have more work to do.  You'll need a custom build of ffmpeg and mplayer.  I think it's the only non-Media Player Classic Home Cinema (i.e., for Windows) video player in the universe that supports MKV ordered chapters.

](*,)

---

### Post by Keypel on 2011-03-03
> **veggen said:**
> This all sounds *very* similar to my problem, that I (mostly) solved. Have you checked out my thread?

yes, I did. a bit technical for me but in the end didn't you say it was mostly driver related and that updating mostly solved your problem? My drivers are now up to date.

> **jwcalla said:**
> I noticed in your mplayer output that the video codec it selected was ffh264 rather than ffh264vdpau.

I think there was a bug in SMPlayer that also failed to pass along the -vc codec switch to mplayer, which was fixed in version r2939.  Can you post the output of smplayer -v?

output of smplayer -v is:
This is SMPlayer v. 0.6.9 (SVN r3447) running on Linux

Looks like my version is old? I just got it from Synaptic?

[QUOTE=jwcalla] You can also try forcing the codec in SMPlayer to see if that fixes playback:  Options -> Preferences -> Advanced -> Options for MPlayer and paste "-vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau" into the "Options" field.[/QUOTE]

YUP, That did it. smplayer now works as "well" as the mplayer command line you had me do. Not perfect but 1000 times better than before posting this thread. I think all this time that I was not using any hardware acceleration for playing video files. Does vlc player not support vdpau?

[COLOR="Red"]edit: [/COLOR]

spoke too soon on smplayer. still not right. playing it with the mplayer command line is still yielding the better playback. I should figure how to update smplayer and try it again. or maybe it has somthing to so with the way smplayer renders subtitles as veggen has said in his other thread. I could build a new video file with mkv merge without subtitles and see if smplayer plays it any smoother?

[QUOTE=jwcalla]You can also try installing gnome-mplayer, another frontend for mplayer.  There are some similar config options that have to be setup to specify the output video and audio drivers.[/QUOTE]

I would have never imagined that playing hd would be so difficult.

---

### Post by jwcalla on 2011-03-03
I'm not sure if VLC supports vdpau... I think it uses va-api or something like that for hardware acceleration, and I don't think nvidia employs that technology.

It looks like you have the latest version of smplayer.  Does it play any smoother when subtitles are turned off?

---

### Post by wiggly81 on 2011-03-03
the graphics card could well be capable of 1080p but if the monitor isn't then it will make no difference what driver you run, do you know the max resolution of your monitor ?

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> I'm not sure if VLC supports vdpau... I think it uses va-api or something like that for hardware acceleration, and I don't think nvidia employs that technology.

It looks like you have the latest version of smplayer.  Does it play any smoother when subtitles are turned off?

no smplayer doesn't play it smoothly with or without subs.

but I do have good news, on a whim I tried xbmc for linux. I found it when google'ing my motherboard + x264. Anyways I just added the ppa and installed it through Synaptic. It supports VDPAU, mkv chapters, and best of all it plays the 720p mkv I was testing flawlessly. I mean absolutely flawlessly!

I still like vlc for simplicity but, hey what can I do.

---

### Post by jwcalla on 2011-03-03
Wow I'm surprised XBMC worked for you because it tends to be heavy on the processor.  Unfortunately they don't have a version that supports ordered chapters yet, but that's a minor inconvenience.  XBMC is great if you intend to build a media library.

Now it's time to find a 1080p video.  :)

---

### Post by Keypel on 2011-03-03
> **jwcalla said:**
> Wow I'm surprised XBMC worked for you because it tends to be heavy on the processor.  Unfortunately they don't have a version that supports ordered chapters yet, but that's a minor inconvenience.  XBMC is great if you intend to build a media library.

Now it's time to find a 1080p video.  :)

I can't tell if xbmc is hard on the cpu or not because xbmc runs in full screen. I can't figure out how to switch to the system monitor while it's running but I do know xbmc is bulky. Generally I am not a big fan of bulky programs. My favorite programs are small clean and "just work"

but for now xbmc is playing what others would not. I really thought my problems were hardware related but it seems they are mostly software related. I almost went out looking for new hardware.

xbmc works for now, I'm sure programs like vlc, smplayer, mplayer, movie player, etc will catch up in time. I have no idea why I can't get smplayer to run smooth but at this point I don't really care. This beats re-encoding every time I want to watch something.

I'm satisfied with the outcome, Thanks for all the time and effort you put into helping a stranger out!!

---

### Post by jwcalla on 2011-03-03
No problem!  I'm glad you found a solution that works.  After all... a man's gotta have his 1080p.

And we get to go to bed early tonight.  ;)

---

