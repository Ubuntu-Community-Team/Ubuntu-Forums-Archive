---
title: "Mencoder Can't Find MP3 Codec"
date: 2006-04-15
forum: General Help
---

### Post by maxol on 2006-04-15
Hi,

I use mencoder to encode video for my Cowen IAUDIO X5. I use the command:> mencoder inputfile.avi -o outputfile.avi -ovc lavc -oac lavc -lavcopts acodec=mp3:abitrate=96 -ofps 13 -vf scale=160:108

I have a desktop and a laptop which both use Ubuntu Breezy, this works fine on my desktop machine but running the same command on my laptop gives me the error:> Audio LAVC, couldn't find encoder for codec mp3


I have mp3lame installed and have tried reinstalling mplayer and the multimedia codecs but still get the same error.

Anyone have an idea why this is happening?

---

### Post by Perfect Storm on 2006-04-15
Silly question is the w32codecs installed?

---

### Post by maxol on 2006-04-15
Yes, checked and they're definately there.

---

### Post by croak77 on 2006-04-15
Is lame installed?

---

### Post by maxol on 2006-04-15
Yes lame is installed.

---

### Post by Sokertes on 2008-02-20
I know this is an old thread but in case you or somebody else is having this problem here is a solution

change

mencoder inputfile.avi -o outputfile.avi -ovc lavc -oac lavc -lavcopts acodec=[COLOR="Red"]mp3[/COLOR]:abitrate=96 -ofps 13 -vf scale=160:108

to 

mencoder inputfile.avi -o outputfile.avi -ovc lavc -oac lavc -lavcopts acodec=[COLOR="Red"]libmp3lame[/COLOR]:abitrate=96 -ofps 13 -vf scale=160:108

and that should take care of it for you.

---

### Post by sefs on 2008-03-12
Hi i am having this problem with acid rip.

When I select lavc in the audio encoding settings...I get this.  How can we make lavc find the mp3 encoder or whats not

---

### Post by sefs on 2008-03-12
Ok i was able to solve my problem by switching the audio selection in acidrip to mp3lame...although i am 100 percent positive i was able to use lavc before.

---

### Post by coyotepod on 2008-07-18
Redundant I know...I too was using Acid Rip and also changed the audio options to libmp3lame with success.

---

