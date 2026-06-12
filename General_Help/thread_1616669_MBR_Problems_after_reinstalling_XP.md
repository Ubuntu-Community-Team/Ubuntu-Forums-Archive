---
title: "MBR Problems after reinstalling XP"
date: 2010-11-08
forum: General Help
---

### Post by mihamil on 2010-11-08
I KNOW, it's taboo to ask this here but I need help.  

Before I start I want to say that I have not abandoned ubuntu.  Ubuntu was on my wife's laptop and she has been trying to get used to it for a year and is still struggling.  She asked me to "PLEASE put Windows back on her computer".  So I tried to wipe everything (10.04) and install XP Pro.  I actually am a network admin and pretty good with computers so I thought this shouldn't be a problem. Just insert the WIN disk, boot up, delete all partitions, format using NTFS, and install Windows XP Pro.  Did that.

Then I got a message saying this when it booted up.

Error: unkown filesystem
Grub rescue>

Figures.  So I put the Windows Installation disk back in and go to Recovery console.  I have ran fixmbr and fixboot.  Same thing.

I even reran the windows installation, started all over again and made absolutely sure I deleted all of the partitions (thought I might have missed one and screwed things up).  Same thing.  

The only way I can get my installation of windows to come up is by putting the Windows CD in the drive, booting to the CD drive, and not pressing anything when it says

Press Any key to boot to the CD...

When I don't press anything it abandons the installation and sends you to the primary partition on the hard drive and it boots.

Any ideas?  PLEASE HELP ME...


GOT IT.  It was acting jacked up because my flash drive was in.  I have had my flash drive set up as a bootable live os once I guess I never removed the boot partition from it.  In addition I feel ashamed that I allowed myself to fall victim of that stupid of a problem.

---

