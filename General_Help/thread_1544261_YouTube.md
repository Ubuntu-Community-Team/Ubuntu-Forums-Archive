---
title: "YouTube"
date: 2010-08-02
forum: General Help
---

### Post by Hosmion on 2010-08-02
Hello everyone :).  I watch a bunch of YouTube videos on a bunch of different things, but I tend to have a couple problems.  When I find something I want to watch, I click on it and it takes me to the video screen.  But, nothing works when I click on the video.  No pause, no volume down, no nothing.  I don't know how to fix this so if someone could help that would be fantastic.  Thanks :).

---

### Post by Cavsfan on 2010-08-02
> **Hosmion said:**
> Hello everyone :).  I watch a bunch of YouTube videos on a bunch of different things, but I tend to have a couple problems.  When I find something I want to watch, I click on it and it takes me to the video screen.  But, nothing works when I click on the video.  No pause, no volume down, no nothing.  I don't know how to fix this so if someone could help that would be fantastic.  Thanks :).


Check this workaround. The 3rd step is all I had to do to get the buttons working.

_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

---

### Post by Cavsfan on 2010-08-02
That should do it, but if you don't have the latest flash installed check _[here.]("http://www.adobe.com/software/flash/about/") _
Then if you're out of date, install **LovingLinux**'s Flash-Aid FF add-on from _[here.]("https://addons.mozilla.org/en-US/firefox/addon/161939/") _

That should fix you up! :D

Plus installing the flash-aid will be good for future flash updates.
As you may be aware of Adobe stopped supporting 64 bit flash, 
but if you are 32 bit or 64 bit, the 32 bit version works very well!

---

### Post by _h_ on 2010-08-02
> **Cavsfan said:**
> As you may be aware of Adobe stopped supporting 64 bit flash

No. They stopped letting people download the labs version of it temporarily, and they are continuing work on it.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

> We have temporarily closed the Labs program of Flash Player 10 for  64-bit Linux, as we are making significant architectural changes to the  64-bit Linux Flash Player and additional security enhancements.  We are  fully committed to bringing native 64-bit Flash Player for the desktop  by providing native support for Windows, Macintosh, and Linux 64-bit  platforms in an upcoming major release of Flash Player. We intend to  provide more regular update information on our progress as we continue  our work on 64-bit versions of Flash Player. Thank you for your  continued help and support. Stay tuned to the [Flash Player discussion forum]("http://forums.adobe.com/community/webplayers/flash_player") for further announcements.

---

### Post by Bhamid on 2010-08-02
Try disabling Compiz and running with Metacity instead (disable Desktop Effects).

---

### Post by Cavsfan on 2010-08-02
> **_h_ said:**
> No. They stopped letting people download the labs version of it temporarily, and they are continuing work on it.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)


Yea, that is what I meant to say: that they stopped development temporarily on 64 bit Linux flash.
They say it that way, but they do not seem in any hurry to get back on it...
The version that was available and can still be had, but is a security vulnerability anyway.

_[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)_

---

### Post by _h_ on 2010-08-02
> **Cavsfan said:**
> Yea, that is what I meant to say: that they stopped development temporarily on 64 bit Linux flash.
They say it that way, but they do not seem in any hurry to get back on it...
The version that was available and can still be had, but is a security vulnerability anyway.

_[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)_

They didn't stop development, they only stopped people from acquiring it via adobe labs until their next major release.

---

### Post by Cavsfan on 2010-08-02
> **Bhamid said:**
> Try disabling Compiz and running with Metacity instead (disable Desktop Effects).

That is in the workaround in my first post after the OPs.

The OP has not been back on to check that which will likely solve the problem...

---

### Post by Cavsfan on 2010-08-02
> **_h_ said:**
> They didn't stop development, they only stopped people from acquiring it via adobe labs until their next major release.

Again, I didn't mean they stopped altogether, just took a break from developing it.
But, they are taking their sweet time if they are indeed just pausing...

Edit: I did say temporarily stopped development on it...

---

