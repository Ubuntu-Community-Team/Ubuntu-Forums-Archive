---
title: "mplayer? what? where?"
date: 2006-05-22
forum: General Help
---

### Post by zuus on 2006-05-22
Okay, maybe I'm a complete idiot/newb but I can't seem to find mplayer for Ubuntu Breezy x86 ANYWHERE. Basically I want it to stream music in the background while screened, but every search I do on it is either a dead end or a speel on how wonderful it is, yet here's what I get;

zuus@ikarus:~$ mplayer
bash: mplayer: command not found
zuus@ikarus:~$ sudo apt-cache search mplayer
mga-vid-source - Kernel driver for the back-end scaler on Matrox cards (source)
mozilla-mplayer - MPlayer-Plugin for Mozilla

The only package I have found for breezy was an x86-64, but searches for 386 versions have come up blank and there doesn't seem to be info on them being taken off the shelves.

And yup, I've unlocked all the repositories for apt and did an apt-get update.
I'm stumped :(

---

### Post by aysiu on 2006-05-22
MPlayer is in the Multiverse, not the Universe. So you can't get it from just unlocking repositories that have been uncommented. You actually need to *add* repositories. > Package mplayer

    * breezy (graphics): The Ultimate Movie Player For Linux [multiverse]
      1:1.0-pre7cvs20050716-0.1ubuntu9.1: amd64
      1:1.0-pre7cvs20050716-0.1ubuntu9: amd64
    * dapper (graphics): The Ultimate Movie Player For Linux [multiverse]
      2:0.99+1.0pre7try2+cvs20060117-0ubuntu8: amd64 i386 powerpc

Package mplayer-386

    * hoary (graphics): The Ultimate Movie Player For Linux [multiverse]
      1:1.0-pre6-0.3ubuntu6.2: i386
      1:1.0-pre6-0.3ubuntu6: i386
    * breezy (graphics): The Ultimate Movie Player For Linux [multiverse]
      1:1.0-pre7cvs20050716-0.1ubuntu9.1: i386
      1:1.0-pre7cvs20050716-0.1ubuntu9: i386
    * dapper (graphics): The Ultimate Movie Player For Linux (dummy package) [multiverse]
      2:0.99+1.0pre7try2+cvs20060117-0ubuntu8: all [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) should help.

By the way, why are you posting in the Warty section if you're using Breezy?

---

### Post by zuus on 2006-05-22
Ahh excellent. I added the sources there and that fixed it up. I knew it was in multiverse, and I actually had a .AU multiverse source in there (that's where I got confused), but obviously it didn't have mplayer. 

Sorry about posting under Warty - didn't read the headings properly.

Thanks for the help! :)

---

