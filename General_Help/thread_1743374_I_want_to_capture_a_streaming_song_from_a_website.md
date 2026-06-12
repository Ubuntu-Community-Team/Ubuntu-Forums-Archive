---
title: "I want to capture a streaming song from a website"
date: 2011-04-29
forum: General Help
---

### Post by ClientAlive on 2011-04-29
Hi,

I was recently turned on to grooveshark by a friend and I would like to capture a couple of the songs from there. Can anyone suggest a good app that can do that? I was told about cplayer by someone but I'm not sure if it does that/ has that feature. Also, I read that cplayer uses some other way of using the hardware on my computer (there's a name for it but I don't remember). I'm worried about putting something on here and having problems with sound with other things on my computer too.

Basically I'd just like to find something I can use to do this though. Something easy to use.

Thanks
------------------------

By the way, I'm using Ubuntu 11.04

---

### Post by hwttdz on 2011-04-29
You can record off your soundcard with gnome-sound-recorder, and there are a bunch of firefox addons that will allow you to download media files from various websites (downloadhelper being my poison).  

<required disclaimer about being responsible for your own actions and not doing anything stupid>

---

### Post by ClientAlive on 2011-04-29
> **hwttdz said:**
> You can record off your soundcard with gnome-sound-recorder, and there are a bunch of firefox addons that will allow you to download media files from various websites (downloadhelper being my poison).  

<required disclaimer about being responsible for your own actions and not doing anything stupid>

Yes. I understand. Thank you. I'll check it out. Do you know how this works within the app though? What I mean is, the setting of the app and how you find that feature?

Thanks. I'm looking into this gnome-sound-recorder now too.

---

### Post by ClientAlive on 2011-04-29
I have something called "Sound Recorder" on my computer - it's icon shows a microphone. I don't see how to use it for this though. I'm not sure if this is the right thing. If I put "gnome sound" into synaptic I see a couple things that are already installed but not sure if this is the right stuff. One is: "gnome-media" I think that's the one that has sound recorder with it (installed already). The other ones are: "gnome-session-canberra", "libao4" and "libao-common".

What do I need to do?

Thanks

---

### Post by scouser73 on 2011-04-29
If you know the name of the artist and the song then search for it in YouTube and then use this website to convert the video to audio: [http://www.youtube-mp3.org/](http://www.youtube-mp3.org/)

The site also offers addons for both Firefox and Google Chrome.

---

### Post by buddhuu on 2011-04-29
OutRec is a very simple prog that will record from the soundcard. I use it with Spotify and Grooveshark, no prob.

[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

---

### Post by ClientAlive on 2011-04-29
> **buddhuu said:**
> OutRec is a very simple prog that will record from the soundcard. I use it with Spotify and Grooveshark, no prob.

[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)


Tried to add the repository for outrec through the teminal. The website has the code for it on the website so I copy and pasted that into the terminal. Seemed to go fine based on the response I got after that but then, when doing "sudo apt-get update" I get an error message. I don't understand what I need to do to make this happen. There's at least a half-dozen dependancies listed for this thing on the website and I was hoping to avoid all kinds of dependency drama trying to get this thing.

Here is the output I get after pasting and running the code given on the website:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 2E50182DFB531D953EEAA6C6393493DA71CEA1D7
gpg: requesting key 71CEA1D7 from hkp server keyserver.ubuntu.com
gpg: key 71CEA1D7: public key "Launchpad outrec" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

And here is the output I get that regards outrec repository after doing "sudo apt-get update":

```
W: Failed to fetch http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


Of course, if I put outrec in the search field of synaptic I get no results.

Can anyone help me sort this out?

Thanks
-------------------

Edit: Is it because I'm using Natty and Natty is so newly released?

---

### Post by ClientAlive on 2011-04-30
I started digging around on the web and decided to try Exail and streamripper but when I enter the (correct) url for the site a want to listen to I am given an error message from Exail saying I am missing a codec in gstreamer. I did a search in synaptic for "gstreamer" and see there are a lot of codecs for it. Also, Exail is not really giving me much to go on when I don't know anything about the subject.

Does anyone know which codec it may be complaining about?

Thanks in advance.

Oh, by the way, here's where I got the idea to use these:  [http://www.associatedcontent.com/article/703069/how_to_record_streaming_audio_in_linux_pg2.html?cat=15](http://www.associatedcontent.com/article/703069/how_to_record_streaming_audio_in_linux_pg2.html?cat=15)

Pages 2 and 3 talk about this option. Sounds easy except for the little snaffoo' I've run into here.

Thanks.

---

### Post by SeijiSensei on 2012-07-21
I installed [outRec]("http://outrec.sourceforge.net/") today after a search for methods to record streams took me to this page.  OutRec is a simple application that does exactly what it's supposed to -- record the output of the audio system to the hard drive.  However it takes a bit of work to install.  

It doesn't appear to be in any of the Ubuntu repositories.  There's a PPA link on the outRec home page:

```
sudo add-apt-repository ppa:techm3/outre
```

Like ClientAlive, this didn't work for me.  I opened the repository URL with a browser and discovered there is only a version for Lucid.  So the next step was to edit, as root with sudo, the file /etc/apt/sources.lists.d/techm3-outrec-precise.list.  (If you're using a different version of Ubuntu, you'll see a different name from "precise".)  In that file, replace the name of your version ("hardy", "precise", etc.) with "lucid", then save the file.  

Now there's just one more obstacle in your path.  You'd think that the package would be called "outrec", but it's actually named "outrecen", I guess because it's the English version.  So after you've edited your sources, run these commands:

```

sudo apt-get update
sudo apt-get install outrecen

```

OutRec appears in the "Multimedia" category in my Kubuntu menu.  Two tips.  If you don't click either the MP3 or the OGG buttons, it will record in the default WAV format.  Second, all the recordings are stored in /home/username/outRec/.

I've been looking for a simple application to let me record my vinyl albums to the hard drive.  The only thing I found was Audacity which was way overkill for my needs.  OutRec looks like just the solution for that task as well!

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

