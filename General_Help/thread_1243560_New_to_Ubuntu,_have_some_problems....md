---
title: "New to Ubuntu, have some problems..."
date: 2009-08-18
forum: General Help
---

### Post by forgotten_hell on 2009-08-18
So I installed Ubuntu today using Wubi. I had tried it before but never used it much. I've always used Windows and am pretty good at using it so I thought I should be able to figure out Ubuntu as I've never really had problems with tech related stuff before.

But I am having problems.

I was trying to get Firefox 3.5 installed and I think I ended up installing it as Shiretoko without realizing it. Well, still thinking it wasn't installed, I used Ubuntuzilla to install it. Now Shiretoko is working (figured out what it was), but the Firefox won't load at all and is telling me it's the newest version. So instead of having a functional FF3.0 as was suppose to happen I have a not working 3.5. What should I do to make it functional again?

Also, I wanted to install Skype so I looked up instructions and found them. I downloaded the file, but it won't let me install it with the GDebi package installer as it says I'm suppose to. It tell me what to run it with or something, but I can't find GDebi for the life of me. I am using AMD 64 stuff, but I did download the right file for that. How can I install it?

Thanks for the help!

---

### Post by realzippy on 2009-08-18
Skype:
You have to enable the medibuntu repos..
[http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu)
Then you can install skype via synaptic,e.g....

---

### Post by fela on 2009-08-18
OK. For firefox, what I'd do is completely remove everything to do with firefox (or shiritoko or whatever) - then reinstall it via synaptic.

With skype, you can either do what realzippy suggested, or you can do this:

open up a terminal, and run (assuming the skype deb is on the desktop):

```
cd /home/$USER/Desktop
```

Now run:

```
sudo dpkg -i nameofpackage.deb
```

That should install skype for you. 90% of the time you'll have problems with audio and/or video after it's installed, but 90% of the time they're fixable.

You don't need gdebi to install packages! It's just a silly GUI with a dpkg backend. Using dpkg is more reliable and plain better - remember Linux is centred around the command line and there are (alot of the time) far better command line counterparts than the relatively few GUI apps made for Linux. Hope this helps :)

---

### Post by forgotten_hell on 2009-08-18
Ok, thanks, I did what you said for Skype fela and it worked! Thanks.

But, erm, what's synaptic? And if I do that, will it still be Shiritoko or real FF? Because now I installed my add-ons and everything to Shiritoko and don't really wanna have to do it again, but I could I guess. I just didn't like have this and one non-working Firefox on my system...

---

### Post by fela on 2009-08-18
> **forgotten_hell said:**
> Ok, thanks, I did what you said for Skype fela and it worked! Thanks.

But, erm, what's synaptic? And if I do that, will it still be Shiritoko or real FF? Because now I installed my add-ons and everything to Shiritoko and don't really wanna have to do it again, but I could I guess. I just didn't like have this and one non-working Firefox on my system...

Synaptic is just a package manager (GUI for apt-get) - it's in system > adminsitration > synaptic IIRC.

If you have a working shiritoko that you don't mind using - use that! But if it's not working right then I'd ditch it and everything firefox related (just to clean everything up and in case you missed something) - and reinstall firefox from synaptic. Erm, you can install addons whatever, they're not gonna go away. Sure it's a pain installing them all over again but it's better than having a not working firefox isn't it?

EDIT: if you want a working web browser in the mean time - just install epiphany (might be epiphany-browser - can't remember, I think epiphany might be a game). Just search in synaptic.

---

### Post by forgotten_hell on 2009-08-18
No, Shiretoko is working fine. That's what I am on now... so I guess I'll just use that. But is it possible to revert my actual Firefox down to 3.0 so it works again? Not that I'll be using it, it just bothers me having a browser on my system that doesn't even work.

---

### Post by realzippy on 2009-08-18
If firefox 3.0 has not been uninstalled,it should be still there..
You can open a terminal and type:

**firefox 3.0**

---

### Post by forgotten_hell on 2009-08-18
It's not, it's 3.5.2 or whatever now because I used Ubuntuzilla to update it, but it won't load pages now.

---

### Post by fela on 2009-08-18
> **forgotten_hell said:**
> It's not, it's 3.5.2 or whatever now because I used Ubuntuzilla to update it, but it won't load pages now.

So it doesn't work? I say, if shiretoko works just use it. If you don't want firefox 3.0, try uninstalling it from synaptic (make sure not to select shiretoko though ;))

