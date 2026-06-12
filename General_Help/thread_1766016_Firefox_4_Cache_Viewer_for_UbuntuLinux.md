---
title: "Firefox 4 Cache Viewer for Ubuntu/Linux?"
date: 2011-05-23
forum: General Help
---

### Post by OzzyFrank on 2011-05-23
Hi. OK, just noticed to my major disappointment that Firefox 4 has a new caching system, being multiple folders instead of the one, and even more subfolders within each, which of course makes it a nightmare to try and find those flash vids I used to find so quickly and simply.

There are some Mozilla and Firefox cache viewers for Windows, and even trying to work around the path syntax differences, I can't get either to recognise the cache folder in Ubuntu (possibly to do with it being in a hidden folder).

So, is there any cache viewer made for Linux yet? Or some other way to quickly find stuff in this labyrinth of cache folders?

As for flash/YouTube vids, I'm still seeing people referring to using downloaders, but as far as I know, they're ALL useless with how YouTube does things now... still, if you have found one that can still do this, please let me know, as the primary reason I would be looking in the cache is for such files. Cheers

---

### Post by linuxinstalledfromhdd on 2011-05-23
had the same issue. found some videos I want to save for later.

downgraded to early flash version 9.

problem solved. 

tmp folder will be where they show up in their entirety. no hassle with multiple folders again. :popcorn:

---

### Post by hvbakel on 2011-05-23
Just type ```
about:cache
``` in the URL bar and you'll get an overview of all cached documents.

---

### Post by linuxinstalledfromhdd on 2011-05-23
no, that won't work. Adobe has modified the way the cache files are stored.  They are broken apart into various folder are are made unreadable.  Downgrading your flash plugin would be the only viable solution.

---

### Post by OzzyFrank on 2011-05-23
**about:cache** just gives some info, and doesn't even include the full path. I've read that now Firefox compresses many files into individual cache files, but I'm still seeing lots of individual pics etc (at least I gather that from the thumbnails - so I'm hoping this means those individual Flash vids exist as such somewhere).

As for downgrading Flash, besides the fact I'd really prefer not to have to do that, I have to ask how would this affect Firefox 4's new way of handling all files cached? I mean, Flash handles those vids, but Firefox has a new caching system which I thought is independent of Flash (ie: I thought Firefox handles the caching of those, like it does every other filetype, not the Flash plugin)

---

### Post by linuxinstalledfromhdd on 2011-05-23
It's really simple.

You install flash aid plugin.

Download the flash installer for flash player 9. 

Uncompress it. Locate the flash plugin that was in there.

Open up Flash Aid and point it to the older plugin. 

It will install it automatically, and then check your tmp folder. 

You will find all the videos that you view are stored there again, just like they did years ago in older versions of Ubuntu. 

It's an Adobe issue because Chrome does the exact same thing.

---

### Post by jesterthejedi on 2011-05-25
Where would I grab the version 9? Getting old versions of Flash is not available on Adobe.com

---

### Post by OzzyFrank on 2011-05-25
I was going to look at the "fix", even though I really hate downgrading things, but have just noticed Flash problems I had with certain sites are now cleared up. At Herald-Sun (Aussie newspaper), I could only get 11 secs of 15 of the obligatory ad to play, and never the actual clip I wanted to see (or rarely), and at UK's BBC pages, the embedded clips NEVER played... and all that is fixed up FINALLY! So, I am somewhat loathe to go backwards, as you can well imagine (some of the BCC clips I've missed I really wanted to see).

And I have to admit surprise that this whole folders-within-folders cache move is actually dictated by Flash, not a Firefox move, as others state.

Any other suggestions? Any Windows cache viewers for Firefox 4 that work under Wine?

---

### Post by LordNeo on 2011-05-25
Give Mobile Media Converter a go:

[http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)

---

### Post by lovinglinux on 2011-05-25
Instead of downgrading flash, just get [Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/"). Is the best extension for downloading videos from almost any web site.

---

### Post by OzzyFrank on 2011-05-25
I ended up getting **[COLOR="Red"]Mobile Media Converter[/COLOR]**, and could force-install it on my 64-bit system just fine. Haven't tried the convert feature, as it did what I wanted, being download the vid via the URL (quite happy to keep them as .flv files, since there's no issue playing them in Ubuntu).

I will have to look at **Video Download Helper** as well, after I get back from the gym (been dawdling here too long!). Just I can see it is a Firefox plugin, and all the ones I have previously tried no longer work (presumable coz of changes YouTube made to prevent exactly this). But I'm assuming you're using it just fine, since you mentioned it, so will report back on this for the benefit of others.

As for the former, you can **[download it here]("http://www.miksoft.net/products/mmc_1.7.1_i386.deb")**, and if running a 64-bit system, open a terminal in the folder you downloaded to and run: **[COLOR="Red"]sudo dpkg --force-architecture -i mmc_1.7.1_i386.deb[/COLOR]**

Cheers. Frank

---

