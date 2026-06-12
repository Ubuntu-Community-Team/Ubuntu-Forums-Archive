---
title: "[B]Mozila Thunderbird issue[/B]"
date: 2010-10-17
forum: General Help
---

### Post by iokara08 on 2010-10-17
Good afternoon to everybody,

I have a small sound issue using Mozilla Thunderbird.
I have set up Thunderbird to inform me, using a sound alert, when a new mail arrives. 
The problem is that Thunderbird does not producing any sound. I have tried to use many different sound files but no result. 
In the preferences of Thunderbird after I am choosing a sound file I press play (in order to perform preview) but no sound is produced.
If anybody has the same issue it would be really helpful to inform me how he solved it:) 

Thank you in advance.

---

### Post by TeoBigusGeekus on 2010-10-17
The wav file has to have the microsoft codec (i.e. microsoft pcm).
Open your wav with audacity and convert it. Also, keep it 16bit and mono to be on the safe side.

---

### Post by iokara08 on 2010-10-18
Good evening TeoBigusGeekus and North Greece,

Thank you for your reply,

I made to follow your instructions. I imported a .wav file in Audacity and then I exported it as:
**WAV(Microsoft) signed 16bit PCM**
Unfortunately it did not work.

I have to confess that I used Audacity for first time and thus maybe I did not succeed to use it properly.
Apart of this, I believe that the problem is associated with a malfunction of the corresponding Thunderbird version since I never had this problem. 
I was always able to use the .wav sound files that Ubuntu offers:?:.
Thank you for your help and I will try to search more about this issue:rolleyes::-k

---

### Post by jcoles on 2010-10-20
I think this is a Thunderbird issue. I installed version 3.1 downloaded from the Thunderbird site because version 3.0 in the distribution was unusably slow. But, like you, I can find no sound that Thunderbird will play. Selecting the Default system mail sound option also doesn't work.

---

### Post by Onliner560 on 2010-10-20
Had the same problem with TBird not playing .wav file on email arrival.

1. Install Medibuntu: https.help.Ubuntu.com/community/Medibuntu

2. Make sure key-ring is install [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

3. Install with terminal: sudo apt-get install ubuntu-restricted-extras

4. Then, install the following files:

   libaudiofile0
   libesd0
   esound-common
   esound-clients

.Wav file should sound in TBird with email arrival.

Cheers!

---

### Post by iokara08 on 2010-10-21
Good evening,

Tonight, after I did an update (update manager) in my Ubuntu 10.10, Thunderbird sound is now operating.
Regarding to the post of "Onliner560" I have to say that in my system the files that he proposed for installation are installed. I don't really know if they were installed during the update of before it.....
All of you that you have the same problem try to install the proposed files or simply run the update manager.

good evening;)

---

### Post by iokara08 on 2010-10-26
Hi again,

As I had posted the sound in Thunderbird was working after running the update manager.
Yesterday I experienced again some sound issues in Thunderbird and thus I followed the instructions of "Onliner560". I realized that the sound files that Onliner560 proposes was not anymore installed!

I installed them using the synaptic package manager and now everything is working perfectly.

Thank you once more Onliner560.

---

