---
title: "Ubuntu Virgin (Run for the Hills Ye Knowledgeable Ones)"
date: 2006-02-27
forum: General Help
---

### Post by Xaviar on 2006-02-27
Fleeing from the proprietary technology tyranny the last remaining mascot, the Penguin, leads a rag-tag fugitive network in search of a shining operating system...known as Ubuntu.  
Hello all.  Following yet another collossal system splatterfest from Windows XP, I made use of the live CD and have installed Ubuntu as my sole operating system.  I have no programming skills and am used to drag & drop functions for my day to day computer work.  I have found Ubuntu a mixed blessing (though it's early days yet).  I have managed to use the Synaptic Manager to install Thunderbird (my preferred e-mail client) but it has installed an earlier build than I am used to so there are certain plug-ins that are not compatible (such as allowing no subject heading).  Before I figured out how to bumble through the Synaptic Manager I managed to download the latest T-Bird to the Desktop and run it from there but I want it to run from "inside" the system if you know what I mean.  As a result I uninstalled it and have gone with what the Synaptic manager gave me but have no idea how to get T-Bird to update itself.  Any ideas?

I also have torrented my first file on the new OS and get only video playback (no audio) using Totem.  At first Totem wouldn't play the file at all but following some hints from the web I got it running the video but without sound.  The file in question is an Xvid Microsoft AVI file (MIME type:video/x-msvideo).  Most of the sites I've looked at quote a single string of text or another and I have no idea what it means or where it goes - I really am new at this and I don't want to give up and slink back Gatesville so any baby-food help anyone would give me would be much appreciated.

I also have trouble getting the system to recognize a second hard drive and have no idea how to go about it.

Less important is an issue with themes.  How do I adjust the pallette?  I know how to select from the installed themes but I don't care too much for them and I cannot adjust their colours.  I am currently running Firefox & Thunderbird with their PitchDark theme and am hoping to give my Ubuntu a matching theme.

Any assistance you could give would be great and please speak slowly, as though you're talking to an idiot whom has no idea what he's doing.  I'd like to really make a go of Open Source computing.  Thanx for listening (well..reading).

P.S: I have installed Xine but it too delivers video and no audio.

---

### Post by aysiu on 2006-02-27
Synaptic Package Manager will never be more than six months behind the latest releases of software.

I think the upcoming release of Ubuntu (Dapper Drake--scheduled for April 2006) has Firefox 1.5 and Thunderbird 1.5

In the meantime, you have two options:
1. Use Thunderbird 1.0.7 until April
2. Follow these simple instructions (all you need to do is copy and paste commands): [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

What filesystem is your second hard drive? NTFS? FAT32?

For the videos, you may need to install certain proprietary codecs:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

For themes, go to [http://www.gnome-look.org](http://www.gnome-look.org) and look for Gtk themes, download them to your computer, and drag and drop them to your Theme Manager window (System > Preferences > Themes). Do not unzip the themes--keep them in their .tar.gz form.

P.S. I noticed you're posting in the Hoary section, so your Thunderbird may be even older than 1.0.7.

The releases are as follows:

October 2004--Warty
April 2005--Hoary
October 2005--Breezy
April 2005--Dapper

Breezy is the most up-to-date version.

---

### Post by ekarni on 2006-02-27
Regarding the sound (or lack thereof):  are you getting sounds for other things, just not the videos?  An easy way to check is go to System menu -> Preferences -> Sounds, Sound events tab.  Highlight one of the sound files and hit play.  If you hear something, great, otherwise back up a step and try to get your sound system working.  Let us know and we'll point you towards the appropriate resources if needed.

---

### Post by Xaviar on 2006-02-27
Thanx for responding.  I took your advice ekarni and tested the sound.  It plays the files in the Sound Events Tab and it makes all the annoying bongo noises when I open and close applications so the sound is working, just not for my media players which doubtless is a proprietary codec problem.  

Thanks for the link aysiu.  The CD I used to install Ubuntu had been knocking around here for a while (I think it was from PC World magazine or something) so it will be outdated.  Bear with me here please, for me to update to Breezy, do I need to completely do away with Hoary and do all this setup stuff again or is there an auto-update function?  I mean is this more of an upgrade to Windows XP from Windows ME situation rather than say, a service pack update situation?  Do you guys change your Linux OS every six months?  If so, how does that go with other files (pictures, documents etc.) stored on the drive, it's a partitioning thing isn't it?

As for the hard drive filesystem I am not sure.  How do I determine the filesystem?

Thanks for the theme advice, I had tried that but I had limitted success (I didn't realize I should leave them zipped - dumb mistake since I'm actually quite used to switching themes in Mozilla's programmes).

I'll go to the link you've posted and see what I can do and get back to you.  Thanks for your help.

---

### Post by Xaviar on 2006-02-28
Have been to the link and after a few false starts (dur to my being very new to this) I have gotten the AVI sound up and running in Totem & Xine.  Thanks a lot for your help guys.  One problem down, six billion to go.  I've bookmarked that Wiki (it was a lot easier to understand than many other how-to sites) so I'll go back there and ferret around for more info so I can get used to this OS.  Cheers.

---

