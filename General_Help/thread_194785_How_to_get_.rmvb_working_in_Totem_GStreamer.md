---
title: "How to get .rmvb working in Totem GStreamer?"
date: 2006-06-11
forum: General Help
---

### Post by t_huankiat on 2006-06-11
Hi guys,
I am a newbie to Ubuntu/Linux. I'm glad that I chose Ubuntu as my starting point. The upgrade to Dapper last week was painless. Well except probably the time took to download the new distro took me a while that is;) 

OK long question short, I can't get my default totem to play files associated with rmvb. I googled and was able to find this useful [site]("https://wiki.ubuntu.com/RestrictedFormats"). From the instructions, I was able to get my totem-gstreamer to play .avi, .mpg, .mp3 etc after followed the [Ubuntu Media Player]("https://wiki.ubuntu.com/RestrictedFormats#head-1da38d0e9087e87c10439e6ff124fb9b41e2be27") section and the [Windows Codecs]("https://wiki.ubuntu.com/RestrictedFormats#head-1da38d0e9087e87c10439e6ff124fb9b41e2be27") section. The few glitches were:
I couldnt' install gstreamer0.10-plugins-ugly-multiverse package directly because it said I was missing the liblame0 library. I googled and installed the package and installed the multiverse package successfully.
I couldn't find gstreamer0.10-pitfdll package so I repeated the same steps to find the package manually and installed the package.

I tried to open the rmvb file from totem. The only improvement was instead of showing an error message telling me that I don't have the codec installed, it's showing some sound. But the sound just sounded as if you're watching an action movie in slow motion. For example a simple sentence of "Don't shoot, he's one of us" would probably sounds like "DDDDDDDDoooooonnnnnn'tttttt ssssshhhhhoooottttt, hhhhhheeeee'ssssss oooooonnnnnneeeee oooooooffffffff uuuuuuussssss" if I have the patience to really listen to it... It just doesn't sound right. and the screen is just blank.

So I did a search again and I found [this]("http://ubuntuforums.org/showthread.php?t=186257&page=2&highlight=rmvb").
I read through the whole thread. The problem doesn't seem like mine, but I tried the method posted on the last post anyways. No good either.

I'm gradually switching my activities on Windows to Ubuntu. and watching those tv series e.g. Grey's Anatomy or Lost *cough*downloaded*cough* is part of what I do when I lay back at home!

I have no idea how to get it fix. Please help!

---

### Post by t_huankiat on 2006-06-16
Hi guys,
I have been trying for the past few days, no luck so far. Is it a mission impossible for this to work or I'm just not on the right direction?

My plan is to try again until this weekend. If by that time it doesn't work still, I'll probably switch to Totem-xine or mplayer:-(

---

### Post by stinerman on 2006-06-16
I've never gotten a single movie other than something encoded with Ogg Theora to run under Totem.  It simply hasn't worked for me.

I like mplayer, myself.  It has played every last file I've asked it to.

The downside is that you have to use some proprietary files to get full support for some codecs (WMV for example).  I tend to stay away from anything that isn't Free, but when it comes to simply watching a movie or listening to some music, and there is no Free codec/library available, I don't mind.  If it doesn't bother you, then you'll be in the clear.

---

### Post by Hairy_Palms on 2006-06-16
unfortunately ive been unable to get any gstreamer based thing to play nicely with any real files, i use totem-xine though and it plays then fine :)

---

### Post by t_huankiat on 2006-06-16
[QUOTE=stinerman][/QUOTE]
Hi stinerman,
I'm able to play mp3, mpg and all the avion totem-gstreamer without problem after following the Restricted Format articel and installed the win32codecs.

So I guess nobody actually been able to play rmvb on totem gstreamer? I guess I should quit wasting time and install the totem-xine instead?:?:

---

### Post by stinerman on 2006-06-17
It'd be your best bet.  I'm not too familiar with xine, but as far as I know, its a bit more mature than the gstreamer framework.

Best of luck.

---

### Post by t_huankiat on 2006-06-17
I'm a Linux newbie, but this question keeps me wondering then...
since totem-xine is more mature, why is the default media player for dapper totem-gstreamer, and why the poll indicates that users prefer gstreamer better:?:

---

### Post by stinerman on 2006-06-17
Totem is a front-end that can be used with different backend video players.  I think gstreamer is the default because its part of the GNOME project, while xine isn't (don't quote me on that).

As far as who likes it better ... that's subjective, so I don't have much insight into that.  Perhaps totem is better integrated to gstreamer than xine.

---

### Post by hyperair on 2007-10-22
Xine does depend upon the w32codecs package for playing rmvb files if I'm not mistaken, as does mplayer and Gstreamer. From this I think we can conclude that both Xine and Gstreamer are of little difference when it comes to the end-user.

---

### Post by Ocxic on 2008-01-01
SOLVED!!!!  Go here and follow these instructions and install the proper codec package and you'll be able to play .rmvb files in mplayer like normal.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jobkingori on 2008-05-15
Downloaded the w32codecs_20071007-0medibuntu1_i386.deb from some site (don't remember the link) but still couldn't get the .rmvb files to play on Totem but i finally figured out why...

Somehow, its like the w32codecs_20071007-0medibuntu1_i386.deb pack requires ALL the gstreamer packages installed for it to work properly...so just go to Synaptic n install gstreamer bad...good...ugly...ALL of them except the docs or dev files of course then now with the w32codecs Totem will be able to play rmvb flawlessly.

I'm a linux newbie so i hope i've helped...

---

### Post by hyperair on 2008-05-15
> **jobkingori said:**
> Downloaded the w32codecs_20071007-0medibuntu1_i386.deb from some site (don't remember the link) but still couldn't get the .rmvb files to play on Totem but i finally figured out why...

Somehow, its like the w32codecs_20071007-0medibuntu1_i386.deb pack requires ALL the gstreamer packages installed for it to work properly...so just go to Synaptic n install gstreamer bad...good...ugly...ALL of them except the docs or dev files of course then now with the w32codecs Totem will be able to play rmvb flawlessly.

I'm a linux newbie so i hope i've helped...

Not quite right. The package that's needed for GStreamer to use w32codecs is gstreamer0.10-pitfdll.

---

