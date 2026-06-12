---
title: "Amazon music store doesn't show in Banshee 1.7.3"
date: 2010-07-27
forum: General Help
---

### Post by TheNerdAL on 2010-07-27
I installed Banshee and upgraded it but I don't see the Amazon Music Store. Anyone mind helping a new Banshee user?

---

### Post by LowSky on 2010-07-27
Are you sure you have version 1.7.3?

---

### Post by monstrosity on 2010-07-27
It doesn't show for me either. I do see some dependencies on this webpage: 

[http://abock.org/2010/07/13/amazon-mp3-store-in-banshee](http://abock.org/2010/07/13/amazon-mp3-store-in-banshee)

libwebkit 
libwebkit-dev

libsoup
libsoup dev

this didn't help me, but it did help some others.

---

### Post by TheNerdAL on 2010-07-27
> **LowSky said:**
> Are you sure you have version 1.7.3?

Yeah, I'm sure. I attached a screenshot.

---

### Post by LowSky on 2010-07-27
Sorry I'm not at my Ubuntu desktop to test, but maybe its a plugin you need to enable?

---

### Post by TheNerdAL on 2010-07-27
> **LowSky said:**
> Sorry I'm not at my Ubuntu desktop to test, but maybe its a plugin you need to enable?

The extension is enabled.

---

### Post by LowSky on 2010-07-27
Found this, your not the only one having problems
[http://www.omgubuntu.co.uk/2010/07/banshee-173-released-adds-amazon-mp3.html](http://www.omgubuntu.co.uk/2010/07/banshee-173-released-adds-amazon-mp3.html)

seems it might have been pulled from the Ubuntu PPA, you get 1.7.3 but not all its features.
You might need to install the Tarball, which isn't recommended
[http://download.banshee-project.org/banshee/unstable/1.7.3/banshee-1-1.7.3.tar.bz2](http://download.banshee-project.org/banshee/unstable/1.7.3/banshee-1-1.7.3.tar.bz2)

---

### Post by TheNerdAL on 2010-07-27
> **LowSky said:**
> Found this, your not the only one having problems

seems it might have been pulled from the Ubuntu PPA, you get 1.7.3 but not all its features.
You might need to install the Tarball, which isn't recommended
[http://download.banshee-project.org/banshee/unstable/1.7.3/banshee-1-1.7.3.tar.bz2](http://download.banshee-project.org/banshee/unstable/1.7.3/banshee-1-1.7.3.tar.bz2)

So amazon isn't going to be in Banshee? :(

---

### Post by doorknob60 on 2010-07-27
I installed Banshee-git from AUR and it works fine (awesome feature!). Probably just need to manually compile it and make sure it's enabled.

---

### Post by LowSky on 2010-07-27
it will, its just missing due to one of the required dependencies broke

give it time, in the mean time just go to the amazon website, and try downloading a .amz file and see if banshee recognizes it.
If not there is a way to get the out of date amazon installer to work, which I use currently and is great.

---

### Post by TheNerdAL on 2010-07-27
I also don't know how to use last.fm with Banshee. :P

---

### Post by LowSky on 2010-07-27
> **TheNerdAL said:**
> I also don't know how to use last.fm with Banshee. :P

DO you have a last.fm account? setting it up online isn't hard.

Also I just install 1.7.3 and it works im using the amazon store as I speak. Also added the extension for the Ubuntu One store, so now I can scan both and pick the cheaper option.

so if it isn't showing up, I cant understand why

---

### Post by TheNerdAL on 2010-07-27
> **LowSky said:**
> DO you have a last.fm account? setting it up online isn't hard.

Also I just install 1.7.3 and it works im using the amazon store as I speak. Also added the extension for the Ubuntu One store, so now I can scan both and pick the cheaper option.

so if it isn't showing up, I cant understand why

I do have a Last.Fm account and I logged in but I have no idea how to play.

---

### Post by pemadorje on 2010-07-29
> **LowSky said:**
> Also I just install 1.7.3 and it works im using the amazon store as I speak. Also added the extension for the Ubuntu One store, so now I can scan both and pick the cheaper option.

so if it isn't showing up, I cant understand why

I have really been looking forward to this feature but alas, it isn't working for me either. I have 1.7.3 installed and you can see in the attached screenshot that I have the Amazon store extension enabled, but (as you can also see) there is no store that appears. Total bummer. Not sure what the deal is but would greatly appreciate any help.

---

### Post by TheNerdAL on 2010-07-29
> **pemadorje said:**
> I have really been looking forward to this feature but alas, it isn't working for me either. I have 1.7.3 installed and you can see in the attached screenshot that I have the Amazon store extension enabled, but (as you can also see) there is no store that appears. Total bummer. Not sure what the deal is but would greatly appreciate any help.

Just asking but what theme are you using? :P

---

### Post by pemadorje on 2010-07-29
> **TheNerdAL said:**
> Just asking but what theme are you using? :P

It's the default from this Ubuntu remix... [http://ubuntuforums.org/showthread.php?t=1528174](http://ubuntuforums.org/showthread.php?t=1528174)

---

### Post by pemadorje on 2010-07-30
> **LowSky said:**
> Also I just install 1.7.3 and it works im using the amazon store as I speak. Also added the extension for the Ubuntu One store, so now I can scan both and pick the cheaper option.

so if it isn't showing up, I cant understand why

Can I ask which repository you used to install this? I uninstalled and reinstalled this a bunch of times last night and always the same result. Tried the banshee-team and banshee-daily PPAs and no go. This is driving me mad. Not sure why it is working for some but not others.

---

### Post by Rifester on 2010-07-31
You are not the only one...  I have a computer with OpenSUSE on it and the Amazon Store is working GREAT!  I downloaded the Ubuntu Daily Banshee PPA and installed it.   Only Amazon support is possible, there is no way to select the store.   I wonder if Ubuntu is blocking this feature to "encourage" use of the Ubuntu Music Store.   I sure as hell hope not.

---

### Post by bowens44 on 2010-08-01
> **Rifester said:**
> You are not the only one...  I have a computer with OpenSUSE on it and the Amazon Store is working GREAT!  I downloaded the Ubuntu Daily Banshee PPA and installed it.   Only Amazon support is possible, there is no way to select the store.   I wonder if Ubuntu is blocking this feature to "encourage" use of the Ubuntu Music Store.   I sure as hell hope not.

Specifically which version 1.7.3 are you using? Also which repository did you use to install it?

amazon is not working for me and if I upgrade past the version I have now which is 1.7.3+git20100709.r1.2bc12f2-0ubuntu1+lucid, the lyrics extension doesn't work. 

I installed my version from banshee-team/banshee-daily/


thanks

---

### Post by pemadorje on 2010-08-02
Just for the heck of it, I install Ubuntu Maverick in VirtualBox and then installed Banshee from the banshee-daily ppa and the Amazon store works fine. I noticed that (in Maverick) when you go to edit --> preferences --> extensions, there are actually two extensions: "Amazon MP3 Import" and "Amazon MP3 Store Source".... Whereas in Ubuntu Lucid, there is only the "Amazon MP3 Import" extension.

---

### Post by jblackhall on 2010-08-02
I installed from the banshee unstable PPA and it's working fine: [https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)

---

### Post by pemadorje on 2010-08-02
> **jblackhall said:**
> I installed from the banshee unstable PPA and it's working fine: [https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)

Finally, a lead. :) I didn't know about that ppa. I'll give it a try tonight. Thanks for the tip!

---

### Post by TheNerdAL on 2010-08-02
> **jblackhall said:**
> I installed from the banshee unstable PPA and it's working fine: [https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)

It's not working for me.

---

### Post by Rifester on 2010-08-02
It worked, I had to complete un-install Banshee and then install from the unstable PPA.  Thank you!

---

### Post by TheNerdAL on 2010-08-02
> **Rifester said:**
> It worked, I had to complete un-install Banshee and then install from the unstable PPA.  Thank you!

Guess I must do the same huh?

---

### Post by pemadorje on 2010-08-02
> **jblackhall said:**
> I installed from the banshee unstable PPA and it's working fine: [https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)

Thanks very much. It works. I completely uninstalled Banshee, disabled the other Banshee PPAs, added the unstable Banshee PPA and then re-installed Banshee. At first the store didn't show up again. But then I installed "banshee-community-extensions" and now it's there and it works great!

---

### Post by firefeather on 2010-08-02
This worked for me, too. Specifically, the Banshee Daily PPA has a version with a higher version number than in the Banshee Unstable PPA, but the Banshee Unstable version is the one configured properly for the Amazon Music Store to be included.

Step-by-step:

[LIST=1]
[*]Uninstall the Daily PPA version of Banshee and banshee extensions
[*]Add the Banshee Unstable PPA (or make sure it's enabled)
[*]Disable the Banshee Daily PPA
[*]Reload package information (so the PPA changes take effect)
[*]Install Banshee and the extension packages
[*]Make sure the "Amazon MP3 Store Source" extension is enabled in the Preferences window.
[/LIST]
If you don't have the Banshee Daily PPA enabled and you haven't installed a Daily PPA version of 1.7.3 or higher, follow only steps 2, 4, 5, and 6.

This also makes it possible to enable the Miro Podcast Directory. :D

---

### Post by TheNerdAL on 2010-08-04
> **pemadorje said:**
> Thanks very much. It works. I completely uninstalled Banshee, disabled the other Banshee PPAs, added the unstable Banshee PPA and then re-installed Banshee. At first the store didn't show up again. But then I installed "banshee-community-extensions" and now it's there and it works great!

No wonder it didn't work for me! I didn't disable the other PPA. :p Thanks now it worked! :D

---

