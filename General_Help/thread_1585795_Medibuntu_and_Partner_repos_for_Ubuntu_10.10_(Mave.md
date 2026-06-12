---
title: "Medibuntu and Partner repos for Ubuntu 10.10 (Maverick)"
date: 2010-10-01
forum: General Help
---

### Post by moma on 2010-10-01
Hello,

I would like to test Ubuntu 10.10 RC with all available software. But Medibuntu and Partner repositories are not yet available to Maverick. 

Medibuntu repo:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)   (no Mav3rick yet)
This contains codecs, google-earth and more.

Canonical's Partner repo:
[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/)
You can activate this from Software Sources (in the Synaptic).
This should give us Sun's official Java 6 runtime.
OpenJDK is good but some rare applications still needs Sun's (Oracle's) Java.

When will these repositories open for Maverick?

---

### Post by plucky on 2010-10-01
> **moma said:**
> Hello,

I would like to test Ubuntu 10.10 RC with all available software. But Medibuntu and Partner repositories are not yet available to Maverick. 

Medibuntu repo:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)   (no Mav3rick yet)
This contains codecs, google-earth and more.

Canonical's Partner repo:
[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/)
You can activate this from Software Sources (in the Synaptic).
This should provide Sun's official Java 6 runtime.
OpenJDK is good but some rare applications still needs Sun's (Oracle's) Java.

When will these repositories open for Maverick?

You might get an answer at [Maverick Meerkat Testing and Discussion Forum](http://ubuntuforums.org/forumdisplay.php?f=385) or get a Moderator to move this thread to that forum.

Good Luck

---

### Post by coffeecat on 2010-10-01
With earlier versions of Ubuntu (Lucid and Karmic at least), Medibuntu put up version-specific repositories when they were still in testing. It's odd that they haven't yet organised a Maverick repository. I don't know why. What you could do is to download the packages you want from the Lucid repository - people in the testing subforum have been doing this already - and install them manually. You'll soon be told if there are dependencies to be met. Then, when and if Medibuntu adds Maverick, you can enable this in the normal way and the package manager will update any packages automatically when updates become available. 

With the partner repo, it's interesting that a Maverick-specific package for acroread is already available. If I remember correctly I couldn't get acroread for Lucid and Karmic until they went final. But for sun java, if you navigate from the link you posted to [http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/](http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/) you'll see that the sun-java packages are not version-specific. I would imagine that if you download the ones you want and install them manually as for the medibuntu packages, the package manager will take care of updates for you when sun-java is added to the Maverick partner repo.

---

### Post by moma on 2010-10-01
Thanks for the answers.

There is a private PPA for Maverick and Java 6.
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html)
Let's hope the Canonical's Partner repo opens up soon.

---

### Post by andrew.46 on 2010-10-03
Hi coffeecat,

> **coffeecat said:**
>  Medibuntu put up version-specific repositories when they were still in testing. It's odd that they haven't yet organised a Maverick repository. I don't know why.

I asked a while back on #medibuntu on Freenode and I believe there is some 'reconfiguration' going on that will probably mean that the repository will not be ready until some time *after* the release of Maverick. Hopefully things will come together a little sooner than that.

Andrew

---

### Post by coffeecat on 2010-10-04
> **andrew.46 said:**
> Hi coffeecat,

I asked a while back on #medibuntu on Freenode and I believe there is some 'reconfiguration' going on that will probably mean that the repository will not be ready until some time *after* the release of Maverick. Hopefully things will come together a little sooner than that.

Andrew

Hopefully, indeed! If there is a significant delay with the Maverick Medibuntu repository there are going to be a lot of unhappy people after next Sunday, thinking that they can't install all their goodies.

Thanks for the information.

---

### Post by andreino on 2010-10-06
without having to add any in our Ubuntu Repository


for codec **w32codecs **/ **w64codecs** 
[COLOR=#ff0000]**Ubuntu 10.10 Maverick i386**[/COLOR]

**wget [http://dl.dropbox.com/u/964512/codec/codec_maverick__i386](http://dl.dropbox.com/u/964512/codec/codec_maverick__i386)**

**chmod +x codec_maverick__i386**

**./codec_maverick__i386**
[COLOR=#ff0000]
**for Ubuntu 10.10 Maverick amd64**[/COLOR]

**wget [http://dl.dropbox.com/u/964512/codec/codec_maverick_amd64](http://dl.dropbox.com/u/964512/codec/codec_maverick_amd64)**

**chmod +x codec_maverick_amd64**

**./codec_maverick_amd64**

---

### Post by Brownout on 2010-10-09
> **andreino said:**
> without having to add any in our Ubuntu Repository
....

Installing software from random sources is not a good idea.

---

### Post by unrater on 2010-10-09
They should put now the maverick repo! even if it was a link to the lucid!

---

### Post by andrew.46 on 2010-10-09
Hi unrater,

> **unrater said:**
> They should put now the maverick repo! even if it was a link to the lucid!

I would be wary of telling the Medibuntu people what they should and should not do as they are all volunteers putting this together on their own time. Having said that you will see there is a countdown on their page that suggests they will have the repository ready for the release:

[https://launchpad.net/medibuntu/maverick](https://launchpad.net/medibuntu/maverick)

Andrew

---

### Post by inameiname on 2010-10-10
I was told just now that the Maverick version of Medibuntu has a release date of today. Hopefully it won't be too much longer, as Maverick is out now.

---

### Post by f.pier on 2010-10-10
Still not working to me....

---

### Post by lostnforest on 2010-10-10
> **andrew.46 said:**
> Hi unrater,



I would be wary of telling the Medibuntu people what they should and should not do as they are all volunteers putting this together on their own time. Having said that you will see there is a countdown on their page that suggests they will have the repository ready for the release:

[https://launchpad.net/medibuntu/maverick](https://launchpad.net/medibuntu/maverick)

Andrew

Yes. we should be grateful for all the work they do, especially considering that the normal release date would be at the end of this month - not three weeks early.

---

### Post by pbvijay on 2010-10-10
[@andreino]("http://ubuntu-ky.ubuntuforums.org/member.php?u=1005997") thank you very much its resolved my issue
thank you [andreino]("http://ubuntu-ky.ubuntuforums.org/member.php?u=1005997")

---

### Post by unrater on 2010-10-11
> **andrew.46 said:**
> Hi unrater,



I would be wary of telling the Medibuntu people what they should and should not do as they are all volunteers putting this together on their own time. Having said that you will see there is a countdown on their page that suggests they will have the repository ready for the release:

[https://launchpad.net/medibuntu/maverick](https://launchpad.net/medibuntu/maverick)

Andrew

I know they are volunteers and we are thank for there work. But linking to the lucid version would be simple, and temporarily solve the problem!

---

### Post by f.pier on 2010-10-11
It seems it has been released but I have always the same problem...

---

### Post by coffeecat on 2010-10-11
> **f.pier said:**
> It seems it has been released but I have always the same problem...

Indeed, the Maverick Medibuntu repository seems to be up. What problem? If you need help, you need to be specific.

---

### Post by moma on 2010-10-12
Follow this ([http://www.futuredesktop.org](http://www.futuredesktop.org)) guide.
And look for [step 6...]("http://www.futuredesktop.org/#step6") and beyond.

It will also tell you howto install the very latest version of Google Earth. Google Earth is not in the Medibuntu repo anymore. Look for [step 7b]("http://www.futuredesktop.org/#step7").

Case solved. Thread closed. Thanks to all.

---

