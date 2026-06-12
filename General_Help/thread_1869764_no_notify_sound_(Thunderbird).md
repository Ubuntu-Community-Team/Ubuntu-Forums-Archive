---
title: "no notify sound (Thunderbird)"
date: 2011-10-26
forum: General Help
---

### Post by mike555 on 2011-10-26
I don't seem to be able to get any new mail notify sound in Thunderbird , any tricks to get it working   (I have Xubuntu 11.10)

---

### Post by decrepit on 2011-10-26
I had this problem with 10.4.
From memory the default location had no sounds in it.
I pinched a mail alert sound from my fedora installation and put it in.
/usr/share/sounds

Then selected "use the following sound file" and "browsed" to it.

---

### Post by mike555 on 2011-10-26
I tried pointing Thunderbird to a .wav file and it just did not play , nor did the default sound.  
 I have version 7.01 of Thunderbird.

---

### Post by decrepit on 2011-10-26
Have you got the "play" button in the preferences window?

If that doesn't play, you need better help than I can give you.

---

### Post by mike555 on 2011-10-26
Yes I tried the play button as well as sending myself email to see if the sound worked , but no sound.
   and I tried the xfce forum , no reply yet.

---

### Post by mike555 on 2011-10-26
Ok, I got it...... I had to Install the following files:

          Libaudiofile0
    Libesd0
   esound-common 

now it works fine...

---

### Post by ThomasNovin on 2011-12-08
> **mike555 said:**
> Ok, I got it...... I had to Install the following files:

          Libaudiofile0
    Libesd0
   esound-common 

now it works fine...

Worked for me too, although the filenames should be:

libaudiofile0 libesd0 esound-common

---

### Post by risyho on 2011-12-30
I had the same problem. Solved now. Thanks a lot! :D

---

### Post by Kryzzalid on 2012-01-06
Worked for me too! thanks:)

---

### Post by slickvguy on 2012-02-20
Fresh install fo Xubuntu 11.10. No sound in Thunderbird on e-mail arrival nor Lightning extension (event reminder). Nada.

After much googling, I simply installed libesd0 package (and its dependencies), and the dinky sound.wav can now be heard in Thunderbird and Lightning. Confirmed fix.

Wish I had seen this thread about an hour earlier. ;)

---

