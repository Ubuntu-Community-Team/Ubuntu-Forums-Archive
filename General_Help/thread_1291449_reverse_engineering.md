---
title: "reverse engineering"
date: 2009-10-14
forum: General Help
---

### Post by theozzlives on 2009-10-14
How would I reverse engineer a program I wrote back in 1994 in VB 3.0? I found The RAMBar Shell (a Program Manager replacement) and long since lost the source and VB 3.0. I'd like to reverse engineer it and use the source, and Lazarus to create a Linux WM. Any help?

---

### Post by theozzlives on 2009-10-14
Included is a copy of RAMBar Shell! 3.0 in case someone has a copy of Windows 3.1. It's my program so there are no legalities to it.

---

### Post by coldReactive on 2009-10-14
HoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldon

You want to make a 16-bit (Win 1, 2 and 3 just sit on top of DOS) app run in VB 3?

---

### Post by theozzlives on 2009-10-14
> **coldReactive said:**
> HoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldonHoldon

You want to make a 16-bit (Win 1, 2 and 3 just sit on top of DOS) app run in VB 3?

I want to bring it back to source so I can see how I made it 15 years ago and turn the concept into a Linux WM. I also need info about the Linux API and integrating a WM into the system (you know, like a GNOME or KDE replacement). I downloaded it off the Internet so it must've been popular, back then it was Shareware. I will make it open source.

---

### Post by KlinerDraken on 2009-10-14
Found these at [http://www.woodmann.com/crackz/Tools.htm]("http://www.woodmann.com/crackz/Tools.htm")

[VB Decompiler Pro 3.4]("http://www.woodmann.com/crackz/Tools/Vbdec34.zip") - GPcH Soft's Decompiler (2.12Mb).
[Visual Basic v3.0 Decompiler]("http://www.woodmann.com/crackz/Tools/Vb3dec.zip") - from DoDi (1.28Mb).


good luck

---

### Post by theozzlives on 2009-10-16
Alas, after 15 years, I forgot how heavily The RAMBar Shell relies on the Windows API. I'd like to combine the concept of RAMBar with the functionality of GNOME.

Unfortunately, I doubt GNOME was written in Pascal. As I only know BASIC and Pascal I'm now in search of an easy way to find the source and have it translated to Pascal.

Any Help?

---

### Post by P4man on 2009-10-16
No decompiler is going to get you very useful source code back. Might be okay to examine a particular part of code, but its never going to be the basis of a new program. Especially not as in this case you'd end up with (mostly unreadable) VB 3 code you'd like to port to linux.

If the idea was good, keep the idea, ditch the code, start from scratch. But you'll need to learn a more modern language first anyway, something like Python. Writing a desktop manager sounds pretty ambitious for a first project though...

Perhaps it would be better if you wrote a blueprint or something on launchpad where you describe in details your idea and concept and hope some dev's pick it up. In the meanwhile, spend your time learning to make "hello world" in python. (FWIW, Im almost there :p)

---

### Post by theozzlives on 2009-10-16
> **P4man said:**
> No decompiler is going to get you very useful source code back. Might be okay to examine a particular part of code, but its never going to be the basis of a new program. Especially not as in this case you'd end up with (mostly unreadable) VB 3 code you'd like to port to linux.

If the idea was good, keep the idea, ditch the code, start from scratch. But you'll need to learn a more modern language first anyway, something like Python. Writing a desktop manager sounds pretty ambitious for a first project though...

Perhaps it would be better if you wrote a blueprint or something on launchpad where you describe in details your idea and concept and hope some dev's pick it up. In the meanwhile, spend your time learning to make "hello world" in python. (FWIW, Im almost there :p)

I'm to into my business to learn a new language, programming is a hobby not a profession. Besides, Pascal is a powerful language... tried and true. I just don't think it gets the credit it deserves. Everyone is into C, java, or perl.

---

### Post by undecim on 2009-10-16
To reverse engineer something, you need to have a deep understanding of the assembly for the architecture that the program was compiled for. Usually reverse engineering is meant to get source code; It's just done to figure out what a program is trying to do. Its what security specialists do to viruses, and what pirates do to DRM'd software.

Reverse engineering isn't going to get your code back. Going from source, to machine code to source is like going from Engligh to japanese to english again.

Kind of like... [http://translationparty.com/#4813074](http://translationparty.com/#4813074)

And even if you could get back your code verbatim, you wouldn't even have your comments - you'd be stuck trying to figure out what you meant a long time ago.

If you like it that much, its easier to just build a clone of it.

BTW, if you still have W3.1, it runs in DOSBox. There are also plenty of abandonware sites you can get it from (though its legality is questionable)

---

### Post by theozzlives on 2009-10-17
I'm running DOS 6.22 in a Virtual Box. I thought I stated that I'll need to start from scratch. A WM is a lot more involved than a Program Manager replacement. I just need to know the Linux and X API because most software now days don't speak to hardware, but to the OS.

---

