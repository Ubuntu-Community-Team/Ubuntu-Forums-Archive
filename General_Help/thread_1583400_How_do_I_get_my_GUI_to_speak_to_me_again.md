---
title: "How do I get my GUI to speak to me again?"
date: 2010-09-27
forum: General Help
---

### Post by JustGus on 2010-09-27
I recently [posted]("http://ubuntuforums.org/showthread.php?p=9879357") after my system failed to boot properly, leaving me with the dreaded "Ubuntu is in low-graphics mode" box and access only to the console.

I've not gotten any suggestions on how to rectify this and am keen to get my system back up and running.  I've tried to find similar issues posted to see if that would fix the problem and one of the suggestions has been to roll back the system to an earlier state.  

As I'm without a GUI, can anyone out there explain how to do this from the console?  (Or, if anyone knows how to fix the low-graphics mode problem as it relates to my [earlier post]("http://ubuntuforums.org/showthread.php?p=9879357"), I'm all ears)

Thanks for any suggestions!  I'm missing my Ubuntu media player!

---

### Post by Jonny87 on 2010-09-27
Not 100% sure if it applies to your situation but to try getting a GUI you could try one of the following.

```
startx
```
```
sudo service gdm start
```

---

### Post by JustGus on 2010-09-27
Thanks for the suggestion.

Had a go and it kicks me back to "Ubuntu is in low-graphics mode".

I wonder if it's bad mojo going with the xserver-xorg config file, given this [reference]("http://i52.tinypic.com/2dj5su0.jpg") on one of the screens I get when I tried to boot.

I've had a look at wiki.x.org, but wasn't able to figure out what to do.

---

### Post by Jonny87 on 2010-09-27
I know its possible to configure a an Xorg file, this may work and alow you to run startx. I'm no expert on the this so feel free to get a second opinion on the matter. If you would like to give it a try though here are some notes that I have on it. 

> Now we need to generate the xorg.conf file. It seems that this does not seem to work with sudo. So issue the command: sudo -i to obtain a root command prompt then Xorg -configure. Note the case sensitivity. This will generate a new file in ~/xorg.conf.new (i.e. in the root user's home directory). Edit this if required.  

Copy this file to /etc/X11/: cp ~/xorg.conf.new /etc/X11/xorg.conf  

After moving this file to the proper location you can start the X again and see what happens: sudo service gdm start or simply type startx. (There should be no difference unless you have had to change some settings in xorg.conf to (say) alter the screen resolution).

---

### Post by 3Miro on 2010-09-27
Try this:
```
 sudo dpkg-reconfigure xserver-xorg  
```
This should revert the graphical environment back to original state. Then reboot.

If this doesn't help, tell use what kind of graphics card you have.

---

### Post by JustGus on 2010-09-28
Thanks to both of you for your help!

Jonny - I followed your instructions, redoing the config and I managed to get into the GUI.  From there something weird happens, which might explain the origin of the problem.   When I tried to install the updates, I got a message saying my HDD was full.  That seemed very strange, as the machine is used solely as an audio server, which should only be half full.  I rebooted, but came up against the "Ubuntu is running in low-graphics mode" box.

So I tried 3Miro's suggestion, but no joy, so I went through Jonny's suggestion again.  Again, I was able to access the GUI and had a look at the Properties of the HDD and found that the media folder had swelled, taking up most of the capacity.  As I mentioned before, this seemed odd, as my ripped CD collection takes up no where near the full capacity of the drive (incidentally my Music folder sits in the "home" folder, not the "media" folder.  Here are screenshots of what I found:

Firstly, a single folder lies just below the media folder, which has a title that's a string of numbers:
[IMG]http://i54.tinypic.com/15mek94.jpg[/IMG]

Within the media folder, are further folders, which appear to be created automatically on a periodic basis (as they're dated):
[IMG]http://i51.tinypic.com/2nauptw.jpg[/IMG]

One of the sub-folders, which is typical of the contents of the remaining folders has various small files and a gynormous tarball in it (132gb!).  The accumulation of these across the subfolders has taken up all the drive space.
[IMG]http://i51.tinypic.com/or04ya.jpg[/IMG]


I have no idea what these are, or whether simply deleting them will toast my system.  I've not installed them.  If anyone can can make sense of where these are likely to have come from I'd be interested to know (e.g. did a backup system get turned on somehow; does it look like the result of some kind of virus...) 

If anyone more experienced can offer more info before I do this, as well as a plausible explanation for what's happening, it would be helpful!

EDIT --- 
On reflection, I figured that items in the media folder could probably be thrown in the trash without ill effect, so I've gone ahead and deleted one of the folders to free up space.

THE GREAT NEWS IS THIS HAS CORRECTED THE PROBLEM!  Thanks to your suggestions, I'm back in business!

That said, I'm still very interested in any possible explanations for how the mystery folders were created and what I need to do to stop them from being created.

---

### Post by 3Miro on 2010-09-28
My "solution" was simply aimed at the graphical environment, it will have no effect on HDD space.

Now on the second problem. Without trying to expose any private information, there is something on the screenshots that I don't understand. The folders that you are showing are in /media/something. The only things that you should have in /media should be links to other partitions/usb/cdrom/external hdd. Everything should physically be somewhere else and it should not affect the main Ubuntu partition /.

As for the gigantic tarballs, can you open them to see what is in it. This may give us clue on what caused the issue, maybe it is a buggy program.

---

### Post by JustGus on 2010-09-28
3Miro - Will investigate and post more this evening (am at work), but have encountered some issues this morning when I booted up the server.

As I mentioned this machine is used solely as an audio server, which interacts with some media clients - in this case [Sqeezeboxes]("http://www.vistra.com.au/logitech/squeezebox.html").  

I booted up the server this morning and the players lit up, but all their configs had gone back to the factory settings and while I was able to get the server on using Wake on LAN, once the machine booted up, the players didn't connect to the server itself.  They were unable to find the Music folder, which usually happens automatically.  

Will post more this evening...  Thanks for you help!

---

### Post by JustGus on 2010-09-29
So, I've now had a look at the media folder and opened one of the tarballs. Each of the folders is quite different. Some have tarballs. Others don't. Some tarballs are large (132gb).  Others are small (2gb).  I can't see any sort of pattern to them.  I  think they *might* be formed at the time that I install updates onto my system.

When I try to open the larger ones they take forever, but after 15-20 minutes I finally get an error message: 
> gzip: stdin: unexpected end of file.
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

The other interesting thing is that my Squeezebox media server interface is totally up the spout.  I typically use a web interface (using localhost on  port 9000).  Now when I try to access it I get a message "Unable to connect. Firefox can't establish a connection to the server at localhost:9000.  
I've no idea why/how this would have changed all the settings!

Very weird.  I wish there was some way I could wind back the clock to an earlier set of settings! Is there?

---

