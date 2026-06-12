---
title: "GLSlideShow no longer works after upgrade to 11.10"
date: 2011-10-19
forum: General Help
---

### Post by TerranJerry on 2011-10-19
Hello fellow Ubuntu users!

I am hoping you can help me.  Since I let the upgrade manager upgrade my Ubuntu system to 11.10 (I think I was previously at 10.06 or so), I find that the GLSlideShow (xscreensaver) that was working before is no longer working - with the same images that were working previously.

Basically when I start xscreensaver in verbose mode, i see these types of errors when it attempts to access each JPG file.  Note - these files worked prior to the upgrade to 11.10.

xscreensaver-getimage: unable to load "/usr/share/backgrounds/cosmos/venusmoon_eder.jpg"
xscreensaver-getimage: reason: Couldn't recognize the image file format for file '/usr/share/backgrounds/cosmos/venusmoon_eder.jpg'
 <match value="mimetype" type="string" offset="30">

Also, I should mention that I saw the very old comments in another post about editing the MIME types in freedesktop.org.xml to remove the line that looks like this:
 <match value="mimetype" type="string" offset="30">
and then reload the mimetypes.  I tried that.
Unfortunately that did not fix the problem.

The xscreensaver still complains that it doesn't recognize the image file format.

Any ideas?  I very much appreciate your kind help and thank you in advance for any tips!  :)

Jerry

---

### Post by TerranJerry on 2011-10-25
I'm a bit surprised no one else has encountered this since upgrading to 11.10 - at least no one has replied on this yet.  I run a pretty standard Ubuntu - no special mods really.  I update it when the updates are available so it should not have run into this problem aside from something changed.  I would guess it was something in the MIME types or GTK but I'm not a guru by any stretch on those subjects so that's why i am hoping someone else has seen this happen.  It seems familiar to the previous incident several years ago but the fix suggested then does not seem to work now for me.

Is this territory that is unsupported since this is Xscreensaver and the Gnome screensaver seems to be the preferred solution?

---

### Post by TerranJerry on 2011-11-01
Wow 89 views and no feedback.  Has no one else seen this issue?  I am surprised I am the only person using Xscreensaver with the GLSlideShow option that is seeing this problem!  Seems like others should have seen this.  By the way, it is not limited to GLSlideShow.  It seems like any screensaver that uses a JPEG file (including the one that uses the desktop) is having an issue opening it.  Does that trigger any thoughts on what might be wrong?

---

### Post by TerranJerry on 2011-11-15
So, 124 views and not one reply (other than my own). ... Do I need to repost this in some other forum area to get assistance?  Seems odd no one has encountered this here.... Jerry

---

### Post by Peter Maunder on 2011-12-03
I have not hit your exact problem but screensavers are a well exercised subject with 11.10, I am sorry to say.

The xscreensaver website is at [http://www.jwz.org/xscreensaver](http://www.jwz.org/xscreensaver) if you need specific advise .

The Gnome screensaver in 11.10 just provides a blank screen, a subject of some debate.  If you wish to use a "proper" screensaver with a slideshow you need to remove or disable the Gnome-screensaver, install the latest versions of xscreensaver and xscreensaver-gl (the latter contains GLSlideshow). 

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html) deals very well with this subject. 
There is also a small problem if you use the Ubuntu Software Centre to manage your software as the 11.10 version does not show the products under the index entry of  "SCREENSAVER". You will need to search under Gnome-screensaver, Xscreensaver and Xscreensaver-gl to find and manage the individual products. Synaptic and Terminal are business as usual.

Hope this helps Peter

---

