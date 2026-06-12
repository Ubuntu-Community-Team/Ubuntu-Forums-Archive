---
title: "Who can watch the following streams with seeking in Firefox, in Lucid?"
date: 2010-05-06
forum: General Help
---

### Post by kimangroo on 2010-05-06
I've been posting about this in another thread but the problem is different now so I thought I'd start a new thread.

I'd like to watch a bunch of mms streams in Firefox with seeking enabled. I've tried a number of plugins ([for full and boring story see this post]("http://ubuntuforums.org/showpost.php?p=9249976&postcount=10")) but although at one moment I had a workaround going for some very strange reason it's not working again.

I have to say it's driving me just a little crazy.

So I thought I'd ask who can see the following streams in FF with _seeking enabled_. If you can could you tell me how you set up your plugins different from the clean Lucid install.

[http://www.thalassa.france3.fr/?page...&id=1&play=yes](http://www.thalassa.france3.fr/?page...&id=1&play=yes)
[http://www.nhk.or.jp/rj/asx/jp/japanese.asx](http://www.nhk.or.jp/rj/asx/jp/japanese.asx)
[http://news.tbs.co.jp/news_mainprogram/asx/1_nb.asx](http://news.tbs.co.jp/news_mainprogram/asx/1_nb.asx)

Thanks a million.

---

### Post by sgage on 2010-05-07
Well, all three streams played for me, including seeking, in FF. The "bad" news is that I didn't do anything special to enable it that I can think of. I installed ubuntu-restricted extras - that's about it.

---

### Post by kimangroo on 2010-05-07
Such a short post and yet such a welcome one! Thanks so much for bothering to check it out for me. Luckily it was "bad" news at all!

I've put hours and hours of googling and forum trawling into this and somehow seem to have completely missed this ubuntu-restricted-extras package. I've already downloaded loads of other restricted codec packages and enabled strange repositories etc but they didn't help.

I installed the ubuntu-restricted-extras and can now watch the three streams with seeking. That was almost annoyingly simple! (at first I thought sound wasn't working, but for some reason it's just that the plugins now load with the volume control on the lowest setting).

The only fly in the ointment is that there are still a couple of other streams I'm having problems with. I thought the three I had posted would cover all stream types but apparently not. I'm guessing it's probably a conflict with some codec package I installed previously. Do you think you check to see whether you can see the streams correctly?

I can't post direct links for these it seems. They are on this page:

[http://www.rusnovosti.ru/online/](http://www.rusnovosti.ru/online/)
The green loudspeaker icon one is radio only and seems to be flash or something and I have had occasional problems with it on windows too so might not be an ubuntu problem.

The webcam icon below should definitely work. I just get a black screen. If I open it from the plugin with vlc I get video but no audio. Finally if I copy and paste and open the mms directly in vlc it works fine!

I'm guessing I've messed something up with the constant installing and uninstalling of the millions of packages from synaptic.

Again, thanks, this problem has been driving me crazy!

---

### Post by sgage on 2010-05-08
The streams on the page you linked to are Windows Media, and don't play inline for me, either. I'm not sure if there is a codec available for that - there may be, if you poke around.

Glad you're able to see most of your streams, though. The intro sequence to that "Thalassa" stream was very cool!

- sgage

---

### Post by Dilutu on 2010-05-08
For me,they play only with totem plugin. I tried mplayer plugin and could not get them to play.To get good quality,I had to get to gstreamer-properties and switch video to use xv.I often watch "http://www.thalassa.france3.fr/". The webcam icon on your link works ok . Its another story for flash content. Youtube is ok here but others like "http://www.tou.tv/decouverte/S2009E34" drop so many frames.....

---

### Post by kimangroo on 2010-05-10
Thanks again for the feedback, good to know it's not just me. The most important streams are working so I'll stick with them for now until I can be bothered to have another go fiddling about with different plugins.

Thalassa is an excellent program about all things related to the sea and coastal countries, if you understand French I highly recommend it. There was a great episode the other week about the intelligence of octopuses and their problem solving abilities, apparently some of the octopuses would regularly escape from the tanks and then follow the researchers about to see what they were doing.

---

### Post by kimangroo on 2010-06-01
I've never had much luck in my attempts to migrate to Linux, whether it be Mandriva, Suse or now Ubuntu. Things always seem to work at first and then gradually go wrong.

I haven't installed or done anything to my system that I'm aware of and yet now the above streams that I could view fine before are all behaving buggily. I have to refresh the page a random number of times before I can get the stream to play, the quality is terrible and seeking more often than not doesn't work anymore; it starts playing a few minutes and then cuts out, or just cuts out straight away.

:confused:

It is truly terrible the amount of time I've wasted on this problem. There are so many things that I dislike about XP, and so many great things about Linux, but the sad truth is that I find myself spending far too much time just trying to get things to "work" on Linux, that I never have had to do with XP. 5 years ago it used to be driver hassles, now it seems to be internet plugins/compatibility. I'm not sure it's worth it.

:(

---

### Post by hansdown on 2010-06-01
Hi kimangroo.

Install 

```
exine-plugin
```

and 

```
exine-ui
```

Exine plays these smoothly.

---

