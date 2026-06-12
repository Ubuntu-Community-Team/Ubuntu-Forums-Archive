---
title: "U3 Flash Drive- Block autoinstall?"
date: 2010-06-08
forum: General Help
---

### Post by rdbowers on 2010-06-08
I've run into a headache and haven't found a way of preventing this from happening again.  I put a flash drive in my system and there was an autoinstaller in it: "U3".  The autoinstaller locked me out from seeing it or making serious changes to the drive- I had to go to Root and use line commands to copy and paste some files.  Every since the flash drive was mounted, I've had some strange things happening with Linux (Ubuntu 10.4).  It seems a bit slower and I've had problems getting into some of my folders- having to try twice and so on.

I've already found the U3-Tools, but it doesn't say how to dig out something already installed.  I am pretty upset because I thought that Linux would be pretty much resistant to this sort of ****!!!

I have Fedora 12 on my laptop, and it won't allow flash drives to autoinstall software- we used it to scan and prevent viruses from infecting school computers during a symposium (I caught a LOT of bad malware and viruses on flash drives!).  

**Is there some way to "lock out" flash drives in general under Ubuntu, so they can't put stuff in that we don't want?**

If not, that would be a nice setting or small utility!!!

---

### Post by wilee-nilee on 2010-06-09
U3 can be removed here is a link.
[http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)
Use at your own risk and make sure that nothing is on the thumb that you may want to keep, just to be safe. This has to be run in a MS environment.

---

### Post by rdbowers on 2010-06-09
Yeah, Ubuntu has an app for that, but I'll check it out anyway.

What I'm looking for is a way to block ALL flash drives from autoinstalling stuff - unless I specifically want it (which I doubt will ever happen).  

In Windows, you have to disable it on each drive on a case-by-case basis, unless you purchase special software.  It makes for a gigantic security hole.  The "blocking" should be automatically a part of Linux- and like I mentioned, Fedora 12 seems to have it built-in.

Maybe it's a setting that I haven't properly set- I don't know.

---

### Post by wilee-nilee on 2010-06-09
When you say auto installing do you mean auto mount, I have seen instruction but I suspect the gconf-editor is the place to look.

Found it go to home edit preferences media and tick off, never prompt or start programs on media insertion. I think this is what you want.

The auto installing is the sandisk I think so even turning off the auto mount probably wont change anything I would get it off the thumb

---

### Post by dcstar on 2010-06-09
> **rdbowers said:**
> I've run into a headache and haven't found a way of preventing this from happening again.  I put a flash drive in my system and there was an autoinstaller in it: "U3".  The autoinstaller locked me out from seeing it or making serious changes to the drive- I had to go to Root and use line commands to copy and paste some files.  Every since the flash drive was mounted, I've had some strange things happening with Linux (Ubuntu 10.4).  It seems a bit slower and I've had problems getting into some of my folders- having to try twice and so on.
.........

U3 is a Windows application that cannot do anything to your Linux system.

It might do something silly to the Wine environment if you have that on your system, but don't blame it for anything on how your Ubuntu system performs.

If you don't want Ubuntu to autorun plugged in devices then change that setting in Nautilus-Preferences-Media.

---

### Post by rdbowers on 2010-06-09
Well, it did something.  Rebooting Ubuntu fixed the "strangeness", but something about whatever is on that drive keeps me from doing anything with the drive unless I'm operating as Root.

I don't like that.  I didn't have that problem with any other flash drive (I have and use four- disabled the autoinstall on the two with it).

I appreciate the tip on fixing the autoboot problem.  That was what I was looking for.

---

### Post by rdbowers on 2010-06-09
I found the settings- but there are times when I'd like a DVD or CD to autostart.  NEVER for a flash drive.  Is there some way to lock out the flash drives but not CD or DVD drives?

---

### Post by dcstar on 2010-06-10
> **rdbowers said:**
> I found the settings- but there are times when I'd like a DVD or CD to autostart.  NEVER for a flash drive.  Is there some way to lock out the flash drives but not CD or DVD drives?

You do not understand the way these things work. The options do **not** relate to the physical media type that contains them, they relate to what **content** is on the media.

The options apply to all content whether it is on something you put in the disk drive or a USB port - USB drives can contain CD audio or DVD video images that are exactly the same as an audio CD or a video DVD.

---

### Post by rdbowers on 2010-06-10
UHHH... I DO KNOW the difference.  Don't make unwarranted assumptions.

I never use a flash drive for music or videos or anything like that- I only use them to transfer files from one computer to another.

My problem is I don't want the autoinstaller build into the firmware of some drives to be activated.  I don't need to autostart software on a flash drive (ONLY on a flash drive).  THAT is what caused me a problem.  (It's also the primary way viruses are spread on my campus- our IT people trash the autoinstaller-equipped drives without opening or using them because they can bypass a lot of defenses.)

Autostarting software on a CD??? Sometimes I DO want that.  (However, I also rarely watch videos and don't listen to music on my computer.)

---

### Post by rdbowers on 2010-06-11
You said that the software only worked on Windows.  Well, it did something interesting.

It's set things up so every flash drive I have cannot be used (you cannot copy and paste to or from it) unless you're operating as root.

I didn't set that.  That is one of the symptoms that first appeared when the flash drive with the autoinstaller was first put in.

I've got a problem to dig out.

Caused by "Windows Only" autoinstaller.

---

