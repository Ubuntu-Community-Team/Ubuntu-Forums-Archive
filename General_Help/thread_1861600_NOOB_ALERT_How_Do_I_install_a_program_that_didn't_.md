---
title: "NOOB ALERT: How Do I install a program that didn't come from the software centre?"
date: 2011-10-15
forum: General Help
---

### Post by razorneck on 2011-10-15
Yes, hello everyone. I'll just start by apologizing, OK? lol

I come from the Windows world, but would like to start using Linux. I think.

- Using the new Ubuntu 11.10

- Need to install screenplay writing software called 'Celtx'.

- Downloaded file gave me: an archived file which spit out a folder.

- So... uh... what now? I don't see any 'executable' files in the folder - of course, I actually have no idea if Ubuntu even uses 'executable' files. I see a celtx-bin... is that what I'm looking for?

muh. I'm so lost. Sorry for starting out as a pain to this community, but if someone could take pity on poor little old me, that would be sweet. Heard lots of good things about Ubuntu. Duel booting with Vista right now.

...please don't make me go back to Vista. I'm begging you.

matt

---

### Post by haqking on 2011-10-15
> **razorneck said:**
> Yes, hello everyone. I'll just start by apologizing, OK? lol

I come from the Windows world, but would like to start using Linux. I think.

- Using the new Ubuntu 11.10

- Need to install screenplay writing software called 'Celtx'.

- Downloaded file gave me: an archived file which spit out a folder.

- So... uh... what now? I don't see any 'executable' files in the folder - of course, I actually have no idea if Ubuntu even uses 'executable' files. I see a celtx-bin... is that what I'm looking for?

muh. I'm so lost. Sorry for starting out as a pain to this community, but if someone could take pity on poor little old me, that would be sweet. Heard lots of good things about Ubuntu. Duel booting with Vista right now.

...please don't make me go back to Vista. I'm begging you.

matt

First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)

**For your particular application instructions are here [http://wiki.celtx.com/index.php?title=Installation](http://wiki.celtx.com/index.php?title=Installation)** scroll down for Linux installation

Have fun

Regards

haqking

---

### Post by razorneck on 2011-10-15
hey thanks for the crazy detailed explanation, haqKing!

I couldn't get it to work, but not for lack of effort on your part.

I'm afraid the linux install instructions on the celtx site don't take 11.10 into consideration. I gave linux a shot a long time ago and actually got this to work just by creating a custom launcher - but after reading a couple of other threads it looks like the custom launcher option is gone now?

Bleh. I don't have time to screw with this. Back to Vista I guess :(

---

### Post by digc16 on 2011-10-17
Just click the celtx file inside the celtx folder twice. It will ask if you want to run, run in terminal, and some other options...just choose run. If it doesn't launch, then run this line. It may be a bit of an overkill, but it consistently has worked for me, so I'm sharing the result.  When your desperate and it works you become gracious.

sudo apt-get install ia32-libs libstdc++6 libstdc++5 freeglut3

To create a new launcher you will have to edit that in unity, after you get it celtx work.  There is an entry from kerry_s that is pretty good. This shouldn't be too hard. Good luck.

[http://ubuntuforums.org/showthread.php?t=1578379](http://ubuntuforums.org/showthread.php?t=1578379)

---

