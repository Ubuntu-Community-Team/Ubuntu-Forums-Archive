---
title: "Is mplayer in Lucid repos outdated?"
date: 2010-05-01
forum: General Help
---

### Post by inameiname on 2010-05-01
I've noticed a couple of times having comments about mplayer being outdated or that it needs updated since I installed Lucid a couple days ago.

Anybody else having this issue? Or having trouble with mplayer?

---

### Post by dracayr on 2010-05-01
mplayer works fine on my system (Lucid)

---

### Post by Coda2010 on 2010-05-01
There is a significant article re: mplayer and lucid on ubuntu geek.

---

### Post by clhsharky on 2010-05-01
HI inameiname

Is there something wrong with mplayer?

Works fine on my system.


Sharky

---

### Post by Ginsu543 on 2010-05-01
It appears that mplayer works fine with the version of ffmpeg in the lucid repos but it won't work with the latest version of ffmpeg I've recompiled from svn. I get the following error message:

"relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference"

Unfortunately, I can't use the ffmpeg in the repos because it doesn't support aac, which I need. So I recompiled it with aac (and several other codecs) enabled.

---

### Post by aviramof on 2010-05-01
There are newer version in rvm ppa and in ripps ppa.
 
[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)
 
i prefer ripps because she multi threaded but i recommend adding both ppa's.

---

### Post by Ginsu543 on 2010-05-01
aviramof, you are a lifesaver!!! Thanks for the heads-up. Now my ffmpeg works as it should with mplayer and mencoder.

---

### Post by inameiname on 2010-05-02
Thanks for the input. I did the same thing that Ginsu543 did, so I'm sure that's the issue. Duh on me. :P Thanks for the PPA suggestion. I'll try that. :)

---

### Post by Ginsu543 on 2010-05-02
I tried the rvm ppa and it worked like a charm.

---

### Post by inameiname on 2010-05-02
Awesome. I just put both PPAs into my sources.list and updated. I think the Ripps one had the most up-to-date one, so hopefully it works too. Otherwise, I'll get rid of it and use the RVM one only as you said it worked.

---

### Post by dixon on 2010-05-02
The package (mplayer) dependancy in rvm's ppa isn't setup correctly. If you're not using nvidia GPU it may break your system. 
The mplayer from the ppa requests to install nvidia-current package etc. The same problem [had]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/530481") default mplayer package during the Lucid development phase. Hopefully it'll be fixed soon.

---

### Post by inameiname on 2010-05-02
Oh so RVM's doesn't work now for you, despite you saying it did in earlier posts? Is that what you are getting at?

---

### Post by dixon on 2010-05-02
> **inameiname said:**
> Oh so RVM's doesn't work now for you, despite you saying it did in earlier posts? Is that what you are getting at?

Is this a response to my post? I didn't get it. What earlier posts? I'm just saying that the current mplayer package in the ppa isn't packaged correctly. It depends upon nvidia-current...

---

### Post by mc4man on 2010-05-02
> I'm just saying that the current mplayer package in the ppa isn't packaged correctly. It depends upon nvidia-current...

If you take a look you'll see that is a 'personal ppa', it was I believe set up for a specific build. 
It does say 

> 
For mplayer and smplayer packages, please use these PPAs instead:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)
or
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

So no I don't think it's mis-configured at all...
(testing has the 'generic' mplayer build for lucid

---

### Post by Ginsu543 on 2010-05-02
I was the one who said rvm's ppa worked. But then again, I'm running an nVidia graphics card (for the first time in a long time), so I didn't know it didn't work for others.

---

### Post by inameiname on 2010-05-02
Oh I'm sorry Dixon, I thought you were the one who recommended that ppa. It was Ginsu543. My mistake. Chalk it up to posting that reply at such an early time in the morning. :P

Anyway, thanks for the comment, Dixon. I decided to just remove the svn version of ffmpeg that I created and installed using a script, and install it from the official repos and be done with it.

---

### Post by rvm4000 on 2010-05-02
So what should be the correct build-depend?

I think my latest build depends on libvdpau-dev and not on nvidia-185-libvdpau-dev.

---

### Post by mc4man on 2010-05-02
> what should be the correct build-depend?

The ppa linked in this thread is from your personal ppa where there is a depend on nvidia-current
> libxxf86vm1, nvidia-current, zlib1g (>= 1:1.1.4),


(though it does state that one should use the other ppa's in the links

---

### Post by dixon on 2010-05-02
> **rvm4000 said:**
> So what should be the correct build-depend?

I think my latest build depends on libvdpau-dev and not on nvidia-185-libvdpau-dev.

I think I'm not using the correct PPA as mc4man stated. I'm using the ppa:rvm/ppa. When I add this ppa and run aptitude install mplayer It wants to install the nvidia drivers.
```

The following NEW packages will be installed:
  dkms{a} libdirac-decoder0{a} libggi-target-x{a} libggi2{a} libgii1{a} 
  libgii1-target-x{a} mplayer-skins{a} nvidia-current{a} nvidia-settings{a} 
The following packages will be upgraded:
  mplayer 

```
I first looked into ppa:rvm/mplayer, but I didn't find the lucid build there. As I can see now you've added the lucid build into the ppa. Thank you very much :)

Btw thank you for the great work - your smplayer is the only video player that suits me in ubuntu :)

---

### Post by rvm4000 on 2010-05-02
> **mc4man said:**
> The ppa linked in this thread is from your personal ppa where there is a depend on nvidia-current

> libxxf86vm1, nvidia-current, zlib1g (>= 1:1.1.4),

(though it does state that one should use the other ppa's in the links

I don't recommend to use that ppa ([http://launchpad.net/~rvm/](http://launchpad.net/~rvm/)). It's for me only (to test things) and sometimes I even forget about what I uploaded.

I think the package from [https://launchpad.net/~rvm/+archive/testing/](https://launchpad.net/~rvm/+archive/testing/) doesn't have that problem, it doesn't depend on any nvidia package.

---

### Post by mc4man on 2010-05-02
> I don't recommend to use that ppa ([http://launchpad.net/~rvm/](http://launchpad.net/~rvm/)). It's for me only (to test things) and sometimes I even forget about what I uploaded.
That's what I was thinking - The confusion in this thread came from the link posted in post #6 from aviramof - iirc you were helping him with his 'unique' issue in lucid testing and he may have assumed that link was the one to recommend to others in general

---

### Post by aviramof on 2010-05-05
I Have edited my #6 reply and removed rvm ppa but i do hope that when i would reinstall ubuntu 10.04 in a few week it would already have an updated mplayer in the
main reposetories and an updated versions of everything that should be updated including fixed bugs like with fglrx and plymouth and ubiquity and compiz and etc.
 
And that is all for now unless someone have something to say to me here or in private.:)
 
Bye for now and cya then.:):):):)

---

