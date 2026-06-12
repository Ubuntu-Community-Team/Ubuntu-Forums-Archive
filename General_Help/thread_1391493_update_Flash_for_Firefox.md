---
title: "update Flash for Firefox"
date: 2010-01-26
forum: General Help
---

### Post by okhowaboutthisusername on 2010-01-26
FF has been segfaulting tonight and it appears to be caused by Flash. See [this thread]("http://ubuntuforums.org/showthread.php?t=1391476"). Or, at least, Flash is involved somehow.

I thought I should start a new thread to ask about updating. I'm a recent convert from Fedora and some things are still a bit confusing.

So I tried updating the plugin yb going to Tools->Add-ons->Plugins and clicking "Find Updates". I'm told that my version (Shockwave Flash 10.0 r32) is outdated and so I head over to Adobe's site. They're offering "Adobe Flash Player version 10.0.42.34" and I select "APT for Ubuntu 9.0.4+". When apt-url launches, it prompts me to join something called the "9.10 Partner Channel". I do so and apt-url downloads 57 files, then announces, "Could not find package 'adobe-flashplugin'."

So, I'm wondering what the heck is going on here. Why would apt-url prompt me to join this package group if the software I'm looking for isn't offered?

Secondly, is there some other place to get this from? Like, Adobe, maybe?

I realise that I can download a tarball, but I'm pretty fresh with Ubuntu still and only a hazy idea where I should install things to.

---

### Post by michael37 on 2010-01-26
> **okhowaboutthisusername said:**
> FF has been segfaulting tonight and it appears to be caused by Flash. See [this thread]("http://ubuntuforums.org/showthread.php?t=1391476"). Or, at least, Flash is involved somehow.

I thought I should start a new thread to ask about updating. I'm a recent convert from Fedora and some things are still a bit confusing.

So I tried updating the plugin yb going to Tools->Add-ons->Plugins and clicking "Find Updates". I'm told that my version (Shockwave Flash 10.0 r32) is outdated and so I head over to Adobe's site. They're offering "Adobe Flash Player version 10.0.42.34" and I select "APT for Ubuntu 9.0.4+". When apt-url launches, it prompts me to join something called the "9.10 Partner Channel". I do so and apt-url downloads 57 files, then announces, "Could not find package 'adobe-flashplugin'."

So, I'm wondering what the heck is going on here. Why would apt-url prompt me to join this package group if the software I'm looking for isn't offered?

Secondly, is there some other place to get this from? Like, Adobe, maybe?

I realise that I can download a tarball, but I'm pretty fresh with Ubuntu still and only a hazy idea where I should install things to.

What's your version of Firefox?  Please post help/about.

---

### Post by scouser73 on 2010-01-27
> **okhowaboutthisusername said:**
> FF has been segfaulting tonight and it appears to be caused by Flash. See [this thread]("http://ubuntuforums.org/showthread.php?t=1391476"). Or, at least, Flash is involved somehow.

I thought I should start a new thread to ask about updating. I'm a recent convert from Fedora and some things are still a bit confusing.

So I tried updating the plugin yb going to Tools->Add-ons->Plugins and clicking "Find Updates". I'm told that my version (Shockwave Flash 10.0 r32) is outdated and so I head over to Adobe's site. They're offering "Adobe Flash Player version 10.0.42.34" and I select "APT for Ubuntu 9.0.4+". When apt-url launches, it prompts me to join something called the "9.10 Partner Channel". I do so and apt-url downloads 57 files, then announces, "Could not find package 'adobe-flashplugin'."

So, I'm wondering what the heck is going on here. Why would apt-url prompt me to join this package group if the software I'm looking for isn't offered?

Secondly, is there some other place to get this from? Like, Adobe, maybe?

I realise that I can download a tarball, but I'm pretty fresh with Ubuntu still and only a hazy idea where I should install things to.

[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by michael37 on 2010-01-27
> **scouser73 said:**
> [COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

Good instructions for 32-bit Firefox.

**Will not work** for 64-bit Firefox.

Please clarify in the future.

---

### Post by khelben1979 on 2010-01-27
I think you just should download the tar ball. Extract it in /home/[user]/plugins/. Restart Firefox.

Done.

---

