---
title: "Linux equivalent of Windows Movie Maker?"
date: 2012-04-13
forum: General Help
---

### Post by Eirreann on 2012-04-13
So even though I've had to make the switch to Ubuntu, I still am trying to keep up with my YouTube channel ([www.youtube.com/generalnerevarine](www.youtube.com/generalnerevarine)), however for that I need a movie maker to piece together clips, add transitions, etc. etc.
So, what is Linux/Ubuntu's counterpart to Windows Movie Maker (what I used with Windows XP)?

Also, I need a programme with which I can record video with my webcam, anyone have any suggestions that work on Ubuntu 11.10?

Thanks in advance!

---

### Post by oboedad55 on 2012-04-13
> **Eirreann said:**
> So even though I've had to make the switch to Ubuntu, I still am trying to keep up with my YouTube channel ([www.youtube.com/generalnerevarine](www.youtube.com/generalnerevarine)), however for that I need a movie maker to piece together clips, add transitions, etc. etc.
So, what is Linux/Ubuntu's counterpart to Windows Movie Maker (what I used with Windows XP)?

Also, I need a programme with which I can record video with my webcam, anyone have any suggestions that work on Ubuntu 11.10?

Thanks in advance!

Software Center shows several things, openshot, kino, and LiVES. I have a friend who used the latter and likes it.

---

### Post by Eirreann on 2012-04-13
> **oboedad55 said:**
> Software Center shows several things, openshot, kino, and LiVES. I have a friend who used the latter and likes it.

LiVES... I'll look it up...
Do you have any suggestions for my webcam as well?

---

### Post by oboedad55 on 2012-04-13
> **Eirreann said:**
> LiVES... I'll look it up...
Do you have any suggestions for my webcam as well?

For what aspect of it? If it's for taking photos, etc. then try Cheese. I just did a search of "webcam" in Software Center.

---

### Post by Eirreann on 2012-04-13
> **oboedad55 said:**
> For what aspect of it? If it's for taking photos, etc. then try Cheese. I just did a search of "webcam" in Software Center.

For recording video; it's what I use to make the videos that I have on my YouTube channel (see first post...)

---

### Post by cody1233 on 2012-04-13
Try osalt.com.  They list a lot of open source alternatives to paid programs.  Haven't tried it with this, but it has been very useful to me.

---

