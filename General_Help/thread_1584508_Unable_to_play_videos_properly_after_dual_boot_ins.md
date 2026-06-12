---
title: "Unable to play videos properly after dual boot install"
date: 2010-09-29
forum: General Help
---

### Post by rmcellig on 2010-09-29
I just installed Ubuntu 10.04 on my iMac. I can play videos from Youtube no problem but when I try and play avi, mov or any other video format, the Movie Player quickly opens and closes. When I try with VLC player, I see the player bar but no video. When I try with SMplayer, I can watch the video but when I go full screen, the movie doesn't take up the whole area of the screen. It stays at the same small size.

What do I need to do to make this right? I installed the Ubuntu Restricted Extras. Did I miss something?

---

### Post by leclerc65 on 2010-09-29
Follow this [guide]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by rmcellig on 2010-09-29
Thanks so much!

I remember doing this a while back in a previous install but I keep forgetting to go to this site when I do a new install.

---

### Post by Blook on 2010-09-29
Have you installed the "restricted extras" package yet?I think that may be the cause for your problem!

---

### Post by rmcellig on 2010-09-29
Yes I installed the Ubuntu restricted Extras as well as restart my computer. When I play a video with VLC player, no video at all apears. When I play with the Movie player, the movie plays but as soon as I resize the movie or go full screen, movie player quits. Is this a graphic card problem? I'm not sure what is going on here.

I installed Ubuntu 10.04 on my iMac dual boot is that has anything to do with this.

---

### Post by leclerc65 on 2010-09-30
How about the w32codecs (or the w64codecs) ?

I usually follow this guide, up to the end then do

sudo apt-get install w32codecs non-free-codecs

sudo apt-get install mplayer

sudo apt-get install vlc

then I dl the deb from RealPlayer and install Realplayer.

Then the only problem I have is WMV9 audio codec from You Know Who.

---

### Post by rmcellig on 2010-09-30
Is there a command I can paste in the terminal that will tell me if I have all of those codecs? I can post back the result.

---

### Post by Cavsfan on 2010-09-30
Add this to your sources: [B]gksudo gedit /etc/apt/sources.list
[/B]Then add these 2 lines to the bottom:

```
deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main 
#deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main 
```Then to add the key type this into a terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 051D8B58
```

---

### Post by Cavsfan on 2010-09-30
Then enter **sudo apt-get update && sudo apt-get upgrade**

---

### Post by Cavsfan on 2010-09-30
With these I can play a WMA file in Rythmbox (Windows Media Audio file)! :P

---

### Post by rmcellig on 2010-09-30
I am new to all this so I need a bit more detailed explanation. Attched is what I have in my Sources already.

---

### Post by Cavsfan on 2010-09-30
> **rmcellig said:**
> I am new to all this so I need a bit more detailed explanation. Attched is what I have in my Sources already.

Click on **Applications** > **Accessories** > **Terminal** and enter this command **gksudo gedit /etc/apt/sources.list **
That will open up your sources list as a text file after you enter your password.

Then simply copy and paste this into the very bottom of that text file:

```
deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main 
#deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main

```
The # sign comments out that line as it is for source and you won't need it.

Then you need to add the key for the above repository so you don't get errors:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 051D8B58
```

Then enter this into the terminal to get the updates:
```
sudo apt-get update && sudo apt-get upgrade
```

The && just separates the 2 commands.

---

### Post by rmcellig on 2010-09-30
Thanks. I just did all that and it still doesn't work. Do I have to restart?

---

### Post by Cavsfan on 2010-09-30
> **rmcellig said:**
> Thanks. I just did all that and it still doesn't work. Do I have to restart?

Yes, it probably wouldn't hurt.

---

### Post by rmcellig on 2010-09-30
There is something I hav to mention and you might find this odd. I have an iMac. I have been using Macs since 1988. I really love using the Mac until I discovered Ubuntu. Now I find myself spending more time in Ubuntu and less on the Mac. That's why I have a dual boot setup now. There are three issues that I really need to get resolved and I have the feeling that it is much harder getting Ubuntu to work on a Mac than it is on a PC. Running in VMWare Fusion is fine but running Ubuntu Natively at least for me has been a pain to get going.

My three issues are:

1. Unable to record from Line In. Recording from the built in Mic is fine but line in doesn't work. I need this to work because I work at a radio station and use the radio attached to my Mac to record shows.

2. Getting the built in webcam on the Mac to work. At the moment it doesn't work at all.

