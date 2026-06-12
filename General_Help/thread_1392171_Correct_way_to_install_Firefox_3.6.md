---
title: "Correct way to install Firefox 3.6"
date: 2010-01-27
forum: General Help
---

### Post by oxf on 2010-01-27
OK right now with Jaunty I have Firefox 3.0......... something or other.

I'd like to install FF 3.6. What is the "correct" way to do that and replace my current version of 3.0 that came with Jaunty with FF 3.6? (not have two versions on my system)

I have some instructions on how to do this adding the repository but its written for Karmic and I did try this and it messed things up a bit. Thats no big deal now but I'd like to add FF 3.6 properly

Thanks

---

### Post by blazemore on 2010-01-28
Frankly, you can't.
You can use Mozilla's package and untar it, or you can use the mozilla-daily PPA.
I'm waiting for someone to package a .deb for GetDeb.

---

### Post by Leppie on 2010-01-28
use the mozilla daily ppa, the repos are:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main 
```

---

### Post by Oropher8598 on 2010-01-28
Unfotunately there isn't a repository anywhere with 3.6 right now The mozilla-daily repo contains development versions, which are generally stable, but come branded as 'Shiretoko' rather than 'Firefox'.

What I did was download from Mozilla and unpack it into a hidden folder in my home directory. (I usually put apps like this go into one called '.extras' - ~/.extras/firefox in this case.) If you change the preferred browser in *Preferred Applications* to a custom shortcut pointing to 3.6 (e.g. /home/myusername/.extras/firefox/firefox ), and make launchers for it wherever you tend to start Firefox from, it replaces the stock Firefox fairly seamlessly.

---

### Post by Leppie on 2010-01-28
> **Oropher8598 said:**
> Unfotunately there isn't a repository anywhere with 3.6 right now The mozilla-daily repo contains development versions, which are generally stable, but come branded as 'Shiretoko' rather than 'Firefox'.
i have namoroka, i think shiretoko was the previous one?

> **Oropher8598 said:**
> What I did was download from Mozilla and unpack it into a hidden folder in my home directory. (I usually put apps like this go into one called '.extras' - ~/.extras/firefox in this case.) If you change the preferred browser in *Preferred Applications* to a custom shortcut pointing to 3.6 (e.g. /home/myusername/.extras/firefox/firefox ), and make launchers for it wherever you tend to start Firefox from, it replaces the stock Firefox fairly seamlessly.
i don't think that your installed plugins in 3.5 will be available in 3.6 like this

---

### Post by oxf on 2010-01-28
> **Oropher8598 said:**
> Unfotunately there isn't a repository anywhere with 3.6 right now The mozilla-daily repo contains development versions, which are generally stable, but come branded as 'Shiretoko' rather than 'Firefox'.

What I did was download from Mozilla and unpack it into a hidden folder in my home directory. (I usually put apps like this go into one called '.extras' - ~/.extras/firefox in this case.) If you change the preferred browser in *Preferred Applications* to a custom shortcut pointing to 3.6 (e.g. /home/myusername/.extras/firefox/firefox ), and make launchers for it wherever you tend to start Firefox from, it replaces the stock Firefox fairly seamlessly.

OK I see what you mean. I'll try that then

For my learning experience what exactly is the "mozilla-daily-PPA"? Is that justa fancy name for the development repos?
Thanks!

---

### Post by Leppie on 2010-01-28
> **oxf said:**
> OK I see what you mean. I'll try that then

For my learning experience what exactly is the "mozilla-daily-PPA"? Is that justa fancy name for the development repos?
Thanks!
it's a prelease which is updated daily. this means that issues are unlike to persist for a long time if a bug is filed.

---

### Post by sarin_cv on 2010-01-28
i have configured the daily repo...but i could not find firefox 3.6 there...instead i installed firefox 3.7 which ws code named as minefield. downloading tar file from mozilla website also din't work as it launched the old firefox itself...

---

### Post by oxf on 2010-01-28
> **Leppie said:**
> it's a prelease which is updated daily. this means that issues are unlike to persist for a long time if a bug is filed.

OK thanks!

That all installed nicely :)

A couple of "cosmetic" questions now....
I
 was told I can change the name that it shows up as i.e Namoroka to Firefox by changing it in: About:Config, under: useragent..... I did that, replacing namoroka with firefox but it still lists as firefox. Why? can I change that?

And is there any way to replace the Naoroka icon, i.e the blue planet earth, with the normal Firefox icon?

Just cosmetic issues I know and not that big of a deal but just curious.

---

### Post by Uncle Spellbinder on 2010-01-28
There is no "correct" way. There are several reliable ways, but here is the easiest..

Ubuntuzilla, the BEST way to go to get Firefox 3.6.

Simply add to following to your sources.list:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Then do:
```
sudo apt-get update
```

Then do:
```
sudo apt-get install firefox-mozilla-build
```

More info here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and here: [http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by hvbakel on 2010-01-28
There is also the firefox-stable ppa:

[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

---

### Post by skymera on 2010-01-28
I highly suggest using the Firefox Stable PPA for Ubuntu.

```
 https://launchpad.net/~mozillateam/+archive/firefox-stable 
