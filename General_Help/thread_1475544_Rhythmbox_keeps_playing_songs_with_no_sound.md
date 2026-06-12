---
title: "Rhythmbox keeps playing songs with no sound"
date: 2010-05-07
forum: General Help
---

### Post by altjx on 2010-05-07
For some reason, Rhythmbox will show itself playing a song (the notification in the top right corner) but I hear no sound. I can go to the application itself and see the play slider moving. I can't pause it or anything. I'm wondering if it's a bug in Rhythmbox itself. If I browse to the directory, and right click > Open with Rhythmbox, it works perfectly (although I still can't pause it)

Also, if I jump to another song, and then play the song it was playing silently, it works. Not sure why it does this. Hopefully someone else has this issue and has resolved it

I doubt it's the files themselves because I've been downloading all my songs from one site, and never had an issue in iTunes on a windows PC. It only does this to about 3 songs out of 164. It used to do this to only 2, but now it's doing it to 3 since the past few days when adding more songs.

---

### Post by garvinrick4 on 2010-05-07
[QUOTE=altjx;9252875]For some reason, Rhythmbox will show itself playing a song (the notification in the top right corner) but I hear no sound. I can go to the application itself and see the play slider moving. I can't pause it or anything. I'm wondering if it's a bug in Rhythmbox itself. If I browse to the directory, and right click > Open with Rhythmbox, it works perfectly (although I still can't pause it)

Also, if I jump to another song, and then play the song it was playing silently, it works. Not sure why it does this. Hopefully someone else has this issue and has resolved it

I doubt it's the files themselves because I've been downloading all my songs from one site, and never had an issue in iTunes on a windows PC. It only does this to about 3 songs out of 164. It used to do this to only 2, but now it's doing it to 3 since the past few days when adding more songs.[]


Make sure you got all your codecs installed come with ubuntu-restricted-extras package without qoutes. Run it in terminal if all loaded will not hurt anything if some are not loaded will install. Never had any problem with rhythmbox, if all other sound works it has worked as long as I got the g-streamer codecs installed.
If that does not work:
Also might as well 

sudo apt-get clean

Then reinstall rhythmbox from repositories to make sure you got a good copy.

---

### Post by altjx on 2010-05-07
same thing happens. installed ubuntu-restricted-extras, ran sudo apt-get clean, same thing. reinstalled rhythmbox after that, same thing. i try pausing the song, it still plays... >_< if i delete the 3 specific songs its doing it to, it will pick other random songs to do it to.

---

### Post by mbyrd11 on 2010-08-03
I am having the same problem with rhythmbox and totem. 
however I downloaded vlc from the repo's and plays sound fine.
I'm not sure why its doing this.

---

### Post by Cavsfan on 2010-08-03
Have you added the medibuntu repositories and keys?

---

### Post by Cavsfan on 2010-08-03
Install the medibuntu repositories and key ring to obtain the codecs for mp3s, wmas etc.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get 
--quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install 
medibuntu-keyring && sudo apt-get --quiet update
```[FONT=monospace]

[FONT=Verdana]Then there are a bunch of plugins you can install.
I will list mine if you want.[/FONT]

[FONT=Verdana]I have [/FONT][/FONT]Rhythmbox[FONT=monospace][FONT=Verdana] able to play just about anything even windows wma files.[/FONT]
[/FONT]

---

### Post by maciej234 on 2010-08-03
check under sound preferences.  There is a tab to check the sound preferences for a specific application, make sure rhythmbox is up.

---

### Post by Cavsfan on 2010-08-03
Then there is the gstreamer PPA and key...

---

### Post by Cavsfan on 2010-08-10
Edit your sources list - **gksudo gedit /etc/apt/sources.list**
Add this to the very bottom and then save the file:
```
#added gstreamer ppa
deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
```Then add the gstreamer key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  051D8B58
```Then update your system. 

Just don't let it do a partial update...

---

### Post by Jeanfrancoissven on 2010-08-20
I installed all the recommended codecs, reinstalled rhythmbox, but I still have the same problem here and it is just with some particular songs...

---

### Post by Cavsfan on 2010-08-20
> **Jeanfrancoissven said:**
> I installed all the recommended codecs, reinstalled rhythmbox, but I still have the same problem here and it is just with some particular songs...

What type of songs? Some MP3s, all MP3s. some WMAs, all WMAs...

---

### Post by Jeanfrancoissven on 2010-08-24
> **Cavsfan said:**
> What type of songs? Some MP3s, all MP3s. some WMAs, all WMAs...

With all types of songs, all different bit rates, ... I don't see a logical reason... I even converted a MP3 song that was acting strange into a ogg file, but it was the same again.
But now I **deactivated** the **crossfading** function and the problem dissapaered! It's not a real solution but the songs are acting normal now...

---

### Post by Cavsfan on 2010-08-24
This thread might be of interest to you. It allowed me to play WMA (windows media audio) files even!
I can play mp3, wma, wmv. and anything else I have tried.

[[color=blue]_http://ubuntuforums.org/showthread.php?t=1520301_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1520301)

---

### Post by KegHead on 2010-08-24
Hi!

Try system...preferences...sound... uncheck mute.

KegHead

---

### Post by ShakeyJake on 2010-08-29
Disabling crossfading does seem to stop the issue. But that's not really fixing it, that's just admitting defeat.

---