3. The ability to play videos. I don't know what is going on here. I tried what you suggested but so far nothing is working. If there is more information that you need, let me know.

---

### Post by Cavsfan on 2010-09-30
> **rmcellig said:**
> There is something I hav to mention and you might find this odd. I have an iMac. I have been using Macs since 1988. I really love using the Mac until I discovered Ubuntu. Now I find myself spending more time in Ubuntu and less on the Mac. That's why I have a dual boot setup now. There are three issues that I really need to get resolved and I have the feeling that it is much harder getting Ubuntu to work on a Mac than it is on a PC. Running in VMWare Fusion is fine but running Ubuntu Natively at least for me has been a pain to get going.

My three issues are:

1. Unable to record from Line In. Recording from the built in Mic is fine but line in doesn't work. I need this to work because I work at a radio station and use the radio attached to my Mac to record shows.

2. Getting the built in webcam on the Mac to work. At the moment it doesn't work at all.

3. The ability to play videos. I don't know what is going on here. I tried what you suggested but so far nothing is working. If there is more information that you need, let me know.

Let me do some looking around...

---

### Post by Cavsfan on 2010-09-30
There is an area of this forum dedicated for Apple users! I would be pretty sure that some people in there will be able to help you.:)
[[COLOR=blue]_Apple Users_[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=328")

This is a very good forum and you will find someone that can help you in there. I am just not at all familiar with MACs.

---

### Post by rmcellig on 2010-09-30
I have some posts already in there. I just tried opening a video and still the same problem. Could it have anything to do with the video card that is in my Mac (Nvidia)? I installed the Nvidia drivers.

---

### Post by Cavsfan on 2010-09-30
> **rmcellig said:**
> I have some posts already in there. I just tried opening a video and still the same problem. Could it have anything to do with the video card that is in my Mac (Nvidia)? I installed the Nvidia drivers.

I have an nVidia card too, but I really don't know too much about Macs. 
Did you install the sugggested one in **System** > **Administration** > **Hardware Drivers**?
There is one that you have to activate if you want open gl.

---

### Post by rmcellig on 2010-09-30
Yes I did that. You have Ubuntu on a PC dual booting with Windows?

---

### Post by Cavsfan on 2010-09-30
> **rmcellig said:**
> Yes I did that. You have Ubuntu on a PC dual booting with Windows?

Yes. You might want to look around on this page
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

There seems a lot of video and audio info on there.

---

### Post by rmcellig on 2010-09-30
I started up from my xubuntu live CD and all the videos played great in full screen and just regularly. I was asked to install some missing plugins and after that no problem. When I start back into Ubuntu, the problems are still there. Is there some kind of log file I can post that may indicate what is going on?

---

### Post by rmcellig on 2010-10-01
I am starting to think there is something seriously wrong with my 10.04 install. When I xtarted up from the Ubuntu 10.04 live CD, I tried to watch a movie and the attached message appeared. I was unable to install these plugins. The Xubuntu 10.04 live CD allowed me to. What gives and where do I go from here :(

---

### Post by Cavsfan on 2010-10-01
Have you installed the Medibuntu Repositories? I think we forgot that one maybe.
Which would be most of the problem. ](*,)

This command should be run in the Terminal (Applications &#8594; Accessories &#8594; Terminal):

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by Cavsfan on 2010-10-01
Sorry **leclerc65** I didn't notice that you had mentioned the above back on page one. 
Did you already get the Medibuntu sources added?

If not, that one single command I posted above is from the same guide and will install it.

After you have that added to your sources list, 
what do you see when you enter these 2 commands into a terminal?
**sudo apt-get update**
**sudo apt-get upgrade**

If you haven't done all of this already, it should be asking you to enter "y" to install a bunch of stuff.

---

### Post by rmcellig on 2010-10-01
I upgraded to release candidate 10.10 and as far as watching videos, everything works fine now in VLC Player, Totem Movie player as well as SMplayer.

One down three to go as far as continuing problems go.

---

### Post by leclerc65 on 2010-10-02
@Cavsfan

I follow the guide without any problem, except that I cannot play videos with WMV 9 codec (the video will play, but the sound is muted).

---

### Post by Cavsfan on 2010-10-02
I finally found it! This is the thread that got my WMA files to work and before they wouldn't.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1520301_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1520301")

That aught to fix everything. I think I rebooted after doing all of the updates and then it worked, strangely enough.

---

