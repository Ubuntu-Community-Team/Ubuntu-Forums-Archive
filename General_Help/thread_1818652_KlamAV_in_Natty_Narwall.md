---
title: "KlamAV in Natty Narwall?"
date: 2011-08-05
forum: General Help
---

### Post by kyral210 on 2011-08-05
I have been using KlamAV as a good GUI to Clam Antivirus for a while and I like how it is simple and I can do automatic scans every day. I upgraded to 11.04 and it is no longer in the software centre.
 
Is there any way I can install Klam? I have tried the website but their instructions are way too complicated for my beginner knowledge.

---

### Post by Matt__ on 2011-08-05
klamav is kde...why not use clamav.

in a terminal one at a time
```
[B][FONT=Arial]sudo apt-get repository ppa:ubuntu-clamav/ppa
sudo apt-get update
sudo apt-get install clamav[/FONT][/B]
```

---

### Post by haqking on 2011-08-05
> **kyral210 said:**
> I have been using KlamAV as a good GUI to Clam Antivirus for a while and I like how it is simple and I can do automatic scans every day. I upgraded to 11.04 and it is no longer in the software centre.
 
Is there any way I can install Klam? I have tried the website but their instructions are way too complicated for my beginner knowledge.


Unless you share files with windows users then dont worry about the AV software, it is not needed if you are solely a linux user with no windows files being shared

---

### Post by Matt__ on 2011-08-05
+1 haqking
but is it possible NOT to have to share with win users? theyre everywhere! :)

---

### Post by haqking on 2011-08-05
> **Matt__ said:**
> +1 haqking
but is it possible NOT to have to share with win users? theyre everywhere! :)

I hang garlic on my router to keep them away ;-)

---

### Post by kyral210 on 2011-08-05
I am using the Ubuntu machine to convert files for a large international research project. The files are coming from Windows and will ultimately go to windows. I am 99.99999999999999999999% certain I won't get a virus, but as information is passing through our systems it is good to say that we have screened it for viruses. 
 
As for ClamAV, I really don't care what antivirus software I use as long as:
[LIST=1]
[*]it can detect viruses at a reasonably good rate
[*]Can be setup easily to scan the whole hard drive once a day
[/LIST]If I installed ClamAV as listen above, how would I get it to do the autoscan? Besides, I thought KlamAV was just a useful GUI front to the ClamAV software?
 
Hang garlic around server? Well, I am one of the few people at Loughborough Uni who will touch Linux, which is why I got the job i am doing now. IT here dont like it and stick to Windows Server & Windows desktop almost exclusively (although there are a few sneeky macs kicking around).

---

### Post by haqking on 2011-08-05
> **kyral210 said:**
> I am using the Ubuntu machine to convert files for a large international research project. The files are coming from Windows and will ultimately go to windows. I am 99.99999999999999999999% certain I won't get a virus, but as information is passing through our systems it is good to say that we have screened it for viruses. 
 
As for ClamAV, I really don't care what antivirus software I use as long as:
[LIST=1]
[*]it can detect viruses at a reasonably good rate
[*]Can be setup easily to scan the whole hard drive once a day
[/LIST]
If I installed ClamAV as listen above, how would I get it to do the autoscan? Besides, I thought KlamAV was just a useful GUI front to the ClamAV software?
 
Hang garlic around server? Well, I am one of the few people at Loughborough Uni who will touch Linux, which is why I got the job i am doing now. IT here dont like it and stick to Windows Server & Windows desktop almost exclusively (although there are a few sneeky macs kicking around).

I meant hang garlic to keep away windows users and the viruses ;-)

and AV software is fine for linux, there are no active viruses in the wild for Linux, clam AV is popular so if it works for you then fine.

KlamAV and ClamAv are the same thing (the K in klam refers to use under the KDE environment

see here for more info on viruses  in and around linux

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Frogs Hair on 2011-08-05
I used Clam when I started with Ubuntu and I found it difficult to update . I would look into Avast also . I only scan windows now , I never send any attachments or photos of unknown origin anyway . [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

---

### Post by Matt__ on 2011-08-05
Now look in the software centre for clamtk gui for clamav.
to update clamav open a terminal and ```
sudo freshclam
```

---

### Post by kyral210 on 2011-08-08
Thanks. I have installed ClamTk and set up daily scan. However, when the time comes for the scan I see no icons coming up or anything to tell me the scan has started. I checked my system monitor and found it runs in the background with no visual display. Not really ideal as I like to see things in my GUI, but as I dont expect any virus on my system anyway I am happy enough with this.

---