### Post by Cavsfan on 2010-08-02
There is about a 99.9% chance that my first post will fix the OPs issue, can we just wait until he/she comes back and tries that before we offer more suggestions? :|

---

### Post by Hosmion on 2010-08-02
> **Bhamid said:**
> Try disabling Compiz and running with Metacity instead (disable Desktop Effects).
This fixed it.  Much appreciated.

---

### Post by Cavsfan on 2010-08-02
> **Hosmion said:**
> This fixed it.  Much appreciated.

If you don't want Compiz anymore I guess you are good to go...

---

### Post by Hosmion on 2010-08-02
> **Cavsfan said:**
> If you don't want Compiz anymore I guess you are good to go...
Compiz is the only one that works.  I can't seem to download the Flash Player from Adobe, I did the editing of whatever (didn't work), and disabling Compiz is the only one that works.

---

### Post by Cavsfan on 2010-08-02
> **Cavsfan said:**
> If you don't want Compiz anymore I guess you are good to go...

> **Hosmion said:**
> Compiz is the only one that works.  I can't seem to download the Flash Player from Adobe, I did the editing of whatever (didn't work), and disabling Compiz is the only one that works.

I like Compiz and mine works superbly! All I had to do was edit the file:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: [COLOR=Navy]export GDK_NATIVE_WINDOWS=1[/COLOR] before the last line of text

That works for most people.
But, glad one of them got yours to work.

---

### Post by Hosmion on 2010-08-02
> **Cavsfan said:**
> I like Compiz and mine works superbly! All I had to do was edit the file:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: [COLOR=Navy]export GDK_NATIVE_WINDOWS=1[/COLOR] before the last line of text

That works for most people.
But, glad one of them got yours to work.
I already did that, hense:

> **Hosmion said:**
>  I did the editing of whatever (didn't work)

---

### Post by Cavsfan on 2010-08-02
> **Hosmion said:**
> Compiz is the only one that works.  I can't seem to download the Flash Player from Adobe, I did the editing of whatever (didn't work), and disabling Compiz is the only one that works.

Get **Lovinglinux**'s FireFox addon for updating flash as it works well.

[U][https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

[/U]Maybe that'll solve your problem, so you can still use Compiz.

---

### Post by Hosmion on 2010-08-02
> **Cavsfan said:**
> Get **Lovinglinux**'s FireFox addon for updating flash as it works well.

[U][https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

[/U]Maybe that'll solve your problem, so you can still use Compiz.
Seems to be fixed, but I just did it so it could go wrong soon.  I'll edit this post and message you if it has problems again.  Thanks :)

---

### Post by Cavsfan on 2010-08-02
> **Hosmion said:**
> Seems to be fixed, [COLOR=Red]but I just did it so it could go wrong soon[/COLOR].

You are welcome, but just wondering why you would hope it goes wrong soon....
IMHO if it's fixed, it'll stay fixed. :rolleyes:
And please don't message me about this.

And did you enable compiz?

---

### Post by Hosmion on 2010-08-02
> **Cavsfan said:**
> You are welcome, but just wondering why you would hope it goes wrong soon....
IMHO if it's fixed, it'll stay fixed. :rolleyes:
And please don't message me about this.

And did you enable compiz?
Haha I won't message you :).

Yes, I enabled Compiz.

---

### Post by Cavsfan on 2010-08-02
> **Cavsfan said:**
> You are welcome, but just wondering why you would hope it goes wrong soon....
IMHO if it's fixed, it'll stay fixed. :rolleyes:
And please don't message me about this.

And did you enable compiz?

> **Hosmion said:**
> Haha I won't message you :).

Yes, I enabled Compiz.


Glad you got it going! That workaround has fixed many people's problems with youtube including myself. 
And I didn't mean any offense about the messaging...

Could you please mark this thread as solved if it has served it's purpose.
You just go up to [COLOR=Red]Thread Tools[/COLOR] at the top right and then click on [COLOR=Red]Mark this thread as solved[/COLOR].
Thanks :)

---

