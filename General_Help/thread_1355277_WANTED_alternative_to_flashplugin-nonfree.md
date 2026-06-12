---
title: "WANTED: alternative to flashplugin-nonfree"
date: 2009-12-14
forum: General Help
---

### Post by jhsu802701 on 2009-12-14
I have a minimal installation of Ubuntu Hardy Heron, and I'm looking for an alternative to the flashplugin-nonfree package that kept crashing my browser (both Firefox and Epiphany).  What are the alternatives?

---

### Post by lewisforlife on 2009-12-14
As far as I know there are no alternatives.  I don't think there are any real viable alternatives.  Flash is closed source, and is not an open format, nor does it follow any industry standards.  I have seen the following, but I don't think they are real alternatives yet, I think they are in the infant stage:

[http://www.osflash.org/](http://www.osflash.org/)
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by jhsu802701 on 2009-12-14
So how do you view Flash animations and videos (like Youtube) in Ubuntu?  I'm sure a distro this widely used has to have a way.  Puppy Linux's Flash package works fine.

---

### Post by jbrown96 on 2009-12-14
There's opensource versions called swf (i think the full package is mozilla-plugin-swfdec or something similar) and gnash. You can try searching and installing them from Synaptic. You need to have the browsers closed when you installed them, and be sure to remove flash first.

I'm going to warn you that they don't work very well. As the previous poster said, flash is proprietary, and no one has reverse engineered it very well.

---

### Post by jhsu802701 on 2009-12-14
> **jbrown96 said:**
> There's opensource versions called swf (i think the full package is mozilla-plugin-swfdec or something similar) and gnash. You can try searching and installing them from Synaptic. You need to have the browsers closed when you installed them, and be sure to remove flash first.

I'm going to warn you that they don't work very well. As the previous poster said, flash is proprietary, and no one has reverse engineered it very well.

Is there ANY good way to get Flash working in Ubuntu?  The Puppy Linux package for Flash works great.  I'm surprised that Ubuntu hasn't just copied Puppy Linux.

---

### Post by llamabr on 2009-12-14
> **jhsu802701 said:**
> Is there ANY good way to get Flash working in Ubuntu?  The Puppy Linux package for Flash works great.  I'm surprised that Ubuntu hasn't just copied Puppy Linux.

They're the same packages.  There's no trouble with the free flash plugin.  Most of the rest of us use it just fine.  You have some specific problem that you need to overcome.  You say it's crashing your firefox?

Try:

```
mv .mozilla .mozilla.save
```

and open firefox.  That will begin with fresh config files.  If it works, there's some conflict in something else you've installed.  If not, we'll need more info to help you.

---

### Post by fluffman86 on 2009-12-14
flashplugin-nonfree works fine for me.  You'll be better off looking for a way to fix it than looking for a replacement.  Sorry I can't help without better information.

edit: llamabr's suggestion is a good place to start.

---

### Post by jhsu802701 on 2009-12-14
OK, I installed the flashplugin-nonfree package.  I deleted the .mozilla directory again, and I rebooted.  But when I go to a Youtube video, I get the message "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/")."  But JavaScript and Java are both enabled.

What now?

---

### Post by llamabr on 2009-12-14
Strange.  Why are you running hardy?  And what sort of computer is this?

---

### Post by FreezWay on 2009-12-14
hmmm it works from me fine on chrome. i installed with

sudo apt-get install ubuntu-restricted-extras
it will also install things like mp3 codecs etc.

are you on 32 or 64 bit?

---

