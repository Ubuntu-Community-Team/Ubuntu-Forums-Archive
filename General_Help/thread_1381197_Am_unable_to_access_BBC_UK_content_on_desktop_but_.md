---
title: "Am unable to access BBC UK content on desktop but can on laptop - why?"
date: 2010-01-14
forum: General Help
---

### Post by Scunnered on 2010-01-14
Earlier when installing Karmic I requested assistance to enable me to listen & view BBC content in the United Kingdom.  This involved me in loading :

mozilla-mplayer, 
flashplugin-nonfree,
Ubuntu restricted extras

which worked a treat. 

I decided to install Karmic on an old desktop system with the intent of using it as a backup system for my data.  Having installed this as a fresh install I again followed the earlier advice only to find that when I attempted to connect to the BBC I was asked to load flash.  This happened no matter which station I attempted to listen or view.   

As far as I can see everything has been installed exactly as on my laptop and therefore should naturally work as before.  The only difference is the laptop is using 64 bit and the desktop 32.
Since I now see that the desktop is also capable of 64 bit processing should installing the 64 bit Karmic help?

Using sysinfo does not give too much information. I am told that the CPU is an AMD Athlon 64x2 Dual Core processor 4400+, 1000.000 MHz & L2 cache 512.  The graphic card is shown as VGA Compatible Controller and the Sound Card as a multimedia Audio Controller.

I am at a loss why I am being asked for flash on the desktop and not being able to have the same benefits as I have on my laptop running the same OS.

Can anyone offer a solution to this problem.

---

### Post by mk1w86 on 2010-01-14
Have you restarted your browser etc. and does the problem occur on every website that uses flash or just IPlayer?

If you have a 64bit disk from your laptop it is probably worth trying it just to see if you have the same problem. :)

---

### Post by ron999 on 2010-01-14
Just to add to what mk1w86 has said above.

Check that the Firefox flash plugin has actually been installed. In Firefox enter **about:plugins** in the browser.
That's **a b o u t : p l u g i n s** without the spaces.
It should say:-
> Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r42

Also in Firefox select Tools > Addons > Plugins and make sure that Flash has not been disabled.

---

### Post by audiomick on 2010-01-14
gday Ian.
It is not the 64 - 32 bit difference. If anything, the 32 bit version should work better.
There'll be some silly little thing missing...;)

---

### Post by Scunnered on 2010-01-14
My thanks to you both for your advice.

I had an initial look at the plugins only to find that Shockwave is installed on the laptop but nowhere to be seen on the desktop.

Can you please advise how I go about loading Shockwave to the desktop?

Many thanks

---

### Post by ron999 on 2010-01-14
Hi Scunnered
I seem to remember that firefox asked me if I wanted to install it and I just said yes.
Maybe you have to download it (a deb) from here:-[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by mk1w86 on 2010-01-14
When you installed ubuntu-resticted-extras flash should have been installed along with the various other packages it downloads.

You could try running:

```
sudo apt-get install ubuntu-restricted-extras
```

again just in case it installs some extra packages. 

Otherwise have a look at the link that ron999 posted above. :D

---

### Post by Scunnered on 2010-01-14
Who ever said that things could only get better lied !

I followed to the letter the suggestions of ron999 and mk1w86 and in each instance was informed that in the case of the extras I had the most up to date version and adobe advised that their install conflicts with installed Flashplugin-installer.

Further advice on activating Shockwave would be appreciated as I am getting to like banging my head against the wall a little too much

---

### Post by t0p on 2010-01-14
> **Scunnered said:**
> 
Further advice on activating Shockwave would be appreciated as I am getting to like banging my head against the wall a little too much

I would suggest that you use the search function in Synaptic to search for "shockwave".  This will list all packages with "shockwave" in the title; then you can see about installing it.

You might have to uninstall your present flash player in order to install the Shockwave player.

---

### Post by audiomick on 2010-01-14
sorry I can't help you. If a site won't play for me, I tend to get snooty and not go there.;)

Have a whisky and wait for someone smarter than me to turn up. It is possible to fix this.:D

edit: see, he's already here!

---

### Post by mk1w86 on 2010-01-14
As a last resort you could reinstall Ubuntu (32 or 64bit) and run:

```
sudo apt-get install ubuntu-restricted-extras
```

after installation.  This should install all packages necessary to use IPlayer (no other package installation should be required even though it has worked on your laptop).

You might also be interested in this:

[http://linuxcentre.net/getiplayer](http://linuxcentre.net/getiplayer)

---

### Post by Scunnered on 2010-01-14
Again my thanks to all for their posts.

**t0p**

Synaptic is not offering anything against the description of Shockwave.

** audiomick**

Michael I can't agree more that a large drop of the water of life will go down extremely well. Two would be much better and I propose to have them both and sleep on the problem. No doubt someone will rescue me.

Failing that I will start afresh and load the 64 bit version and hope that works.

Like you if a site will not work for me most of the time it's kick it into touch but as everything works perfectly on the laptop I see no good reason why it will not work on the desktop.

---

### Post by Scunnered on 2010-02-26
I gave up on this as frustration had set in but got back to it again and am pleased to say I managed to resolve matters.

I was at a loss as to what graphic card I had on this old desktop and after a bit of searching found out how to check.  Found that it was a nVidia and checking hardware drivers found that there was one available. 

The download worked a treat so I am now happy to report that alls well that ends well.

---

