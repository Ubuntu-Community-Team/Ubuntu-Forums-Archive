---
title: "Help with Abcde please!"
date: 2010-08-09
forum: General Help
---

### Post by caffeinated blood on 2010-08-09
I've installed abcde, lame, flac and id3v2 in order to re-rip some cd's to flac and mp3 music files. I copied the /etc/abcde.conf file to my Home folder - .abcde.conf file.I've tried many different ways to configure this file, but when I save any configuration, no matter how basic, I cannot stop the default settings from running.It keeps outputting to my Home folder(not exactly where I want my music) and it does this in oggvorbis encoding.What am I doing wrong?Is anyone having trouble using abcde on Lucid Lynx?

---

### Post by andrew.46 on 2010-08-10
Hi caffeine,

Perhaps have a look at this guide:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

Make sure you have the configuration file in the correct place, it should be $HOME/.abcde.conf or abcde will ignore it and use the defaults as you describe.

Andrew

---

### Post by caffeinated blood on 2010-08-10
I've tried that as well as many other configurations.I can't change one single default setting because the system keeps going to the /etc/abcde.conf file and not the $HOME/.abcde.conf file.This is the problem.I'll save the newly configured .abcde.conf file and the system just skips over it.

---

### Post by AlphaLexman on 2010-08-10
You can 'force' a different .conf file with the -c option...
```
abcde -c /home/username/.abcde.conf
```

---

### Post by caffeinated blood on 2010-08-10
Would you believe I have tried that too?I enter the command and get an error message - CDROM has not been defined or cannot be found... something like that.I also have to manually tell abcde where -d is.I have no problems with my cdrom drive on the system or with any other application so I don't know why this is happening with abcde.

---

### Post by andrew.46 on 2010-08-11
Hi caffeinated,

> **caffeinated blood said:**
> I can't change one single default setting because the system keeps going to the /etc/abcde.conf file and not the $HOME/.abcde.conf file.This is the problem.I'll save the newly configured .abcde.conf file and the system just skips over it.

Could you run the following:

```
find $HOME -name '.abcde.conf'
```

and this should show definitively if your configuration file is the correct place. On my own system:

```

andrew@skamandros~$ find $HOME -name '.abcde.conf'
/home/andrew/.abcde.conf

```

Andrew

---

### Post by AlphaLexman on 2010-08-11
Do you have more than one CD drive?

Maybe /dev/cdrom/ is pointing to the 'other' disc drive. Try putting the disc in the second drive...

---

### Post by caffeinated blood on 2010-08-11
Thank you both for keeping up with this thread.This is driving me nuts.I ran the command you asked, andrew.46 and the results are as you said they should be - the file shows with the command. And no, AlphaLexman, I only have one drive. It's an SATA DVDRW drive. I don't know if that makes a difference. My motherboard supports IDE, but no drives of that type are on it. As I mentioned in previous reply, this drive works fine with the system and other apps.I even tried changing the "d" to "g" in the configuration file for SCSI emulation layer(in the same paragraph for naming the CDROM device) - still did nothing to effect the .abcde.conf file.Any other ideas?

---

### Post by andrew.46 on 2010-08-11
Hi caffeinated,

> **caffeinated blood said:**
> I ran the command you asked, andrew.46 and the results are as you said they should be - the file shows with the command. 

Can you post the contents of your ~/.abcde.conf file here?

Andrew

---

### Post by AlphaLexman on 2010-08-11
Have you tried:
```
abcde -d /dev/scd0
```
You may need to change 'scd0' to your device descriptor for your cd drive.

---

### Post by cavalier911 on 2010-08-11
What about permissions and owner:group of ~/.abcde.conf

---

### Post by caffeinated blood on 2010-08-12
These are the basic changes I made to the .abcde.conf file. #MP3ENCODERSYNTAX=lame    #CDROM=/dev/sr0   #LAME=/usr/bin/lame #OUTPUTDIR=$HOME/Music #WAVOUTPUTDIR=$HOME/Music #OUTPUTTYPE="mp3"    all other settings in the file are unchanged. I experimented with some lameopts that I copied from configurations I found online, but nothing worked that way either so just the one listed are currently the only ones changed from default. As for the permissions, owner:group settings I have changed those too and you guessed right..... didn't work either. So those settings have been set back to the original which are Owner=R+W,Group and Others R only.Hope this helps you guys to help me.

---

### Post by mc4man on 2010-08-12
> These are the basic changes I made to the .abcde.conf file. #MP3ENCODERSYNTAX=lame #CDROM=/dev/sr0 #LAME=/usr/bin/lame #OUTPUTDIR=$HOME/Music #WAVOUTPUTDIR=$HOME/Music #OUTPUTTYPE="mp3" all other settings in the file are unchanged

Just out of curiosity - you have uncommented the lines you want used in your .abcde.conf?

Maybe ck. this sample for mp3
[http://www.andrews-corner.org/abcde.html#mp3](http://www.andrews-corner.org/abcde.html#mp3)

---

### Post by caffeinated blood on 2010-08-12
Boom!Got it working.Thank you mc4man!!!!!!!!It was exactly as you suggested.Uncommented the lines and all is fine.Thanks to everyone.Sorry,I misunderstood what "uncomment" means(LOL)A simple mind once again screws up a simple procedure.Obviously still a newbie,but loving every minute of it - even with all the frustrations that I create for myself.

---

### Post by hokage13 on 2011-01-02
I am having some trouble with abcde and came across this post.

I specified in my conf file to output files as mp3 and to a specific location, however, resulting files is wav and output in a dir under home directory.

output of find $HOME -name '.abcde.conf'
```
/home/xbmc/.abcde.conf
```

Attach is also my config file

I invoke abcde with the following command:
```
abcde -d /dev/cdrom1  -c /home/xbmc/.abcde.conf -N
```

Not sure what is wrong...

---

### Post by mc4man on 2011-01-02
Your abcde.conf is specifying to save the .mp3's in ~/Music/mp3/aristname/albumname/

Are you sure the mp3's aren't there?

---

### Post by hokage13 on 2011-01-02
Thanks for pointing that out.

I was looking for ~/Music/aristname/ and not ~/Music/mp3/aristname/ and then I assumed that it is not working

silly me...

---