```

Upgrades Firefox rather than installing a new package.
I find this is better than the Mozilla Daily

---

### Post by NFblaze on 2010-01-28
Ubuntuzilla (which Uncle Bender has already wrote suggested) is what I used. It works so far. I think I like it better, because it's basically a ppa. Except they update much more timelier than the Ubuntu repository. I've removed Ubuntu's Firefox and am now using Ubuntuzilla's Firefox and will continue to do so. It works great, everything including bookmarks is still the same. I had to make a new shortcut on my toolbar, but it's great.

Oh yea, Ubuntuzilla only has 32-bit packages right now. So if your using 64-bit you may need to use something else.

---

### Post by blazemore on 2010-01-28
> **Uncle Spellbinder said:**
> There is no "correct" way. There are several reliable ways, but here is the easiest..

Ubuntuzilla, the BEST way to go to get Firefox 3.6.

Simply add to following to your sources.list:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```Add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```Then do:
```
sudo apt-get update
```Then do:
```
sudo apt-get install firefox-mozilla-build
```More info here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and here: [http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)
Doesn't work on 64 bit

---

### Post by scouser73 on 2010-01-28
Here's the advice I give.

[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> **sudo -i**
Enter your password if asked
> **cd /opt**
> **chown -R username firefox**
[COLOR="Red"]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by bodhi.zazen on 2010-01-28
> **oxf said:**
> OK right now with Jaunty I have Firefox 3.0......... something or other.

I'd like to install FF 3.6. What is the "correct" way to do that and replace my current version of 3.0 that came with Jaunty with FF 3.6? (not have two versions on my system)

I have some instructions on how to do this adding the repository but its written for Karmic and I did try this and it messed things up a bit. Thats no big deal now but I'd like to add FF 3.6 properly

Thanks

There is no single "correct" way to install firefox 3.6 , only options. use the one you like best.

Personally I agree with scouser73 in that I simply download the binary from mozilla and put it in my home directory (single user system) or in /usr/local (multi user system).

Personally I find it is quite simple to use the binary and it works well.

I do not worry about having multiple versions installed on my system, it does little or no harm and takes up a little HD space is all.

In terms of extensions, some are not compatible with 3.6 and they will be disabled.

The compatible extensions will work, on one install I had no problems, on another I had to update all my extensions and they then worked.

---

### Post by crichard on 2010-01-29
> **oxf said:**
> OK right now with Jaunty I have Firefox 3.0......... something or other.

I'd like to install FF 3.6. What is the "correct" way to do that and replace my current version of 3.0 that came with Jaunty with FF 3.6? (not have two versions on my system)

I have some instructions on how to do this adding the repository but its written for Karmic and I did try this and it messed things up a bit. Thats no big deal now but I'd like to add FF 3.6 properly

Thanks

It's highly recommended to install firefox from [http://mozilla.com](http://mozilla.com)

Have a look at this post to install [URL="http://surferzworld.com/?p=193"]Firefox / Thunderbird in Ubuntu.
[/URL]

---

### Post by nanotube on 2010-01-30
> **crichard said:**
> It's highly recommended to install firefox from [http://mozilla.com](http://mozilla.com)


by whom, exactly? ( [http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words](http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words) )

> 
Have a look at this post to install [URL="http://surferzworld.com/?p=193"]Firefox / Thunderbird in Ubuntu.
[/URL]

these particular instructions are ok, as in they won't screw up your machine, but since they manually link the launcher to /usr/bin/firefox, that means the next firefox update to come through the ubuntu repos will overwrite the link - not good. they should either add a dpkg-divert, or use /usr/local/bin for the link...

if you're gonna plug a blog post full of ads, at least make sure it has good instructions!

---

### Post by oxf on 2010-01-31
> **scouser73 said:**
> Here's the advice I give.

[[COLOR=Red]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal


Enter your password if asked


[COLOR=Red]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

Thanks for your very logical and detailed instructions! :)

---

### Post by oxf on 2010-01-31
> **Leppie said:**
> use the mozilla daily ppa, the repos are:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main 
```

