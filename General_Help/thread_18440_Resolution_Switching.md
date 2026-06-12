---
title: "Resolution Switching"
date: 2005-03-06
forum: General Help
---

### Post by Zyk0tiK on 2005-03-06
Hey guys :)

I'm not new to linux, but i'm new to Ubuntu, and it does some strange things, let me explain :)

My monitor's refresh rates are a bit strange, so during installation of Ubuntu when it told me to select resolutions I could only chose 1024 and 800, because it specified that it would automatically use the highest one possible, and with my monitor as it is, setting a res higher than 1024 without the correct refresh rates results in no display.

so anyways, now i've configured my X config file to add 1280x960 and others inbetween and also the correct refresh rates, I reboot X, nothing. Restart the system, nothing.

All I get is 1024, why won't it show the resolutions I added?

I'm guessing Ubuntu has set something somewhere telling the system to only use the resolutions specified on install, which is UBER annoying because there's no other way that I can do it.

I tried runnin fglrxconfig but that results in making an X config file that doesn't work (what the f**k is up with that?! Package working things god damnit!!).

Is there a way to run that "please choose appropriate resolutions" thing that is in the installer again? because this is really getting tedious. I don't how how people can live with 1024, there's practically no space to do anything, and running games at 1024 is terrible, with no Anti-Aliasing in America's Army the only way to fix it is to use a higher res... Anyways, I've rambled too much :P

How can I run that thing in the installer to select resolutions without reinstalling? because my system has now been set up to suit me perfectly, and killing everything after i've spent maybe 6 or 7 hours setting it all up would just annoy the hell out of me.

Thanks :)

Steve

---

### Post by holomorph on 2005-03-07
Perhaps a little more info would be helpful like, what card/driver are you using and are you using xorg or xfree86?  If it's an NVIDIA card, with the binary "nvidia" driver, you aren't the only one having resolution issues; it might be because of incorrectly probed refresh rate values when X starts.  That was the problem I was having:
[http://ubuntuforums.org/showpost.php?p=85288&postcount=2](http://ubuntuforums.org/showpost.php?p=85288&postcount=2)

---

### Post by Zyk0tiK on 2005-03-08
Sorry, I thought mentioning fglrxconfig would make you realise it's an ATI card :) 

my bad :)

It's an X800XT Platinum Edition, 256 meg card... I'm using the fglrx driver, whenever I run fglrxconfig it makes a dead config file that Xfree (it's xfree, my bad again ;) ) can't load, XF68Config-4 file has a load of stuff in, but it doesn't work with ubuntu, it just makes the monitor flash a few times, then comes up with "Failed to load X server, to view a detailed report on why press OK" or something like that, so I mash on OK, and it just gives me a single screen saying "This is a test version of Xfree and is not supported" or something stupid like that...

In the end of all this i've just gone to Fedora Core 3, which Ideally I don't want to do, but it's the only way I can get my resolutions working properly, I can't live with 1024 :P, and the new ATI drivers with Slackware 10.1 just make my monitor load a black screen...

Man I really regret buying the ATI card... I wish i'd ignored it being the best and just gone for the top nVidia model!! :D

---