---

### Post by realzippy on 2009-08-18
As fela said,manage your software with synaptic.Open it,
search for firefox.Check the firefox 3.0 for installation and apply.

**sudo apt-get install firefox-3.0**

...would do it faster than synaptic opens...

---

### Post by scouser73 on 2009-08-18
> **forgotten_hell said:**
> No, Shiretoko is working fine. That's what I am on now... so I guess I'll just use that. But is it possible to revert my actual Firefox down to 3.0 so it works again? Not that I'll be using it, it just bothers me having a browser on my system that doesn't even work.

**[COLOR="Black"]Installing Firefox 3.5 [/COLOR]**  

1. Download Firefox from the [[COLOR="Red"]**Firefox**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/") download page to your home directory.
   2. Open a Terminal and extract the contents of the downloaded file.

      [B]cd ~
      tar xjf firefox-*.tar.bz2[/B]

   3. Close Firefox if it&#8217;s open.
   4. To start Firefox, run the firefox script in the firefox folder.

      [B]~/firefox/firefox
[/B]

---

### Post by fela on 2009-08-18
I don't see what the big deal is with firefox 3.5. I tested it on karmic and it didn't seem to offer anything any faster or with more features than 3.0. I do have quite a speedy machine though so it might be more applicable on a slower processor. Chrome beats firefox for me though, but sadly the linux version is still unstable and very lacking right now.

---

### Post by nanotube on 2009-08-18
> **forgotten_hell said:**
> It's not, it's 3.5.2 or whatever now because I used Ubuntuzilla to update it, but it won't load pages now.

Hi
try this tip from the ubuntuzilla faq:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F)

if that still doesn't work, or if you really want to go back to the default version of firefox, just run the ubuntuzilla remove script, and it will set everything back to the way it was:
```
ubuntuzilla.py -a remove -p firefox
```

there are detailed instructions on the ubuntuzilla website.

---

### Post by forgotten_hell on 2009-08-19
> **scouser73 said:**
> **[COLOR=Black]Installing Firefox 3.5 [/COLOR]**  

1. Download Firefox from the [[COLOR=Red]**Firefox**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/") download page to your home directory.
   2. Open a Terminal and extract the contents of the downloaded file.

      [B]cd ~
      tar xjf firefox-*.tar.bz2[/B]

   3. Close Firefox if it’s open.
   4. To start Firefox, run the firefox script in the firefox folder.

      [B]~/firefox/firefox
[/B]


I got Firefox back down to the 3.0 then did what you said and it didn't work. It kept giving me this error when on step 2. I don't mind using Shiretoko, but will I be able to update it? And for some reason links from something like Skype still open in Firefox...

---

### Post by forgotten_hell on 2009-08-19
Bump, at this point all I wanna know is if I can update Shiretoko. I'm content using it as long as I can update it.

---

### Post by realzippy on 2009-08-19
Again,use synaptic to manage your software.For removing,installing and
updating....

---

### Post by tacantara on 2009-08-19
> **forgotten_hell said:**
> Bump, at this point all I wanna know is if I can update Shiretoko. I'm content using it as long as I can update it.

You shouldn't have any problems updating Shiretoko.  I've been using it for awhile now, and it even receives the occasional automatic update from Ubuntu.  Currently there's no way through the Help menu to check for updates to the browser, but you can check for updates to plugins.

---

