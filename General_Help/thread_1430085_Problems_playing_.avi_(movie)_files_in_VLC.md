---
title: "Problems playing .avi (movie) files in VLC"
date: 2010-03-14
forum: General Help
---

### Post by cAlpha on 2010-03-14
I can play .avi files in Ubuntu Movie Player, but attempting to open them in VLC stalls--a VLC window opens up, but shuts down immediately thereafter and never plays.  I also tried playing an mp3 file and it works fine, so it seems to be movie media specific.  

I've made sure I've got all applicable updates.  Any other thoughts on what could be causing this?  Are there some other codecs I might need?

---

### Post by akakingess on 2010-03-14
I won't be much help, but I can honestly say that I have never had a problem playing back just about anything with VLC (which is why it's my app of choice), and I know I have played plenty of AVIs with it.

---

### Post by theiron on 2010-03-27
I found and used the following command from another thread, fixed all of my DVD issues:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

Copy and paste into a terminal window, and should Java ask for permission, give it.  All of my DVD play back now.

---

### Post by akakingess on 2010-03-27
```

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
```

I tried that command (via copying and pasting into Terminal) and entered my password, but it never asked for permission and gave me this error, so I was just wondering if you had any thoughts.?.. I know I said I had never had a problem, but I figured maybe I hadn't encountered some of those codecs yet, so why not, and then it didn't go through, just hoping that I don't have bigger issues that are unknown as of yet.

---

### Post by thegod_slayer on 2010-03-27
i hope you might just uninstall and re-install the vlc.
i hope it might work, maybe installation problem.

---

### Post by cAlpha on 2010-03-27
> **theiron said:**
> I found and used the following command from another thread, fixed all of my DVD issues:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

Copy and paste into a terminal window, and should Java ask for permission, give it.  All of my DVD play back now.

Yeah, I saw that too in the other thread I posted.  For me, I'm now able to view DVDs in Mplayer, but they still don't work in VLC.  Kind of a headache, but at least it works in Mplayer...

---

### Post by akakingess on 2010-03-27
I guess I will just leave it as is, as I posted earlier I have not had any issues playing just about anything within VLC, so don't fix it if it ain't broke, right? Well, I will see how long until I need that W32 codec ;)

---

### Post by akakingess on 2010-03-27
> **cAlpha said:**
> Yeah, I saw that too in the other thread I posted.  For me, I'm now able to view DVDs in Mplayer, but they still don't work in VLC.  Kind of a headache, but at least it works in Mplayer...

Any way you could look in the 'codec' folders for those respective programs, and if you see one within MPlayer that's not in VLC's (not sure if it would be local or global), maybe just create a quick symlink and try it out? That would be something I would try at home if I were having the same issue...

---

### Post by cAlpha on 2010-03-27
Do you know where the respective codec folders are located for VLC and Mplayer?

---

### Post by akakingess on 2010-03-28
Not 100% sure, but locally would be somewhere in the .mplayer and .vlc folders within your home folder (be sure to view 'hidden' files) and globally would be wherever they store the global settings for those 2 programs, sorry, don't have the time to investigate myself right now, but might in about an hour or so, let me know if you find them, also, there may not be a seperate 'codec' folder, or it could be called something else, but they (the codecs) would be wherever the settings (.conf or whatever, etc.) are stored.

---

### Post by asmoore82 on 2010-03-28
You can "reset" all of your VLC settings like this:
```
mv "$HOME/.config/vlc" "$HOME/.config/vlc.backup"
```

I find that I have to do this every so often because I like to tweak ;).

---

### Post by akakingess on 2010-03-28
So it's like a firefox profile in that if you just delete it (I know you are actually backing it up, but technically you are just deleting/moving the config file) it will create a new one upon launch? What does that say of codecs and the like, though?

---

### Post by thanuja on 2010-03-28
Whats the version your are using. If it is kubuntu 8.1, just go to add/remove software and search for VLC and install. It worked perfeclty fine for me.