Could someone tell me where/how I obtain the public keys for these?

Interesting when I added these on my desktop it didn't promt me for them. But.... now trying it on my laptop I am prompted for one of them :confused:

Thanks

---

### Post by Yellow Pasque on 2010-01-31
> was told I can change the name that it shows up as i.e Namoroka to Firefox by changing it in: About:Config, under: useragent..... I did that, replacing namoroka with firefox but it still lists as Namoroka. Why? can I change that?

The useragent trick is to make sure websites see "Firefox" and not something else, which might confuse poorly coded sites. It doesn't change the name/logo that the user sees, which is purely cosmetic, as you noted.

---

### Post by nanotube on 2010-01-31
> **oxf said:**
> Could someone tell me where/how I obtain the public keys for these?

Interesting when I added these on my desktop it didn't promt me for them. But.... now trying it on my laptop I am prompted for one of them :confused:

Thanks

if you use apt-add-repository command, it automatically pulls the keys off launchpad... but if you add the sources.list lines manually, you have to add the keys manually too. that's probably the source of the difference between what you did on your desktop and laptop.

at any rate, you can see the key used for the repo on the launchpad webpage for the repo:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by Leppie on 2010-01-31
you can use this oneliner to get a missing key for a repo:
```
sudo apt-get update 2> /tmp/keymissing; for key in $(grep "NO_PUBKEY" /tmp/keymissing |sed "s/.*NO_PUBKEY //"); do echo -e "\nProcessing key: $key"; gpg –keyserver subkeys.pgp.net –recv $key && gpg –export –armor $key | sudo apt-key add -; done
```

---

### Post by devolute on 2010-01-31
> **skymera said:**
> I highly suggest using the Firefox Stable PPA for Ubuntu.

```
 https://launchpad.net/~mozillateam/+archive/firefox-stable 
```

Upgrades Firefox rather than installing a new package.
I find this is better than the Mozilla Daily

I did it this way and it has screwed up my fonts and now I don't have Firefox icons, just large black crosses.

Not very good.

---

### Post by Leppie on 2010-01-31
> **devolute said:**
> I did it this way and it has screwed up my fonts and now I don't have Firefox icons, just large black crosses.

Not very good.
for me the stable ppa works perfectly fine...

---

### Post by crichard on 2010-01-31
@nanotube

> **nanotube said:**
> 

these particular instructions are ok, as in they won't screw up your machine, but since they manually link the launcher to /usr/bin/firefox, that means the next firefox update to come through the ubuntu repos will overwrite the link - not good. they should either add a dpkg-divert, or use /usr/local/bin for the link...

if you're gonna plug a blog post full of ads, at least make sure it has good instructions!

I think you missed out "Notes" part of my post, you can lock any particular package in Synaptic Package Manager to avoid duplication.(System > Administration > Synaptic Package Manager, In Synaptic Package Manager Goto Package > Lock version).

I request you to read my post fully, I've added Ubuntuzilla as an option among other methods. My post is about installing firefox from [http://mozilla.com](http://mozilla.com) (Official website) I don't criticize  any other methods too.I hope forum is for sharing our knowledge and also for learning. Anybody can follow any methods to install firefox which is convenient to them. Anyhow, Thanks for your comments. It helps me to improve my post. Really, usr/local/bin is a nice option. Thank you.:)

---

