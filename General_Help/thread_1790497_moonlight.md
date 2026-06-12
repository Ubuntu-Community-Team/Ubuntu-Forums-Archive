---
title: "moonlight"
date: 2011-06-25
forum: General Help
---

### Post by kybush on 2011-06-25
Does anybody know how to get Moonlight working in Firefox 5.0

---

### Post by lovinglinux on 2011-06-25
See the quote below

> **lovinglinux said:**
> 
Moonlight indeed doesn't work. If you are on a 32bit system, you can do this:

Remove your current Moonlight:

```
sudo apt-get remove libmoon moonlight-plugin-core moonlight-plugin-mozilla
```

Then install [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"), to disable compatibility check. Keep in mind this will allow to install incompatible add-ons in Firefox, so if you experience any problems, disable it.

Then go to [Mono web site]("http://go-mono.com/moonlight/download.aspx") and install the latest Moonlight 4.

Restart Firefox. You can test your plugin at [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)

This method didn't work with 64bit. The plugin just crashes.



---

### Post by Frogs Hair on 2011-06-25
I have Moonlight working on 64 bit FF 7.0 a1 , I don't know why it would work on 7.0 and not the FF 5.0 stable release.

---

### Post by lovinglinux on 2011-06-25
Double post.

---

### Post by lovinglinux on 2011-06-25
Well, I tested on VM, because my host is 32bit. Maybe that was the problem.

---

### Post by parsim on 2011-06-28
I got the "Failed to install" message when trying to install the plugin from here:

[http://go-mono.com/moonlight/download.aspx](http://go-mono.com/moonlight/download.aspx)

... and so then hunted through Synaptic and installed moonlight-plugin-mozilla (2.3.0ubuntu5). As I was waiting, I read that this wouldn't work on 64-bit.

But to my surprise, **it actually worked**. Or at least one of the above worked (I didn't actually test after the initial failure message).

This is on Firefox 5 64-bit: Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/20100101 Firefox/5.0

---

### Post by trizrK on 2011-06-28
I think it's best to wait for an update.

---

### Post by chehalem on 2011-06-30
I was able to get moonlight working in Firefox 5, 64bit 11.04 by removing existing moonlight and all plug ins, installing the Firefox Add-on Compatibility Reporter, then reinstalling the 32bit version of moonlight.  64bit version of moonlight crashed.  It seems to be working even without installing the mozilla moonlight plugin.

see here for more help [http://ubuntuforums.org/showpost.php?p=10979646&postcount=1034]("http://ubuntuforums.org/showpost.php?p=10979646&postcount=1034")

---

### Post by Jimboted on 2011-08-19
Hi, 

Been banging my head against a wall trying to do this for several days, found the solution here:

[http://syntacticsugar.nl/2009/06/19/ubuntu-firefox-moonlight-and-microsoft-codecs-pack/](http://syntacticsugar.nl/2009/06/19/ubuntu-firefox-moonlight-and-microsoft-codecs-pack/)

Only difference being that I could not get the codecs to install until I went to a page with a moonlight video - firefox them prompted me to install automatically.  Used the following:

[http://www.innoveware.com/ql3/QuakeLight.html](http://www.innoveware.com/ql3/QuakeLight.html)

Cheers,


Jim

---

### Post by mgt2000 on 2011-09-03
you can also disable Firefox compatibility check if you want to use Firefox 6. Then you can still use the current version of moonlight on Firefox 6

---

### Post by thepisu on 2011-09-29
Also for me (Ubuntu 11.04 amd64) worked installing package moonlight-plugin-mozilla.

---

### Post by Redsandro on 2012-01-04
So why was the Moonlight plugin [removed from the repositories]("http://www.ubuntuupdates.org/packages/show/345225")?
I googled around, no ball.

It's more of a hassle to get it now, but hey.. life is supposed to improve, not the other way around, right? ;)

---

### Post by crazy bird on 2012-01-04
Moonligth will only work with Firefox versions 3.x through 4.x. Other versions aren't supported at the moment, quote of the Moonlight FAQ:
> *Moonlight should work on any modern 32bit and 64bit Linux distributions under Firefox versions 3.0 through 4.x, as well as Google Chrome, from both stable and dev channels*

 
I experience the same problem when using the latest version of Firefox.

---

### Post by directhex on 2012-01-04
> **Redsandro said:**
> So why was the Moonlight plugin [removed from the repositories]("http://www.ubuntuupdates.org/packages/show/345225")?
I googled around, no ball.

It's more of a hassle to get it now, but hey.. life is supposed to improve, not the other way around, right? ;)

Because upstream is dead.

---

### Post by Frogs Hair on 2012-01-04
I use Moonlight with the Firefox Nightly 12 build and have the tester tools to override compatibility .

Since I don't use the current stable release I don't know what versions Moonlight will work with .

If Moonlight is really wanted or needed this add on may help . [https://addons.mozilla.org/en-us/thunderbird/addon/add-on-compatibility-reporter/](https://addons.mozilla.org/en-us/thunderbird/addon/add-on-compatibility-reporter/) 

Some sites have DRM protection ,so moonlight won't work anyway . For the most part , if I need Silverlight / Moonlight I boot Windows .

---

### Post by MARP1961 on 2012-01-04
I can confirm it does work on Chrome/Chromium. Why don't you use Chromium whenever you need Moonlight?

---

### Post by Frogs Hair on 2012-01-04
> **MARP1961 said:**
> I can confirm it does work on Chrome/Chromium. Why don't you use Chromium whenever you need Moonlight?

I have two browsers already and the reason that Moonlight doesn't work on some sites is DRM not because an inability to find codec/ s .  Netflix is an example of this . MS adds a binary that allows the  proprietary Silverlight to work and this is not included with Moonlight .

---