### Post by OzzyFrank on 2011-05-25
Oops! I actually downloaded the **Video Download Helper** plugin a few days ago. I couldn't get it to do jack, at least when it comes to downloading YouTube vids (didn't test it for any other use). I'll have another look later, but I did look through its Preferences when I couldn't get anything to happen, and didn't find anything useful.

---

### Post by lovinglinux on 2011-05-26
> **OzzyFrank said:**
> Oops! I actually downloaded the **Video Download Helper** plugin a few days ago. I couldn't get it to do jack, at least when it comes to downloading YouTube vids (didn't test it for any other use). I'll have another look later, but I did look through its Preferences when I couldn't get anything to happen, and didn't find anything useful.

That is weird, because all you need is to install the extension, visit an YT  page and the toolbar Download Helper icon will start spinning to show videos are available for download. Just click the arrow and you see a bunch o resolution options to download.

I just tested on a clean profile, to make sure it works out-of-the-box and it does.

BTW, you need to start playing the video on YT to allow the extension to detect the videos.

---

### Post by OzzyFrank on 2011-05-26
Man, I had no idea about the icon! Maybe it said it somewhere on the add-on page, but all I saw mention of was the context-menu, which was easy enough to find, but proved useless to me. However, NOW looking again, I see the ***Media*** sub-menu has a bunch of different listings for the one vid, being different resolutions/sizes and extensions (mp4 and flv). I seriously didn't have this before (that menu was empty, every page I was on), but have restarted Firefox since my initial look.

But the icon near the top of the page is better/quicker, as you can just click ***Download*** and specify a target folder. BUT, not sure what the difference between that option and ***Download & Convert*** is, seeing as the **[COLOR="Indigo"]flv[/COLOR]** was downloaded as an **[COLOR="Indigo"]mp4[/COLOR]**. Isn't that being converted from **[COLOR="Indigo"]flv[/COLOR]**, or does YouTube now store each vid in both formats?

In its Preferences, I could see no mention of default format to save to, but I did see an option to enable converting, which oddly enough is disabled. Using the ***Quick Download*** option, it saves it to **~/dwhelper** as I assumed it would (ie: doesn't give you the option of picking a destination), and once again saves it in **[COLOR="Indigo"]mp4[/COLOR]** format.

Anyway, this is still a quick way to grab YouTube vids, and if you really prefer them in (original?) **[COLOR="Indigo"]flv[/COLOR]** format, use the right-click menu and do it that way.

Now let's see if someone in the open source world follows the Windows guys' lead and creates a Firefox 4 cache viewer, as that will avoid having to re-download every clip you've watched.

---

### Post by OzzyFrank on 2011-05-26
> **lovinglinux said:**
> **BTW, you need to start playing the video on YT to allow the extension to detect the videos.**

Ah, that could be it... I was already on the page of the vid I really wanted to keep (an Ubuntu commercial, actually) before installing the plugin. When I went to other clips' pages, I immediately stopped/paused them before they started playing.

---

### Post by lovinglinux on 2011-05-26
I don't use the convert feature. YouTube stores the videos as mp4, flv or webm.

If you don't want to play before downloading, get my [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer") extension. 

It is primarily designed to allow Linux users to watch HD videos without eating CPU cycles, because it replaces the flash player with something better like gecko-mediaplayer. However the extension also allows to download, without the need to play first. Works on YouTube, Vimeo, Metacafe, Blip.tv and Ustream.

If you want the flv format, you don't need any add-on. Just click the YouTube icon in the address bar, then "More information", then "Media".

---

### Post by OzzyFrank on 2011-05-26
> **lovinglinux said:**
> If you want the flv format, you don't need any add-on. Just click the YouTube icon in the address bar, then "More information", then "Media".

Could you please explain further on this approach? All I could see there was mention of all image files on the page, plus a couple of .swf files. Is one of those .swf files the vid, and are you suggesting to save it in that format? Cheers

---

### Post by lovinglinux on 2011-05-26
> **OzzyFrank said:**
> Could you please explain further on this approach? All I could see there was mention of all image files on the page, plus a couple of .swf files. Is one of those .swf files the vid, and are you suggesting to save it in that format? Cheers

Sorry. It only works with the html5 player.

---

### Post by OzzyFrank on 2011-05-27
Good to know that's there anyway, which I didn't!

---

### Post by johnmarley on 2011-05-27
> **lovinglinux said:**
> Instead of downgrading flash, just get [Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/"). Is the best extension for downloading videos from almost any web site.

Thank You!! :)

---

### Post by lovinglinux on 2011-05-27
> **OzzyFrank said:**
> Good to know that's there anyway, which I didn't!

Yeah, that can be handy.

> **johnmarley said:**
> Thank You!! :)

You are welcome.

---

### Post by Lylex11 on 2011-06-02
Check out this script called "flashcache" Found the youtube video cached in my browswer that all other methods failed to download.

[http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)

I first found it here:
[http://askubuntu.com/questions/37267/tmp-directory-doesnt-show-flashstreaming-youtube-videos-in-firefox-4-why](http://askubuntu.com/questions/37267/tmp-directory-doesnt-show-flashstreaming-youtube-videos-in-firefox-4-why)

---

