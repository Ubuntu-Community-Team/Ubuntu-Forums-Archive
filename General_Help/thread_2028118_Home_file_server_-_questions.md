---
title: "Home file server - questions"
date: 2012-07-17
forum: General Help
---

### Post by ezra4no1 on 2012-07-17
I would like to set up a simple file server for my home, but have some questions.

I'll be using a couple of USB drives, one for a shared volume, the other basically as a back up to the first drive to protect my data should a drive go bad.

My question, how would I mirror the 1st drive to the 2nd drive? I'm not trying to set up a  software raid here, as I believe this would add overhead to an already slow CPU, but I want to copy data that's placed on the shared drive. In the world of Windows, I can use some freeware back-up software that will allow me to do this in time intervals or in real time as data is written to the space. How can this be done in Ubuntu?

Next...
Is there a decent free anti-virus program I can use to scan in real time (as data is written) for Ubuntu?  Since my family will be using this, it would be nice to make sure no viruses gets out to the shared volume.

Last...
In order to also use the server to stream media files to devices like a Boxee, or xbox360, would I need some kind of media extender that is used on Window computer\home servers? If so can this be done in Ubuntu?

Thanks in advance for any tips :)

---

### Post by trundlenut on 2012-07-17
> **ezra4no1 said:**
> I would like to set up a simple file server for my home, but has some questions.

I'll be using a couple of USB drive, one for a shared volume, the other basically as a back up of the first drive to protect my data should a drive go bad.

My question, how would I mirror the 1st drive to the 2nd drive? I'm not trying to set up a  software raid one here, as I believe this would add overhead to an already slow CPU, but I like to copy data that's placed on the shared drive. In the world of Windows, I can use some freeware back-up software that will allow me to do this in time intervals through or in real time as data is written to the space. How can this be done in Ubuntu?


rsync?

> **ezra4no1 said:**
> 
Next...
Is there a decent free anti-virus program I can use to scan in real time (as data is written) for Ubuntu?  Since my family will be using this, it would be nice to make sure no viruses get out to the shared volume.


ClamAV and cron?

> **ezra4no1 said:**
> 
Last...
In order to also use the server to stream media files to devices like Boxee, or xbox360, would I need some kind of media extender that is used on Window computer\home servers? If so can this be done in Ubuntu?

Thanks in advance for any tips :)

Errr don't know about this one.

Have you considered something like FreeNAS as an alternative?

---

