---
title: "Does 10.04 allow use of gnomad2 with creative zen 30GB?"
date: 2010-05-01
forum: General Help
---

### Post by dogdo on 2010-05-01
Hi ive already logged a bug on launchpad but it hasent been fixed yet. Basically i cant use a program called gnomad2 to access my creative zen 30 GB media player. I was able to do this under 9.10. Anyone know of a fix?

---

### Post by WorMzy on 2010-05-01
Do you have to use gnomad? Because my 32GB Zen X-Fi works fine with Rhythmbox. It was simply plug and play.

I can't help with Gnomad, but I thought I'd offer this information. :)

---

### Post by colnizster on 2010-05-02
:( Same problem here - and i've always had the need for gnomad2 because i've never been able to get video to transfer with rhythmbox.

---

### Post by colnizster on 2010-05-02
here is the terminal output: 

sudo gnomad2
[sudo] password for ____: 
Device 0 (VID=041e and PID=413e) is a Creative ZEN Vision:M.
Queried Creative Zen Vision:M
Segmentation fault

the seg fault happens as soon as gnomad tries to load the contents of the zen. i tried turning off all of the settings in gnomad's preferences but it didn't help

---

### Post by frenchy82 on 2010-05-02
Maybe it's the same problem than here
[https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967]("https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967")

Use libmtp8 from karmic help me
(Somebody found this solution in this forum)

---

### Post by lavinog on 2010-05-02
Try accessing the recovery menu in the zen and do a cleanup...sometimes that helps.
My zen x-fi is very annoying...I don't think ubuntu is the problem because I have issues even when using windows.  mtp-tools is handy for working with videos: mtp-sendfile filename filename

---

### Post by uRock on 2010-05-02
[CENTER]You can install most programs while using the LiveCD to test them.
v
V
|
|
|
|
V
[/CENTER]

---

### Post by sleeper414 on 2010-05-02
im looking for another program to transfer video to rather than gnomad.

any suggestions?

---

### Post by dogdo on 2010-05-02
> **frenchy82 said:**
> Maybe it's the same problem than here
[https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967](https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967)

Use libmtp8 from karmic help me
(Somebody found this solution in this forum)

  Yes i found that in ubuntu 9.10 that gnomad 2 did allow me to tranfer files to my creative zen 30GB. Although this only worked if i unmounted the player and then opened up gnomad 2. It did not work at all when the player was mounted.

---

### Post by dogdo on 2010-05-02
Does anyone know if this problem will be fixed any time soon? I could go back to 9.10 for a while but i will have to update to 10.04 eventually. Sigh.   Btw i was the one who opened up that bug report on launhpad (im user meow on that). Still havent gone a response from the developers. Another Sigh.

---

### Post by lavinog on 2010-05-02
It is likely that the problem will not be fixed until 10.10.
This may not be considered important enough to push an update.

You might be able to update with a ppa, but you may need to wait a month or so for a fix upstream.

---

### Post by dogdo on 2010-05-03
Whose ppa? how would this work exactly?

---

### Post by dogdo on 2010-05-05
> **dogdo said:**
> Whose ppa? how would this work exactly?

 Am i barking up the wrong tree here?

---

### Post by uRock on 2010-05-05
I think he was implying that you search for one that does what you want, while he might not know which one will do it?

---

### Post by lavinog on 2010-05-05
> **dogdo said:**
> Whose ppa? how would this work exactly?

I don't think one exists yet.  It will take time for anything to happen.

---

### Post by dogdo on 2010-05-06
> **lavinog said:**
> I don't think one exists yet.  It will take time for anything to happen.

  Will there be a fix for 10.04 in a years time? I could revert back to 9.10 for now but 9.10 will only be viable security update wise for another 12 months. Have other people reverted back to 9.10 to solve this issue?

---

### Post by lavinog on 2010-05-06
> **dogdo said:**
> Will there be a fix for 10.04 in a years time? I could revert back to 9.10 for now but 9.10 will only be viable security update wise for another 12 months. Have other people reverted back to 9.10 to solve this issue?

Usually issues are resolved in under a year.
In the past I have seen issues fixed within a month upstream, but will require you to manually install the updated program.

---

### Post by Crazy K on 2010-05-06
I'm having the same problem. Is there another program that lets you put music on your zen, without messing with Mtp2lastfm? I scrobble with that, and I heard that sometimes it'll actually mess things up.

Update: 

I actually got it to work by closing out of the scanning process. So far I was able to put a full album into my Zen. So yeah try that out.

Nevermind, I couldn't find the music on my zen. :(

I'll gladly use Rhythmebox if it doesn't mess with my scrobbling with mtp2lastfm.

Used Rhytmebox and that worked fine, I just hope it doesn't mess with mtp2lastfm yo.

---

### Post by erwinsoo on 2010-05-08
Gnomad2 is broken for the Zen (not zen xfi) on Lynx. I can transfer music using rhythmbox but not videos. Apart from copying the vid files on an sdcard and plugging into the zen, nothing else seems to work. Sometimes it really makes you wish that all these linux software were donationware or paid apps. At least, it helps keep developers motivated

---

### Post by wpwend42 on 2010-05-10
I am extremely disappointed that gnomad2 is doing this AGAIN. I have the same problem I had in 9.04: freezes after I unmount and try to load gnomad2. Worked fine in 9.10!!!!

What program do people use otherwise to upload to their Creative Zen player in Ubuntu?

---

### Post by granny6989 on 2010-05-18
It's not really Gnomad's fault... Ubuntu has been making changes to USB devices and docking etc, which has been causing problems with Zen, and a bunch of other devices. Until programs are modified, they will not work so hot with the new mounting scenario. 

Anyways - I just tried a few different things with Banshee, and the Zen (Vision M) worked just fine and loaded music (seems cover art works now too, which didn't work for me through Gnomad). So if you're up for it, try installing Banshee, and make sure to enable MTP support in preferences. Open Banshee, and then plug in your Zen, after a few seconds, it should show up and begin scanning your media. Then it's just drag and drop from your library just like everything else. When you're done, right click on your Zen (in the Banshee window), and click on disconnect. It will disconnect and then update, and you should have music after that. Don't know about video, etc...

S*

---

### Post by psablo on 2010-06-01
I'm still on 9.04 and Gnomad2 used to work with my Zen but recently stopped. I can't even mount the volume, so I guess it's not Gnomad but Ubuntu?  RythmBox doesn't work either, so I tried Banshee, and It seems to be working for now.

I spoke too soon, Banshee at least sees my Zen player (RythmBox does not) but I can't transfer files to it or play files from it. 

Any ideas?

---

### Post by UncleBoxy on 2010-06-03
Same here.  At least Banshee is able to see the device and the files on it.  However, like the above mentioned, when you select "Import Media" and try to use the Zen, it says something to the effect of "MTP import not supported yet".  So basically, hurry up and wait.  :(

---

### Post by erwinsoo on 2010-06-07
Gnomad2 is broken with 10.04. For videos, you need to transfer to sdcard. No issues with Rhythmbox for transfer of songs etc. Works alright, scan, transfer is ok.:popcorn:

---

### Post by granny6989 on 2010-06-08
I haven't had problems with Banshee and Lucid. I have only transferred music to it, not tried Import. If you open Banshee, then plug in the Zen, it takes a few seconds to recognize it. It should appear in the left column. Click on it once, and you will get the status screen, and in the center it will show it reading files. Once that finishes, you should see playlists and Music subfolders on the left. Click on the upper Music folder (your hard drive library), then drag songs from there to your Zen icon on the left. It should show it adding files on the bottom left. Once that is done, right click on Zen and hit 'disconnect'. Your Zen screen should show activity and then updating, then it will unmount.

Hope that helps.
S*

I did just try going from the Zen back to the hard drive, and could not get that to work..... So I guess it's only going to let you load the Zen.

---

### Post by HoKaze on 2010-06-14
I'm pretty sure this has already been mentioned but for those of you who wish to transfer video you're either going to have to resort to using the mtp-tools package and transferring via the command line (e.g.  mtp-connect --sendfile /home/user/Videos/video.avi Video) or go to packages.ubuntu.com, find the karmic version of libmtp and install that instead of the lucid version. You may have to uninstall the lucid version first if the package installer complains or you can force it using "sudo dpkg -i nameofpackage.deb"

This solved all my issues with my 15GB Creative Zen and I hope it works for all of you too.

---

### Post by lavinog on 2010-06-14
yeah, I think the lucid version of mtp-tools has some issues.

---

### Post by HeadHunter00 on 2010-08-01
actually, all you need to do is downgrade libmtp8, that way all your mtp problems will be fixed. follow this guide right here: [http://ubuntuforums.org/showthread.php?p=9666027](http://ubuntuforums.org/showthread.php?p=9666027)
just use the older version of libmtp8 until ubuntu 10.10 comes out, and then upgrade it.

---

### Post by vividia on 2010-08-15
I have a Creative Zen Vision M.  I followed Granny's directions on how to transfer to it with Banshee and after some time I disconnected, pulled on the Zen to check the transfers.  Nothing transferred.  But a bunch of it ended up in my Music folder.  So I tried to transfer it from there since I had pulled it off an external drive.  Nothing.

I checked the extensions and MTP support is enabled.  I've had zero luck with Rhythmbox and Lord help me, I refuse to use Amarok.  If I try to hook up my external with 2TBs worth of tunes it wants to scan every single one!

So as of now, I've not been able to put anything on my Creative Zen since April and I'm pretty fed up with this!

:(

---

