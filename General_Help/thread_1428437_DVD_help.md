---
title: "DVD help"
date: 2010-03-12
forum: General Help
---

### Post by werdo1998 on 2010-03-12
Okay, I'm new to Ubuntu. So I have a few problems.  The first one is when I try to play a DVD  with movie player it tells me it can't read from resource.  So how can I get that to work?  Also I  have not  been able to find a player that will let me pause Divx films on the web. Any ideas?

---

### Post by werdo1998 on 2010-03-12
ANYONE? Ideas?

---

### Post by sandyd on 2010-03-12
> **werdo1998 said:**
> Okay, I'm new to Ubuntu. So I have a few problems.  The first one is when I try to play a DVD  with movie player it tells me it can't read from resource.  So how can I get that to work?  Also I  have not  been able to find a player that will let me pause Divx films on the web. Any ideas?

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install libdvdcss2 libdvdread4 libavcodec-unstripped-52 libavdevice-unstripped-52 libavfilter-unstripped-0 libavformat-unstripped-52 libswscale-unstripped-0 libpostproc-unstripped-51 ffmpeg lame libxine1-ffmpeg libamrwb3 libamrnb3 faac faad libquicktime1
```

for 32 bit
```

sudo apt-get install w32codecs

```

for 64 bit
```

sudo apt-get install w64codecs
```

please dont scream at me for adding non-free codecs, and all of the other codecs I could think of off the top of my mind.

---

### Post by mjitkop on 2010-03-12
What carlee said. :)

For more details, you can also check the Ubuntu Help page:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

---

### Post by werdo1998 on 2010-03-12
Thanks Carlee! I'll see if that does it.

---

### Post by werdo1998 on 2010-03-12
I was thinking maybe I didn't have the right driver for my DVD drive. Like I said. I'm new.

---

### Post by werdo1998 on 2010-03-12
P.S. I just found out I am a NERD!

---

### Post by werdo1998 on 2010-03-12
DVD problem solved. Now Lets see if the Divx thing is working.

---

### Post by werdo1998 on 2010-03-12
Nope. I still can't pause my Divx video when it's streaming from the web. When I had Windows on my PC I would use the Divx web player. Is there anything like that for Ubuntu?

---

### Post by Villiam on 2010-03-12
Well its not always like that the stream you are getting is divx. Someties or rather should i say most of the times its flv/swf and many others. RA is also one populaor format. typically the website you are getting stream from does offer a full player (with pause) feature. You will haveto me more specific about the divx streams you are downloading.

---

### Post by sandyd on 2010-03-12
> **werdo1998 said:**
> Nope. I still can't pause my Divx video when it's streaming from the web. When I had Windows on my PC I would use the Divx web player. Is there anything like that for Ubuntu?

what are you trying to stream?
got link?

---

### Post by werdo1998 on 2010-03-12
They are avi/divx files. like [www.stagevu.com]("http://www.stagevu.com") has. I know with  widows it writes a temp  part file on the disk while you are watching the video.  ...and that file is really just an avi file. Anyway some of the videos have  a low bandwith. So It's nice to pause them  so they can load. Being able to rewind would be nice too.

---

### Post by werdo1998 on 2010-03-12
Thanks for the help people.

---

### Post by werdo1998 on 2010-03-12
[www.stagevu.com](www.stagevu.com) . I can't pause or rewind the video . I could do that with Windows. Do you have any idea what I need to do?

---

### Post by qwerty2009 on 2010-03-12
i know this works (i use stagevu aswell) install " gecko-mediaplayer " from synaptic and uninstall " totem-mozilla " also from synaptic package manager :)

the only problem i find is that i cant always rewind or fastforward unless the movie is fully downloaded, you can pause without going to the start of the movie tho

---

### Post by werdo1998 on 2010-03-12
Thanks.

---

### Post by qwerty2009 on 2010-03-12
> **werdo1998 said:**
> Thanks.

 thats the one thing that annoid me about the default plugin for .avi when you press pause it would restart the video, hope uve got it sorted now anyway :P

---

### Post by werdo1998 on 2010-03-12
Yeah, qwerty that didn't work. It's still doing the same stuff.

---

### Post by werdo1998 on 2010-03-12
I wish Divx would make a browser plugin for ubuntu.

---

### Post by qwerty2009 on 2010-03-12
has the interface changed ? the only other thing i can think of, when playin the video click tools from the menu bar and select "manage content plug-ins" it should say divx media plugin is in use, from the drop bar next to it select "Geko Media Player" and restart firefox

---

### Post by qwerty2009 on 2010-03-12
> **werdo1998 said:**
> I wish Divx would make a browser plugin for ubuntu.

very unlikely to happen, divx only provides for windows and mac's because more regular users might purchase there premium package. as we're linux users(free) companies seem to think we wont pay for a decent application

---

### Post by werdo1998 on 2010-03-13
It's already got gecko there.

---

### Post by werdo1998 on 2010-03-13
..and no it's still the same as it was.

---

### Post by werdo1998 on 2010-03-13
I hope there is a special place in hell for Bill Gates!

---

### Post by qwerty2009 on 2010-03-13
whats actually the problem? are you not able to pause still? or isit just the rewind and forward problem?

you could try restarting your machine, somehow it might help

---

### Post by werdo1998 on 2010-03-13
Ok if I click on a video at [www.stagevu.com](www.stagevu.com). The video will play, but it's choppy, and I can't pause or rewind the video.

---

### Post by qwerty2009 on 2010-03-13
> **werdo1998 said:**
> Ok if I click on a video at [www.stagevu.com](www.stagevu.com). The video will play, but it's choppy, and I can't pause or rewind the video.

does it look anything like this? [IMG]http://fc04.deviantart.net/fs70/f/2010/071/e/a/hellping_sum1_out_by_SWOriginal.png[/IMG]

---

### Post by werdo1998 on 2010-03-13
No it does not. I tried the restart too. Didn't work.

---

### Post by qwerty2009 on 2010-03-13
check if you have "mozilla-mplayer" installed via synaptic package manager, if so completely remove it

---

### Post by werdo1998 on 2010-03-13
No mozilla-mplayer installed.

---

### Post by qwerty2009 on 2010-03-13
also check "xine-plugin" remove that if you have it, could you try and post a screenshot of your video playing so i can try and see what plugin you have installed

---

### Post by werdo1998 on 2010-03-13
Nope I don't have that one. Thanks for the help, and your time.

---

### Post by werdo1998 on 2010-03-13
How do I take a screenshot?

---

### Post by werdo1998 on 2010-03-13
I'm really new to ubuntu. I have only had it on my pc about a week.

---

### Post by qwerty2009 on 2010-03-13
you can either use the screen shot tool from accessories or by pushing print screen key on your keyboard, then attach the image from the bottem of your reply page

---

### Post by werdo1998 on 2010-03-13
[IMG]http://ubuntuforums.org/desktop/screenshot-1.png[/IMG]

---

### Post by werdo1998 on 2010-03-13
<img src="file:///home/user/Desktop/Screenshot.png"><br>

---

### Post by werdo1998 on 2010-03-13
Ugg how do I post the shot? LoL!<br>

---

### Post by qwerty2009 on 2010-03-13
click "new reply" then at the bottom of the page it says "manage attachments" go from there lol

---

### Post by werdo1998 on 2010-03-13
Here you go.

---

### Post by qwerty2009 on 2010-03-13
hmm, looks like  mplayer to me. open up gnome mplayer from  your sound and video menu, click on edit>prefrences then click on the mplayer tab and enable mplayer cache then click on the plugin tab and enable divx

---

### Post by werdo1998 on 2010-03-13
No change. I even restarted the browser.

---

### Post by qwerty2009 on 2010-03-13
im lost lol, the only thin i can suggest realy is installing karmic again update then install ubuntu-restricted-extras then  remove totem-mplayer and installing gecko-mplayer, course you cant do any of that if you have ur setup the way you like it. or wait till the next release of ubuntu (lucid 10.04) on april 29th, im sure someone els should be able to help if you leave the thread open

---

### Post by werdo1998 on 2010-03-13
Thanks for trying.

---

### Post by qwerty2009 on 2010-03-13
no problem, do you have ubuntu-restricted-extras installed at the moment if not i sugest you install them :D

---

### Post by werdo1998 on 2010-03-13
doing that now

---

### Post by werdo1998 on 2010-03-13
So here is what I have now after removing totem I still can't pause.

---

### Post by werdo1998 on 2010-03-13
Anyone?

---

### Post by qwerty2009 on 2010-03-13
hi, yeh thats geko-mplayer, once you have the movie playing you should be able to pause at anytime (adjust  the cache size through settings if it takes to long to play)

---

### Post by werdo1998 on 2010-03-14
Yup I'm getting there. Now to get it to rewind.

---

### Post by werdo1998 on 2010-03-14
It's working geat, other than the rewind thing!

---