### Post by pqwoerituytrueiwoq on 2012-04-13
[http://www.getdeb.net/app/WebcamStudio](http://www.getdeb.net/app/WebcamStudio)
how about that?
cheese can record videos or at least it could a few years ago

---

### Post by Eirreann on 2012-04-13
> **pqwoerituytrueiwoq said:**
> [http://www.getdeb.net/app/WebcamStudio](http://www.getdeb.net/app/WebcamStudio)
how about that?
cheese can record videos or at least it could a few years ago

Well Cheese has problems with 11.10; on my computer it won't even launch.  I'm downloading WebcamStudio right now; we'll see how it works...

Okay, it launches in Software Centre but says that the package isn't in my list of repositories; I take it I'll have to install a repo to get it?  If so, what and how?

---

### Post by daslinkard on 2012-04-13
I would also recommend Cheese for the web cam.  It's easy to install and pretty simple to use.

---

### Post by Eirreann on 2012-04-13
> **daslinkard said:**
> I would also recommend Cheese for the web cam.  It's easy to install and pretty simple to use.
Refer to my last post....

---

### Post by donhas on 2012-04-13
you could use winetricks to install movie player):P:popcorn:

---

### Post by daslinkard on 2012-04-13
If you look at the time stamps we practically posted at the same time....no way possible for me to refer to your last post;.

---

### Post by pqwoerituytrueiwoq on 2012-04-14
> **Eirreann said:**
> Well Cheese has problems with 11.10; on my computer it won't even launch.  I'm downloading WebcamStudio right now; we'll see how it works...

Okay, it launches in Software Centre but says that the package isn't in my list of repositories; I take it I'll have to install a repo to get it?  If so, what and how?
[http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb)
that deb file will add the software source

---

### Post by Eirreann on 2012-04-15
> **daslinkard said:**
> If you look at the time stamps we practically  posted at the same time....no way possible for me to refer to your last  post;.

Oh, sorry about that, mate; I didn't notice that.

> **pqwoerituytrueiwoq said:**
> [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1%7Egetdeb1_all.deb")
that deb file will add the software source

Thanks!  I'll give it a go and report back as to whether it works or not, haha!

---

### Post by Eirreann on 2012-04-15
> **pqwoerituytrueiwoq said:**
> [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1%7Egetdeb1_all.deb")
that deb file will add the software source

Okay, I just installed it and it won't boot when I click on the icon.  The loading screen will appear, and in System Monitor I see the process, but then the process ends and the loading screen disappears and I'm left with nothing.

What if I used Wine to install and use the software that is available on Logitech's website?  Would that work?

---

### Post by Herman on 2012-04-16
> I need a movie maker to piece together clips, add transitions, etc. etc.
So, what is Linux/Ubuntu's counterpart to Windows Movie Maker (what I used with Windows XP)?Kdenlive is great! [http://www.kdenlive.org/](http://www.kdenlive.org/) 

It's not simple to get started with, it is real professional heavy duty application so it has a lot of options you can work with. If you already have some video editing experience with a simpler program like Windows Movie Maker that would be a big help. There are lots of YouTubes about how to use KDenLive which are great for learning from. Once you get the hang of it you can produce excellent results.

It's fairly simple to install a working version of KDenLive but there are some special steps to follow. There is a version of KDenLive available in Ubuntu Software Center which used to work fine in previous version of Ubuntu, but in the Oneric Ocelot unfortunately it needs a newer version of some other software (MLT) to get KDenLive to work. 
The alternative that works is to follow the steps in the following linked web page: [Ubuntu Packages]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages") - KdenLive (how to add the sunab repository).

Actually it took me two updates after adding that repository to get my KdenLive working again.

I wasn't aware there are problems with cheese too.

---

### Post by Eirreann on 2012-04-16
> **Herman said:**
> Kdenlive is great! [http://www.kdenlive.org/](http://www.kdenlive.org/) 

It's not simple to get started with, it is real professional heavy duty application so it has a lot of options you can work with. If you already have some video editing experience with a simpler program like Windows Movie Maker that would be a big help. There are lots of YouTubes about how to use KDenLive which are great for learning from. Once you get the hang of it you can produce excellent results.

It's fairly simple to install a working version of KDenLive but there are some special steps to follow. There is a version of KDenLive available in Ubuntu Software Center which used to work fine in previous version of Ubuntu, but in the Oneric Ocelot unfortunately it needs a newer version of some other software (MLT) to get KDenLive to work. 
The alternative that works is to follow the steps in the following linked web page: [Ubuntu Packages]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages") - KdenLive (how to add the sunab repository).

Actually it took me two updates after adding that repository to get my KdenLive working again.

I wasn't aware there are problems with cheese too.

Thanks for the suggestion!  I'm currently using LiVES, though, and I'm liking it thus far, but I'll definitely keep that in mind!
And I think that I've resolved the problem  I was having with Cheese... although now any videos that I record with the webcam are super laggy... something to do with the way Cheese is auto-adjusting the lighting.
But thanks, all, for your help!

---

### Post by chickenPie4breakfast on 2012-04-17
> **Eirreann said:**
> Thanks for the suggestion!  I'm currently using LiVES, though, and I'm liking it thus far, but I'll definitely keep that in mind!
And I think that I've resolved the problem  I was having with Cheese... although now any videos that I record with the webcam are super laggy... something to do with the way Cheese is auto-adjusting the lighting.
But thanks, all, for your help!

As for Video Editors - I tried (in order of features)

Pitivi  pretty limited to simple stuff but great selection of rendering options (the best for rendering)

Openshot  more features than     Pitivi but the keyframing was too limited for me - you only get 2 keyframes per clip!

Kdenlive  This is the one I am using - nice balance between ease of use and features and it's under heavy development - version 8 is much more stable. I actually had no  problems at all installing this from synaptic - unlike a previous poster.

Cinerella   Most features - a bit more buggy for me interface wise but I sort of liked it - I stopped using it though because having many features counts for nothing when it was so so fussy about what videos it would open.

LIVEs is the only one I  havent tried yet.

---

### Post by Eirreann on 2012-04-17
> **chickenPie4breakfast said:**
> As for Video Editors - I tried (in order of features)

Pitivi  pretty limited to simple stuff but great selection of rendering options (the best for rendering)

Openshot  more features than     Pitivi but the keyframing was too limited for me - you only get 2 keyframes per clip!

Kdenlive  This is the one I am using - nice balance between ease of use and features and it's under heavy development - version 8 is much more stable. I actually had no  problems at all installing this from synaptic - unlike a previous poster.

Cinerella   Most features - a bit more buggy for me interface wise but I sort of liked it - I stopped using it though because having many features counts for nothing when it was so so fussy about what videos it would open.

LIVEs is the only one I  havent tried yet.

Those all sound good, and I'll give Kdenlive a try!  LiVES is pretty good, thus far, but it could use some more features, haha!  But thanks for the suggestions!

---

