---
title: "Synchronizing mobile Nokia E51 with Evolution"
date: 2009-11-09
forum: General Help
---

### Post by slorunner on 2009-11-09
Hello to all! First I must say thank you to all that take their time to answer countless questions on these forums. I solved many problems with your help!
But this time I ran into a wall. Here it is:

My boss is giving up on Windows, because he is tired of endless waiting for his computer to do something. So I suggested him to try Ubuntu. I showed him how it works and I explained some thing that I know about how and why Ubunuu is faster and more reliable through time. Now he can't wait for day that the ubuntu logo will show up during the boot of his computer.

But the thing is that he has over 1000 contacts in his Outlook that are being synchronized daily with his Nokia E51. And it is a must have! So I told him, that it is also possible to sync Evolution in the same way. Today we wanted to do a test sync on my computer but with no success.

I've installed MultiSync 0.82 on my Karmic, added a new synchronization pair, set the first plugin - irmc, and the second plugin - Ximan Evolution. I have tested the bluetooth connection and it was successful. Everything ine. But when I started the synchronization procedure, the log said that the connection es successful, but there were no differences found. Although there were no contacts in the Evolution. 

What am I doing wrong? Ive spent half a day just changing the settings of synchronization pair in MultiSync, but with no luck. Does anyone have any suggstions? If you need any additional data, please let me know, and I'll post it.

Best regards,
   Peter

---

### Post by suyog on 2009-11-24
Many people have been able to sync with phones with few issues.

check following links

[http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17](http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17)

---

### Post by forest555 on 2009-11-24
In Karmic it is not possible anymore. Use Jaunty.

---

### Post by suyog on 2009-11-24
@forest555, i dont think there is any bug at least not with latest kernel and updates in 9.10.
myself and one of my friend were able to sync successfully in both directions, i.e phone<->evolution without any issues.

Please check if you have all setup correctly.

---

### Post by forest555 on 2009-11-25
Dear [suyog]("http://ubuntuforums.org/member.php?u=653498"), thank you, can you please tell how did you do that? I have used it successfully since Feisty, now it is finished.

---

### Post by suyog on 2009-11-25
Same How-to

[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)

Are you using via Bluetooth or USB cable?

---

### Post by audiomick on 2009-11-25
Hallo.
another thread on this topic :p

Mine is also broken since updating to 9.10

Nokia E61, Ubuntu Studio 64 bit. USB 

Worked fine from 8.04 tor 8.10 to 9.04.

Nothing changed except the update through the updater. I suspect evo2-sync not talking to a new version of Evolution that came with 9.10

I have read a post that said that he wsa successful with a fresh install of 9.10

Here's some more reading  ;)

[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
[http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html#obexfs](http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html#obexfs)
[http://ubuntuforums.org/showthread.php?t=260676&highlight=E65](http://ubuntuforums.org/showthread.php?t=260676&highlight=E65)
[http://www.opensync.org/wiki/releases/0.2x/syncml-guide](http://www.opensync.org/wiki/releases/0.2x/syncml-guide)
[http://ubuntuforums.org/showthread.php?t=211810&highlight=mobile+phone+mount+usb](http://ubuntuforums.org/showthread.php?t=211810&highlight=mobile+phone+mount+usb)
[http://ubuntuforums.org/showthread.php?t=204765&highlight=multisync-quad&page=2](http://ubuntuforums.org/showthread.php?t=204765&highlight=multisync-quad&page=2)

---

### Post by forest555 on 2009-11-25
> **suyog said:**
> Same How-to

[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)

Are you using via Bluetooth or USB cable?

I can not believe that! Impossible with Karmic.

I am using Bluetooth

---

### Post by suyog on 2009-11-25
I am doing it, not at all impossible. I will suggest you to check all updates including proposed, unsupported.

One more thing i have installed latest version of blueman if thats manking any difference.

---

### Post by forest555 on 2009-11-25
> **suyog said:**
> I am doing it, not at all impossible. I will suggest you to check all updates including proposed, unsupported.

One more thing i have installed latest version of blueman if thats manking any difference.

And you also are able to write from Evolution to E-series Nokia? Are you sure?

---

### Post by suyog on 2009-11-26
I am not having Eseries but N82 - Nseries but I am able to add/update/delete both ways, i.e from phone to evolution and evolution to phone.

No issues at all.

---

