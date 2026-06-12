---
title: "Best image viewer with basic edit (resize, crop, rotate)?"
date: 2012-05-02
forum: General Help
---

### Post by MrsUser on 2012-05-02
Can anyone recommend a good image viewer to a newbie (me)? I switched from Windows to Ubuntu 12.04. In Windows 7, I used XnView. I'm looking for something similar for Ubuntu. I found Gwenview, but it's for KDE. Is there something like Gwenview, but for Gnome? P.S. Running XnView via Wine is not an option for me. It should be native.

---

### Post by andrew.46 on 2012-05-02
It is a little less featured than gwenview but perhaps gqview might be worth a quick look?

---

### Post by MrsUser on 2012-05-02
At any rate, I also need crop function.

---

### Post by LewisTM on 2012-05-02
gThumb is what you're looking for. It runs well in both GNOME and Xfce without the loading time associated with Gwenview (still my all-time favorite).
Click the Edit file button at the top right to access the functions you mentioned.

Cheers!

---

### Post by philinux on 2012-05-02
As well as gthumb try pinta and there's always gimp of course.

---

### Post by sgage on 2012-05-02
> **LewisTM said:**
> gThumb is what you're looking for. It runs well in both GNOME and Xfce without the loading time associated with Gwenview (still my all-time favorite).
Click the Edit file button at the top right to access the functions you mentioned.

Cheers!

I recommend gthumb as well. Lightweight and simple, but does the few things I usually need to do quickly and easily.

---

### Post by keithpeter on 2012-05-02
Hello All

I may have misunderstood the question, but Shotwell can crop, can resize and can rotate in increments of 90 degrees.

Free with every install :twisted:

Seriously, I did all the screengrabs and crops in the Unity poster and in the Unity2d guide linked to my sig with Shotwell as I wanted to show what can be done with the default apps.

---

### Post by philinux on 2012-05-02
> **keithpeter said:**
> Hello All

I may have misunderstood the question, but Shotwell can crop, can resize and can rotate in increments of 90 degrees.

Free with every install :twisted:

Seriously, I did all the screengrabs and crops in the Unity poster and in the Unity2d guide linked to my sig with Shotwell as I wanted to show what can be done with the default apps.

Hi Keith. The thing that puts me of shotwell is the import side. I just don't need it. All my pics  are already organized in folders.

---

### Post by LewisTM on 2012-05-02
> **philinux said:**
> Hi Keith. The thing that puts me of shotwell is the import side. I just don't need it. All my pics  are already organized in folders.
+1
It's a different kind of software. Imagine you get an SD card and you just want to browse the pictures on it. You can't do that in Shotwell without importing them inside your library. You can launch Shotwell to view a single file but then the features are limited. In contrast I have setup a custom command in Thunar to open a given directory with gThumb and it does just that - browse the pics in that folder.

---

### Post by guestolo on 2012-05-02
Why not use XnView?
[http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056](http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056)

---

### Post by LewisTM on 2012-05-02
> **guestolo said:**
> Why not use XnView?
[http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056](http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056)
Looks good.
Found [32-bit]("http://www.wubijacq.com/xnviewmp/xnviewmp0.39x32.deb") and [64-bit]("http://www.wubijacq.com/xnviewmp/xnviewmp0.39x64.deb") packages.

---

### Post by keithpeter on 2012-05-02
> **philinux said:**
> Hi Keith. The thing that puts me of shotwell is the import side. I just don't need it. All my pics  are already organized in folders.

Fair enough.

In Nautilus, right click over image file and select 'open with Shotwell'

You can then just use the editing and export features and not the import.

Resizing is counter-intuitive, you have to select save as, then select the width or height from a dialogue.

YMMV and I'll try out Gthumb to see how I like it.

---

### Post by eric-yorba on 2012-05-02
> **philinux said:**
> Hi Keith. The thing that puts me of shotwell is the import side. I just don't need it. All my pics  are already organized in folders.
Shotwell's directory structure is 100% optional.  Just drag your photo library into the app and select "Import in Place."  Nothing will be moved.

---

### Post by Uncle Spellbinder on 2012-05-02
I love gThumb. Currently using gThumb 3.0.0. Excellent app for common editing procedures. Couldn't imagine using Ubuntu without it.

```
#### gThumb
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/gthumb/ubuntu precise main 
deb-src http://ppa.launchpad.net/webupd8team/gthumb/ubuntu precise main
```