### Post by MooPi on 2009-12-14
I install flash the same way on every Linux computer I use. Download flash for 32 bit from adobe: [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz%29]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz%29")
Open terminal and type  ```
cd .mozilla
```  ```
mkdir plugins
```Now go to where you downloaded flash from adobe and extract the file which should be libflashplayer.so.
Open terminal and type  ```
cp libflashplayer.so ~/.mozilla/plugins
```Restart Firefox and flash should work. Granted this procedure is on a clean system without any prior flash install. The above procedure works on 32 bit as well as 64 bit. Download for 64 bit:[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by jhsu802701 on 2009-12-14
> **FreezWay said:**
> hmmm it works from me fine on chrome. i installed with

sudo apt-get install ubuntu-restricted-extras
it will also install things like mp3 codecs etc.

are you on 32 or 64 bit?
I think I'm on 32-bit (i386, Dell L466CX desktop).

I downloaded and installed ubuntu-restricted-extras, but Youtube STILL refuses to play videos, and I still get that error message.

What exactly is the mechanism that allows Flash to work?  I have absolutely no idea what I'm doing.  At least when I installed the flashplugin-nonfree package the first time, Youtube worked for the first few seconds.  Now it doesn't work AT ALL.

---

### Post by jhsu802701 on 2009-12-14
I've tried more methods, and none of them work.  I tried the dpkg -i *.deb on the downloaded Flash installation file that the Firefox browser directed me to, only to get error messages about dependencies not met.  I tried the the apturl method in [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html), but that didn't work either.

I can't believe that there can be so many ways to install Flash but for none of them to work.  Now I'm even wondering if I messed up my system somehow during previous unsuccessful attempts.  I have no idea how to troubleshoot the Flash mechanism, because I have no idea how it works or what long chain of mechanisms is needed to make it all work.  What should I do?

---

### Post by PRC09 on 2009-12-15
Try the following link and scroll down to the section on flash.....


[http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization](http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization)

---

### Post by Defrector on 2009-12-15
For the sake of the possibility that you might be running in 64-bit land and not knowing it, try running the following in a terminal:

```
ps -A | grep "npviewer.bin"
```

If you get a list of items such as "npviewer.bin" and "npviewer.bin.re", you may benefit from closing your browser and doing the following in the terminal:
```
killall npviewer.bin
killall npviewer.bin.re
```

..and restart your browser. I got this suspicion when you said that flash was running for a few seconds then failed. That often happens when npviewer.bin glitches out.

If that does not work try rebooting and see if flash works again. Whether or not it works may be a clue as to what is wrong. Post the results of the reboot (if the above doesn't fix it)

---

### Post by jhsu802701 on 2009-12-15
I tried "ps -A | grep "npviewer.bin" but got no messages (error or otherwise) whatsoever.  Does this mean that my computer is 32 bits and not 64?

Flash worked for just the first few seconds the first time I installed the flashplugin-nonfree package.  In an attempt to get Flash working, I uninstalled that package and tried various other things, which were unable to get Flash working AT ALL.  I have no idea about the state of my current OS, and I may have messed things up in later unsuccessful attempts to get Flash working.  I have no idea what long chain of events is needed for Flash to work, so I can't even troubleshoot properly.

---

### Post by Defrector on 2009-12-15
The lack of hung or running npviewer.bin implies that your problem probably isn't caused by a wrapper malfunction. Seeing that you have tried many flash plugins, it sounds like you might have a messy install. Try closing your browser(s) and reinstalling the flashplugin-installer. The following code uninstalls things which might not actually be on your machine, so those errors would be harmless. It then reinstalls flash plugin:

```
killall firefox
sudo apt-get remove flashplugin-installer flashplugin-nonfree mozilla-plugin-gnash gnash-common gnash
sudo apt-get install flashplugin-installer
```
..then restart firefox and test.

If this doesn't work, more info would be needed.

To officially find out the version/type of your linux installation, there is this command:
```
uname -a
```

In Firefox, typing the URL:
```
about:plugins
```
Will get you a listing of all plugins loaded into Firefox. Look for the entry "Shockwave Flash" or similar. For example, mine says:
> Shockwave Flash

    File name: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r42

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player

Another thing to do to get a current consensus on where your flashplayer files are, in the terminal:
```
sudo updatedb
locate libflashplayer.so
```

---

### Post by jhsu802701 on 2009-12-15
The output of "sudo apt-get install flashplugin-installer" was:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-installer has no installation candidate

The output from "uname -a":
Linux dhcppc1 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Going to "about:plugins" showed no Flash plugins whatsoever.

The output of "sudo updatedb" followed by "locate libflashplayer.so" was:
/usr/lib/adobe-flashplugin/libflashplayer.so

What does all this mean?  What do I do next?

---

### Post by oldos2er on 2009-12-15
You could try ```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/
```
Then restart Firefox.

---

### Post by fluffman86 on 2009-12-15
yeah, flashplugin-install is not available in Hardy.

Maybe you have have javascript disabled?  Edit > Preferences > Check "Enable Javascript" > Click "Advanced" > Uncheck everything.

---

### Post by jhsu802701 on 2009-12-15
> **oldos2er said:**
> You could try ```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/
```Then restart Firefox.

Youtube still refuses to play videos for me.  I feel like I'm so tantalizingly close to having it working, yet 99% isn't good enough.

---

### Post by Defrector on 2009-12-15
It appears that you are indeed running a 32-bit OS and that's fine.
No flash plugins in ```
about:plugins
``` means that firefox is not detecting the plugin.
My recollection on Hardy's flash installers is poor so there is a limit to how much I can help.

If you are still experiencing problems after performing the cp command given by oldos2er also try this:
```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins/
```

..this also copies the plugin to your home's mozilla plugin directory.
After restarting firefox, check to see if your ```
about:plugins
``` registers the flash plugin.

If things still aren't working, here are some more questions:

When at YouTube, does it tell you that you do not have flash, out-of-date version of flash, or does it give an empty box where the flash should be? Any messages? Errors? Crashes?

Do other sites with flash work? Any errors?

What is the output of:
```
file /usr/lib/adobe-flashplugin/libflashplayer.so
```

Hang in there. Adobe's Flash ports to linux are notoriously sketchy and do not represent how things are for GNU/Linux/Ubuntu.

---

### Post by mkvnmtr on 2009-12-15
Do you by chance have the No-script ext enabled?. 
If you have no luck with your flash there is an app that can view utube without flash. It gives me a better picture than flash. It is called Minitube and you can get it on the Get Deb site, Works best in 9.10.

---

### Post by jhsu802701 on 2009-12-16
> **Defrector said:**
> It appears that you are indeed running a 32-bit OS and that's fine.
No flash plugins in ```
about:plugins
``` means that firefox is not detecting the plugin.
My recollection on Hardy's flash installers is poor so there is a limit to how much I can help.

If you are still experiencing problems after performing the cp command given by oldos2er also try this:
```
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins/
```..this also copies the plugin to your home's mozilla plugin directory.
After restarting firefox, check to see if your ```
about:plugins
``` registers the flash plugin.

Thanks, Defrector.  Flash now works, and I can view Youtube videos.

---

