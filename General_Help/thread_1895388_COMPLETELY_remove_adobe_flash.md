---
title: "COMPLETELY remove adobe flash"
date: 2011-12-14
forum: General Help
---

### Post by SirKingChase on 2011-12-14
I am running Ubuntu 11.10, I need to completely remove flash player from the system.  I want to use only open source alternatives, I am sick of flash.  When I goto a site I want it to tell me that I do not have flash installed. Iev uninstalled anything relating to flash in apt-get however it says that there is nothing to uninstall.  Flashplayer is still present when I goto sites.  Do I need to delete the path to where it is installed,where the .so file located?

I removed firefox and installed seamonkey thinking it wouldn't use flash and it does.  I think chrome has it embedded.  I want to strictly use GNASH, Mplayer, etc. for all my flash needs.  Iev tried flashinstaller plugin for firefox to uninstall flash and install gnash.  It claims to do it in but it does nothing, I firefox wont even agnolage.

I just recently upgraded to a geforce 9500 gt graphic card.  Flash playback in full screen is **** poor.  My onboard intel gma 950 can play full screen flash with no problems but stumbled when playing anything higher than 720p video.

With geforce 9500 I can watch 720p and 1080p movies with no problems, VDPAU works great.  My computer is an old Pentium 4 with only PCI ports.  This card is as good as it gets.  I am currently researching for an Flash alternative that will take advantage of VDPAU.  I am also looking into encoders that support OpenCL and CUDA, for transcoding.

---

### Post by seawolf167 on 2011-12-15
Have you tried to uninstall Flash through the package manager? Search for *flash* then remove/uninstall everything that you find. I'm not sure how embedded flash is into the system now, so this may have unintended side-effects.

Your alternatives are [GNU Gash ]("http://www.gnu.org/software/gnash/")and [Lightspark]("https://launchpad.net/lightspark").

Additionally, do you have drivers installed for your graphics cards? If you don't they will probably increase the full screen responsiveness.

---

### Post by SirKingChase on 2011-12-27
It is not in synaptic either.  I complied it from source and then removed the .so file (thinking I was removing it) but it is still on my system somewhere.

Does anyone know where the web browsers look for the flash files?  Or how to tell it to use something else instead?  I have gnash installed but Adobe is somehow overriding it!  

Its like flash is not detecting the geforce 9500gt and is making my CPU do all the work(which kills it), whereas before it detected the crappy GMA 945 and used that as well as CPU.

Iev tried every single Nvidia driver, Iev tried Ubuntu driver.  Flash video performs the same no matter what.  Iev concluded that its gotta be flash. So I tired all versions of flash I can find.  I compiled these from source placing the .so file where it is supposed to go.  Still no dice, but when I removed these versions the latest remained and now I am stuck with adobe flash. 

Im to the point now of giving up.  I need this card because I use MythTV all the time, but when I want to watch flash its unbearable,  I have to hook up my laptop to the TV for it to be watchable.  My plan now is to build a new computer with only ATI graphics cards and AMD processors.  Im sick of incompatible propitiatory crap from Intel.  I dont think its right that my intel GMA 945 can play full screen flash no problem but the best card for PCI slot can not?  Something is wrong with that.  I still can not believe that this is an issue, the graphics card is more than powerful enough to play it.

---

### Post by d.vanheeckeren on 2011-12-27
I ran into this problem going about a different issue but I found that this works

(Note:  some of these packages may not be installed in your system, adjust accordingly)

```
sudo apt-get remove --purge ubuntu-restricted-extras adobe-flashplugin flashplugin-installer
```

---