[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by mike555 on 2012-05-02
I like "Mtpaint" it works like a viewer,paint program, and does some editing like cropping,adding text, etc.and it's  very light and small.

---

### Post by MrsUser on 2012-05-03
Thanks everyone. I decided to go with gThumb. Shotwell is strange, because I can tell a file to 'Open with Shotwell', but from there I cannot switch to the picture managing/library function. But gThumb seems to get it right.

Would like to try the Linux versin of XnView, too. But as this seems to be in development still and as I don't trust external package sources, I don't want to take the risk.

EDIT:
I have downloaded XnView from that forum link from XnView, followed the instructions to manually install it. And what can I say? It's the best! Forget gThumb and other image viewers. Still couldn't sort out my wifi routing problems though :-/

---

### Post by philinux on 2012-05-03
> **eric-yorba said:**
> Shotwell's directory structure is 100% optional.  Just drag your photo library into the app and select "Import in Place."  Nothing will be moved.

That's what I don't want, my library is organised into date/text ordered folders. So I dont want to drag anything anywhere. I just edit single pics on the fly.

I'll stick with gimp. 2.8 is now out too.

I might give xnview a try out.

---

### Post by eric-yorba on 2012-05-03
> **philinux said:**
> I'll stick with gimp. 2.8 is now out too.
And it's amazing!  For anyone who hasn't installed it yet, you can grab it from this PPA for Precise:
[https://launchpad.net/~otto-kesselgulasch/+archive/gimp]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp")

---

### Post by MrsUser on 2012-08-01
It's me again. Just to update this thread, because since late June 2012 there are now debian packages available for XnView MP 0.51 beta, officially from the XnView author's website (with their forum though):

[http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033](http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033)

There are 32-bit and 64-bit packages.

I tried many viewers, like gThumb for instance. But there is a big problem with gThumb, as it doesn't remember to start maximized or with a screen-centered 'fit to window' mode.

XnView to me always was the best and most powerful image viewer/organizer while I was still under Windows 7. But as I abandoned Windows completely, I was desperately looking for an image viewer as good as XnView - the only last bit I was missing to give me a perfect Ubuntu experience. And luckily, now it's XnView itself, named XnView MP (Multi Platform).

At the moment, XnView MP for Linux is still beta. But it seems a final/stable release is about to come soon to the Linux world. And then I hope it will become the default viewer in Ubuntu and also get global menu integration.

I also recommend XnConvert, which is a batch image processing software. It's from the same developer and already has a final release for Linux available. So far, I was using Phatch, which is an excellent batch image processing tool as well. But I guess the combination of XnView MP and XnConvert is unbeatable.

On top of that, Gimp 2.8 finally made single-window mode available. Now I'm really happy in Ubuntu as far as the image editing stuff is concerned. I hope there will also be a good video editor in the future. And I think Flowblade is the best candidate for this.

<snip>

---

### Post by nitroguy on 2012-09-10
Thanks for the update! I'm looking for the same thing, so I'll give XnView a shot! (Pun intended). :-)

---

### Post by MrsUser on 2012-10-04
The new gThumb version supports remembering the maximized window state and has nice new features:

[http://www.webupd8.org/2012/09/gthumb-gets-webp-support-in-latest-311.html](http://www.webupd8.org/2012/09/gthumb-gets-webp-support-in-latest-311.html)

I already installed it. It's very good. So, basically gThumb is the all-in-one viewer who can do viewing and all basic editing functions such as resizing and cropping. Really nice.

---

### Post by Rebelli0us on 2012-11-09
You can download Xnview [from here]("http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033").

It looks and feels like the Windows version but is much faster. To install, I right-clicked the .deb file and selected “Open with gdebi package installer”, done.

---

### Post by MrsUser on 2013-01-14
XnView for Linux is out of beta stage and now available as a proper release. This is so awesome. It was the only software I knew from Windows which I was really missing in Ubuntu.

It can be downloaded as a .deb file from the official site:

[http://www.xnconvert.com/downloads](http://www.xnconvert.com/downloads)

Double-click .deb file, software center opens, install. Better than any other image viewer I know for Linux. It is fast, has a great library/thumbnailing function (which can be altered in settings - thumbnail caching on disk can be switched off for instance) and many basic editing capabilities (crop, resize, red-eye removal, etc).

---

### Post by LewisTM on 2013-01-14
> **MrsUser said:**
> XnView for Linux is out of beta stage and now available as a proper release. This is so awesome. It was the only software I knew from Windows which I was really missing in Ubuntu.

It can be downloaded as a .deb file from the official site:

[http://www.xnconvert.com/downloads](http://www.xnconvert.com/downloads)

The link you provided is for XNConvert. It looks like a nice batch conversion program and it is reported to be powered by XNview, but it's not a picture browser. [XNview MP for Linux]("http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033") is still dated 26-Jun-2012. Or am I missing something?

---

### Post by MrsUser on 2013-01-15
Sorry, my bad. Indeed, it's for XnConvert. XnView is still beta :-/

---

