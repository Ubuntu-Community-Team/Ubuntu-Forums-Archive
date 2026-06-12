---
title: "Why can't I set my screen resolution - heron"
date: 2010-02-12
forum: General Help
---

### Post by tomm174 on 2010-02-12
I'm running Hardy
A couple of weeks ago I did two things that I know of
Allowed updates to happen
Installed WIne & ClamAV using Add/Remove from the Applications menu

Now I have no access to my samba shares, and I have a choice of resolutions, 800x600, or 640x480

sudo dpkg-reconfigure xserver-xorg makes no difference

Makes no difference if I try to detect displays, edit /etc/X11/xorg.conf, or if the little applet that supposedly allows me to choose what hardware I've got runs when I start the X-server

WTF - Why doesn't xorg.conf do what it always did.
I quite strongly object to updates nuking my customised conf files, but I have come to expect that.
Do I have to burn a hole in google's servers to find out how to fix this ?

I'm still on Hardy because I want stability 

Did I make some stupid error - could it perhaps be arranged that if I am about to then I could be warned

Is this likely to keep happening ? If so does anyone have any suggestion for a way to keep things stable so I can get on with my work ?

---

### Post by stoneage on 2010-02-12
If there was a kernel update you may need to reinstall your graphics drivers.

Do you use drivers from the repository or from the card's manufacturer?

---

### Post by tomm174 on 2010-02-12
Don't think the kernel was updated.
Not sure what you mean by "reinstall your graphics drivers."
I have selected them using displayconfig-gtk & other things.
Drivers are from the repository FWIW

That's not the point I'm making really.
My xorg.conf was nuked - I think it warned me, I saved a copy  & let it save one too, but the version it produced was a low-res basic generic config, and even when I put back the saved version I still get the same lo-res display
It seems that now whatever I put in xorg.conf makes no difference

It looks to me like either :
a) something other than /etc/X11/xorg.conf is setting my X config
OR possibly  - & I'll check into this tomorrow
b) X has decided something is so badly broken that it falls back to a basic config. - I don't know whether it would do that

Is it possible that xorg.conf is no longer in control ?
If it's not, then what is ?

The obvious means I have to set my system's configuration are not working (displayconfig-gtk, dpkg-reconfigure xserver-xorg, system preferences) - that is they run, but it makes no difference. 
Why  ?

---

### Post by stoneage on 2010-02-12
If you compile and install graphics drivers downloaded from the manufacturer's website a kernel update usually necessitates reinstalling the graphics drivers, but if you are using drivers from the repository they should be working. 

Which drivers and graphics card are you using?

Karmic and Jaunty too I think, use something called hal now instead of the xorg.conf but if there is one there it will read from it so it should be using it.

Can you explain this a bit more:-
> My xorg.conf was nuked - I think it warned me,

I had a similar experience a while ago. One day Hardy booted into low graphics mode and nothing seemed to make any difference, I tried updating to Jaunty and got the same thing. So now I use an xorg.conf(also on Karmic) with a custom modeline to ensure I get native resolution.

I still don't know what broke it but my monitor hasn't been properly detected since........  An Asus VW192S

---

### Post by tomm174 on 2010-02-13
Thanks for your help - life is too short

I run an update.  Without my say-so a fundamental configuration of my machine ceases to work.

Seems to me that there is a real problem about what is being allowed to be released.  No one is thinking of the users. There is no reason on earth that whatever improvements developers make should break the basic set up -  there are no developments in graphics that require changing the basic config files.
All that is needed is for a graphics card & display to be selected, so the appropriate driver can be started.
A text based config file is all that is needed. Any amount of bells whistles and widgets can be attached to make it look like something someone should get an award for, it can be changed on the fly or incorporate transform matrices or messages to alien lifeforms, for all I care, so long as the existing setups continue to work.
I realise there are limits to this, but there should be a really good reason to break stuff.  The fact that someone wants to be able to put on their resumé that they did a project with XML is not a reason to put the result into a distribution which will be downloaded to millions of installations and potentially break them.

Just since installing the supposedly stable Heron I have had to deal with 
xorg.conf
dpkg-reconfigure xserver-xorg
HAL
Now [URL="https://wiki.ubuntu.com/Halsectomy"]HAL is deprecated
[/URL]
I don't want to participate in this stupid timewasting game.
It is very disappointing, I will watch the forums to see if I think this kind of self-indulgent change for the  sake of it is has stopped, and in the mean time try to forget that I ever believed there was a place for Ubuntu in my business.

---

