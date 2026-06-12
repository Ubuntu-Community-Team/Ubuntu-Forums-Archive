---
title: "Virus issues"
date: 2010-04-16
forum: General Help
---

### Post by allen01 on 2010-04-16
_Into_.
I have a message come up indicating I had 10 viruses, 5 in in home and 5 on the hard drive. I was under the impression that viruses did not attack Ubuntu, however, looking at the forums I read that they do affect Ubuntu.  To date I have seen no affect or changes to my PC.
I ran clamTK virus scan and found 1 in firefox, this I eventually removed by moving it into another directory and deleting it.  ClamTK would not allow me to quarantine it.  After some research I downloaded and ran klamAV and found 18 viruses.  However I cannot quarantine them.  The program does not respond.  I do not want to delete until I know more.  I am aware that some files do register as a virus.   All 18 are in usr/lib/erlang//// areas and are shown as encrypted zip files.  

_Questions_.

1   Are they viruses
2   Why can I not quarantine them
3   What actions are recommended
4   What does usr directory contain

---

### Post by Chronon on 2010-04-16
ClamAV (for which KlamAV is a front-end) does tend to produce a lot of false positives).  Judging by the location, KlamAV probably doesn't have the necessary permissions to delete or move the files.

I am not aware of any active viruses for GNU/Linux systems at the moment.  By the reading I have done, the primary function of antivirus software on Ubuntu is to cleanse infectious files so they can't infect Windows systems that you interact with.  

You don't mention the exact message you are getting but I believe that "Broken Executable" is a common false positive as it would find these in every scan on my system.  In my case, I know they weren't malware because they were leftovers of a build process run on benign code.

---

### Post by marshmallow1304 on 2010-04-16
1) They are probably false positives.
2) You (running the virus scanner) probably don't have permissions to edit the files.
3) Probably nothing, but it's always a good idea to back up your data just in case.
4) Mainly user applications.  See [this]("http://www.tuxfiles.org/linuxhelp/linuxdir.html").

[This page]("https://help.ubuntu.com/community/Linuxvirus") has more info about viruses.

---

### Post by mike555 on 2010-04-16
make sure you have the latest engine ,(.96) you will probably need to add the ppa to get it .........

---

### Post by 2hot6ft2 on 2010-04-16
Along with what has already been said I suppose you use WINE. It does run windows stuff and that would include windows viruses. Are they perhaps in ~./wine which is in the home folder?

And 5 in home and 5 that are on the hard drive? Is home not on the hard drive?
I would guess 5 that were installed in wine, and 5 that are in the program that you installed them from.

---

### Post by allen01 on 2010-04-24
Many thanks for the relies to date.  Having done a little research I find that erlang is a programming language.
Questions

1.  Is this the case and why would it be in the usr directory as an encrypted zip file?
2.  All the false positives are encrypted zip files, what do these do?
3.  I have no widows files, I think, definitely cannot find WIN files
4.  Am i looking for a ghost and should I give in?  The learning curve is starting to get very steep for a novice

---

### Post by gradinaruvasile on 2010-04-24
Just relax. There are no known viruses for Linux other than a few lab experiments (which used some vulnerabilities that were plugged AFAIK).
If ClamAv reports viruses, those are Windows viruses - if they are not false positives.
And being in encrypted .zip files... How on earth did the AV open them to scan inside?

---

### Post by dcstar on 2010-04-25
> **allen01 said:**
> _Into_.
.......
I am aware that some files do register as a virus.   All 18 are in usr/lib/erlang//// areas and are shown as encrypted zip files.  

I just scanned my entire usr/lib/erlang tree with Clamatk and no viruses whatsoever were identified.

---

### Post by asmoore82 on 2010-04-25
> **allen01 said:**
> _Into_.
I have a message come up indicating I had 10 viruses, 5 in in home and 5 on the hard drive.
...

If *_you_* did not install and run a virus scanner yourself
then this message is not legitimate.

It sounds like you just saw a pop up ad on the web telling you your
computer was infected.

There are absolutely no active Linux viruses in the wild.

---

### Post by 3rdalbum on 2010-04-25
> **allen01 said:**
> 
4.  Am i looking for a ghost and should I give in?  The learning curve is starting to get very steep for a novice

Well yeah, you're looking for something that doesn't exist; there are no Linux viruses that can actually get onto your system.

---

### Post by john newbuntu on 2010-04-25
Go to [http://www.virustotal.com](http://www.virustotal.com) and upload the files.  The site analyzes the files by running it through various scanners and report results.

Edit: Just as how dcstar did, I too put /usr/lib/erlang through clamscan version 0.95.3 and found nothing.

---

### Post by Zintha on 2010-04-25
> **asmoore82 said:**
> If *_you_* did not install and run a virus scanner yourself
then this message is not legitimate.

It sounds like you just saw a pop up ad on the web telling you your
computer was infected.

There are absolutely no active Linux viruses in the wild.
Unless you count users, in which case i'm pretty active.

Also beginning to think this too, if it happened to pop up while you were surfing the web and you didn't even ask for a virus scan from your computer the chances are you're being caught out by one of those silly things that is designed to look like windows prompts but is actually just resizing Firefox to get you to install their software. Which I hear is sometimes harmful.

However, chances are, even if you clicked on it from Ubuntu, it did nothing.
But if you have a windows partition, or duel boot etc etc you can run a scanner and clean out whats there.

---

### Post by dcstar on 2010-04-25
> **allen01 said:**
> _Into_.
I have a message come up indicating I had 10 viruses, 5 in in home and 5 on the hard drive. I was under the impression that viruses did not attack Ubuntu, however, **looking at the forums I read that they do affect Ubuntu**. ........

I cannot recall **one** post in over 5 years on this forum highlighting that any virus ever affected a Ubuntu system.

---

### Post by louieb on 2010-04-25
Seems like I recall 1 a few months back. Someone added a theme to gnome-look.org. turned out to be a Trojan.  Did not take long to figure it out. 

I've used Linux since 2006 - that is the only the only one I have read about. 

One thing about a virus - in order to be successful - it rate of spread must exceed its death rate.

---

