---
title: "Help with httrack"
date: 2012-05-01
forum: General Help
---

### Post by sTpny on 2012-05-01
The Website 'www.creditorsincommerce.com' has absolutely awesome information, mainly in the form of mp3 audio files.  I've been trying (and trying, and trying) to use webhttrack to download all of these mp3s to my computer (so I can transfer them to my mp3 player) but I just can't seem to get it to work, no matter what I try.  I know that this can be done, but I'm not having any luck with it. Can someone please help me? 

For simplicity, as the command line often is easier for such things, can I get the help in the form of the command to download all mp3's from creditorsincommerce.com using httrack, (or any command that will accomplish the task)

also.. I would suggest to everyone to run this command when (and if) anyone/someone provides the solution. The information provided in the mp3's is mostly about how to enforce your rights and protect your freedoms.. which I think is something we can all agree is important. 

Thanks tonnes in advance. :)

---

### Post by jerrrys on 2012-05-01
maybe

[http://ubuntuforums.org/showthread.php?t=1476005](http://ubuntuforums.org/showthread.php?t=1476005)

---

### Post by sTpny on 2012-05-01
> **jerrrys said:**
> maybe

[http://ubuntuforums.org/showthread.php?t=1476005](http://ubuntuforums.org/showthread.php?t=1476005)


Not perfect, but that will do.. it would have taken hours!!  

here are the commands I used.. please feel free to post any other solutions:
(there are also zips with the associated docs.. I suppose -A zip would get them, but I don't need them so not trying.. ) 

wget -r -A mp3 [http://www.cic-root.com/living-temple/](http://www.cic-root.com/living-temple/)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/201007-boston/](http://www.cic-root.com/audio/workshops/201007-boston/)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/201005-atlanta/](http://www.cic-root.com/audio/workshops/201005-atlanta/)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/200910-losangeles/](http://www.cic-root.com/audio/workshops/200910-losangeles/)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/200908-chicago/](http://www.cic-root.com/audio/workshops/200908-chicago/)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/200909-bellingham/](http://www.cic-root.com/audio/workshops/200909-bellingham/)
wget [http://recordings.talkshoe.com/TC-37960/TS-253362.mp3](http://recordings.talkshoe.com/TC-37960/TS-253362.mp3)
wget -r -A mp3 [http://www.cic-root.com/audio/workshops/200908-rancho-cucamonga/](http://www.cic-root.com/audio/workshops/200908-rancho-cucamonga/)
wget -r -A mp3 [http://www.cic-root.com/audio/hall/](http://www.cic-root.com/audio/hall/)
wget -r -A mp3 [http://www.cic-root.com/audio/coaching/](http://www.cic-root.com/audio/coaching/)
wget -r -A mp3 [http://www.cic-root.com/audio/misc/](http://www.cic-root.com/audio/misc/)
wget -r -A mp3 [http://www.cic-root.com/audio/hg/](http://www.cic-root.com/audio/hg/)

I hope this helps everyone/anyone.. it's certainly helped me! 

.. I'm freer than I've ever been. :)


EDIT - Some wget requests came back as ERROR 403: Forbidden  -- any clues? 

Heres a sample error.. 

tony@Rebel:~/Downloads/cinc$ wget -r -A mp3 [http://www.cic-root.com/audio/workshops/200908-chicago/](http://www.cic-root.com/audio/workshops/200908-chicago/)
--2012-05-01 18:58:44--  [http://www.cic-root.com/audio/workshops/200908-chicago/](http://www.cic-root.com/audio/workshops/200908-chicago/)
Resolving [www.cic-root.com]("http://www.cic-root.com")... 67.20.76.38
Connecting to [www.cic-root.com|67.20.76.38|:80]("http://www.cic-root.com%7C67.20.76.38%7C:80")... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-05-01 18:58:44 ERROR 403: Forbidden.

---

