---
title: "Shockwave"
date: 2010-09-04
forum: General Help
---

### Post by Scunnered on 2010-09-04
I have been told that I need flash & shockwave to view a web site but on checking it appears that shockwave is not available in Linux.  The posts that I found when googling were a bit historical and I wonder whether there is any improvement in the availability.

I only have the capability of using Ubuntu on my system as it was purchased as a Linux system.  I have seen remarks about using wine but as I am unable to load Windows on this system this is a no go.

Is there any hope for me or do I have to mug the proverbial little old lady for her Windows laptop.

Your assistance will be appreciated

---

### Post by lykeion on 2010-09-04
> **Scunnered said:**
> I have seen remarks about using wine but as I am unable to load Windows on this system this is a no go.
What do you mean by this? That you cannot install wine? It should be as simple as launching this command from a terminal:```
sudo apt-get install wine
```I haven't tried this myself, but you could try to install win version of firefox in wine, and then install the **shockwave** plugin.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by ellgor on 2010-09-04
Hi,

I found this guide that worked for me, its for a 64bit so look for the 32bit if needed:

ote: When I did this it removed a whole bunch of things (around 80) nothing seems to have been affected two days on.

1. Remove your current flash install if you have it:
Code:

sudo aptitude remove flashplugin-installer

2. Add the ppa to your sources list. There are several ways to do it so choose your favourite, but to use command line do this:
Code:

sudo add-apt-repository ppa:sevenmachines/flash

3. Update apt and install Flash 64 bit: (change to 32bit if needed)
Code:

sudo aptitude update
sudo aptitude install flashplugin64-installer

4. Restart Browser

It got mine working a treat.

Regards, Ellgor.

---

### Post by lykeion on 2010-09-04
Regarding the **flash** plugin you shouldn't need any external PPA like above poster says. It's in the Ubuntu partner repository.
Enable partner repository:
Synaptic > Settings > Repositories > Other Software tab > check partner repository (at top)
Click Reload
Install package adobe-flashplugin

---

### Post by Scunnered on 2010-09-05
**lykeion**

Many thanks for your reply.

From memory I loaded wine OK but on attempting to put XP on it failed miserably.  I then attempted to dual boot with XP only to find that the BIOS did not like Windows.  How surprising !!!

I will have a look at installing Wine but wonder if I attempt to load Firefox on Wine will it be accepted without Windows running?

I am very happy to be like my BIOS so if I can't get shockwave then I will do without.  This is unless you know a little old lady !

---

### Post by pbrane on 2010-09-05
you do not need (nor can you, IIRC) install windows in wine. wine is a (almost) complete replacement for windows. You should be able to install firefox for windows using wine. something like **wine firefox-sintaller.exe** in a terminal. Then you can install shockwave. 

You can also install firefox for windows using nautilus by right clicking on the downloaded installer and choose open with wine.

Also the flash-plugin in the repos is 32-bit flash. if you want the 64-bit version you'll have to install it manually.

---

### Post by Scunnered on 2010-09-05
**pbrane**

I have had a look at your suggestion.  Copied text supplied and provided password only to have the following displayed :

**wine: /home/ian/.wine is not owned by you**

Where should I go from here ?

---

### Post by pbrane on 2010-09-05
did you download the windows firefox installer? if so you should be able to run it by prefacing the command with wine. You should make sure you use the installer name and not the one I supplied. I have no idea what the real installer is called. I don't have wine installed, I'm not using any windows apps.

try finding the installer in your file manager (nautilus in GNOME) and try right clicking on the installer. There should be an option to open with wine. 

About that error message, I'm not sure why $HOME/.wine would not be owned by you. I'm pretty sure that when I had wine installed $HOME/.wine was owned by me. You should not have to install anything as root in wine.

I downloaded the windows installer. it's called **Firefox Setup 3.6.8.exe** so you should be able to run it from the file manager or from a terminal like this:
```

 wine Firefox\ Setup\ 3.6.8.exe

```
you should not be asked for your password, I don't ever remember having to provide my password for an install in wine.

---

### Post by Scunnered on 2010-09-05
**pbrane**

I am getting nowhere fast on this.  I think that I shall mug the little old lady after all.

When I attempt to load the firefox for windows from Mozilla I keep getting told that it is an .exe and is dangerous.  Attempting to open with wine I still am locked out.

I will see what develops when I check further on being blocked out and hope that I can get it working.

My thanks for your assistance

---

### Post by keypox on 2010-09-05
Is  the 64bit version better if you are running 64 bit buntu?

---

### Post by Scunnered on 2010-09-05
**keypox**

When I had problems with the BBC iPlayer I was given this advice in post No 9.

[http://ubuntuforums.org/showthread.php?t=1468743](http://ubuntuforums.org/showthread.php?t=1468743)

This may be of assistance to you

---

### Post by pbrane on 2010-09-05
Well, I just installed wine
```

sudo aptitude install wine

```

then I downloaded the firefox installer for windows. I got the warning about '.exe' being dangerous too. Then I typed 
```

wine Firefox\ Setup\ 3.6.8.exe

```
in the same terminal I used to install wine. And the windows version of firefox installed. It should be that simple for you too. 

Did you install wine from the ubuntu repos?

---

### Post by Scunnered on 2010-09-05
**pbrane**

I don't know what has happened but somehow you have enabled me to achieve my aim.  Despite all the error messages etc etc I went back to the site I was attempting to access in order to see if there was anymore information I could impart.  Lo and behold instead of it blowing the proverbial raspberry at me the site worked.

Please don't ask me to explain how it happened as I have no idea however I am very happy at the end result.

You must be a magician.

My sincere thanks

---

### Post by keypox on 2010-09-05
> **Scunnered said:**
> **keypox**

When I had problems with the BBC iPlayer I was given this advice in post No 9.

[http://ubuntuforums.org/showthread.php?t=1468743](http://ubuntuforums.org/showthread.php?t=1468743)

This may be of assistance to you

Thanks im gonna try the 64 bit version.  Hopefully hulu will run in fullscreen, without hacks.

Edit:  LOL wont even play hulu, says not supported with 64bit versions of flash.  O well...

---

### Post by scouser73 on 2010-09-05
> **Scunnered said:**
> I have been told that I need flash & shockwave to view a web site but on checking it appears that shockwave is not available in Linux.  The posts that I found when googling were a bit historical and I wonder whether there is any improvement in the availability.

I only have the capability of using Ubuntu on my system as it was purchased as a Linux system.  I have seen remarks about using wine but as I am unable to load Windows on this system this is a no go.

Is there any hope for me or do I have to mug the proverbial little old lady for her Windows laptop.

Your assistance will be appreciated

Shockwave isn't available for Linux.

---

### Post by pbrane on 2010-09-06
> **keypox said:**
> Thanks im gonna try the 64 bit version.  Hopefully hulu will run in fullscreen, without hacks.

Edit:  LOL wont even play hulu, says not supported with 64bit versions of flash.  O well...

Wow, this must be something new! I was watching some old TV shows on hulu last month on my 64-bit flash. But you're right, hulu won't work on 64-bit flash now.

Wait, some movies still work. Advertisements too, of course. Looks like some of the older TV shows will play.

> **scouser73 said:**
> Shockwave isn't available for Linux.
That's why he was trying to use firefox for windows under wine.

---