---

### Post by asmoore82 on 2010-03-28
> **akakingess said:**
> So it's like a firefox profile in that if you just delete it (I know you are actually backing it up, but technically you are just deleting/moving the config file) it will create a new one upon launch? What does that say of codecs and the like, though?

Yes, on the next launch, VLC will re-create this folder and re-ask you about automatic download policy.
Any codecs that were installed via a package manager are safely located somewhere else in system files.
This is one of the many reasons that the Unix way of strict separation
between system files and user files is highly superior.

---

### Post by akakingess on 2010-03-28
Although I understand what you are stating, I am curious, does that mean that all Codecs are installed globally? If not, then where is the line drawn between system and user files?

By the way, I am not trying to start an argument/debate, just trying to learn where lines are drawn within Unix...

---

### Post by jocko on 2010-03-28
> **akakingess said:**
> Although I understand what you are stating, I am curious, does that mean that all Codecs are installed globally? If not, then where is the line drawn between system and user files?.
Yes. The package manager installs everything globally, including codecs.
It would be silly if the package manager installed things to your home directory (there would have to be several copies of everything, one in every users home directories plus one somewhere in the system to be able to copy into the users home directories... And if there would be an update to a package, how would the package manager handle your local files? And other users local files? Overwrite them with the new ones, possibly overwriting files that you have placed there manually or leave the home directory alone? Either way would cause problems).

You can still install codecs locally if you want to (works for mplayer, but I'm not sure if vlc would use them. Doesn't vlc come with it's own codecs?)

**To the op:** If vlc can't play any video files, the problem is not with missing codecs. The default install of vlc comes with support for all common video codecs I have ever encountered. And in the few cases where an obscure codec is missing, vlc will give you a message about exactly which codec it can't find (such as: "No suitable decoder module:
VLC does not support the audio or video  format "vo3+". Unfortunately there is no way for you to fix this.").

The only thing I can think of is that something is wrong with your configuration of vlc. Delete or rename your ~/.config/vlc directory and let vlc re-generate it.

---

### Post by akakingess on 2010-03-28
Sorry, but again we are referring to the package manager, which of course would do everything globally, but it can't do everything (some codecs, Flash, Java, etc.) which is why I was asking. Obviously, it would be silly for a system-wide package manager to do things other than profile/user specific locally, but I guess I was curious about the possibilities/problems with other plugins, apps, whatever and why if Unix/Linux is so "ideal" it is still having some difficulty with those that have been out for years. Don't take it the wrong way, I wouldn't be in this forum or have Linux installed on 4 out of my 5 machines if I thought it was a poor OS, just trying to find out why we can't have more universal additions easier to access. Thanks for all of your input, and please don't take any disrespect from my humble opinions. Good night for now, see y'all tomorrow!

---

### Post by theiron on 2010-08-15
That command stream that I posted seems to be good only for the Karmic Koala, Ubuntu 9.10  Sorry that I kinda dropped off the face of the earth, but I've been too busy until just lately to play around in Linux.

I've since decided to upgrade to the Lucid Lynx, Ubuntu 10.04 LTS.  That command stream is broken now, it can't find the medibuntu.org site.

So, I'm back on the hunt for the right codecs to make VLC work.  Funny thing, I did a fresh installation of Lucid Lynx Netbook on the Dell laptop that I'm working on right now,  It will not play prerecorded TV series, and I've not tried anything else just yet.

On MY Dell Inspiron 1520, I've got the 10.04 Desktop rev running, cuz with a dual core CPU and 2 GB of RAM, it rivals most desktops that I've seen.  There, it has no problems, it was a rolling upgrade from a fully tweaked Ubuntu 9.10, and it seemed to take all of the nuances into 10.04 as it installed.

PS... I await the 10.10 release of the Lynx, it is projected to support Blu-Ray playback, and at that point I will be ditching Windows for good!

---

