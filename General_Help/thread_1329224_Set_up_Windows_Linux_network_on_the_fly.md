---
title: "Set up Windows Linux network on the fly"
date: 2009-11-17
forum: General Help
---

### Post by healee on 2009-11-17
One of my Windows computer with Vista system wouldn't boot.  I am trying to set up a network between Linux and Windows using ubuntu 9.04 Desktop Edition so that I can transfer data files from the unbootable computer to another Windows system.

At present, ubuntu just wouldn't mount anything from another Windows system.  Am I to set up samba on ubuntu?  How do I go about setting up on the ubuntu and Windows?  I am booting up the unbootable Windows system with the ubuntu CD.

---

### Post by mdurham on 2009-11-17
Would it be easier to plug the drive into the Windows computer?

---

### Post by Aubergines on 2009-11-17
Basically you'll need to make sure a) the ubuntu livecd is on the network and b) you can mount the windows partition on the livecd. I have no idea what your level of linux knowledge is and I was thinking of a way of explaining how to do the above without having into detail on how linux mounting works, how to find you hard disk in /dev, the windows partition structure, ifconfig and possibility having to use the commandline to do it.

But then I found this which saves on all the explaining I need to do - [http://theseus.posterous.com/ubuntu-to-the-rescue](http://theseus.posterous.com/ubuntu-to-the-rescue)

---

### Post by coffeecat on 2009-11-17
> **healee said:**
> At present, ubuntu just wouldn't mount anything from another Windows system.  Am I to set up samba on ubuntu?

Jaunty (9.04) was a bit odd in that sometimes browsing smb shares worked out of the box, and sometimes one had to do a bit of fiddling. At least that was my experience with Jaunty on about 5-6 different machines.

Anyway, I found it useful first to set up a Windows share in my Jaunty box. Create a folder in home, right-click on it > 'Sharing Options'. Try to create a share and let the system download and install the samba stuff. Log out and in again and then finish creating the share with that folder.

If then you still cannot browse shares on your Windows system, have a look at the first post in this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

It's a bit more straightforward than it appears. :-s Just go through the points and you should be fine. With that guide I can now browse Windows shares in any combination of Jaunty >< Karmic >< Windows >< MacOS >< Western Digital 'MyBook' NAS.

---

### Post by healee on 2009-11-19
> **mdurham said:**
> Would it be easier to plug the drive into the Windows computer?

Thanks for reminding me.  It is a laptop.  I hope to find my laptop hard drive adpator and try it out.  I often have problem taking parts out of laptops.  I haven't tried this one though.

It is more convenient to be able to transfer files without doing all these physical works.  Seeing all the kind responses below, it looks like I am having a lot of material to read.

---

### Post by healee on 2009-11-19
> **Aubergines said:**
> But then I found this which saves on all the explaining I need to do - [http://theseus.posterous.com/ubuntu-to-the-rescue](http://theseus.posterous.com/ubuntu-to-the-rescue)

I don't use Linux a lot but I think I can follow instructions.

I followed the given web page.  I have copied a few files to a USB drive.  However I couldn't connect to a shared directory in a Windows system of another computer so that I can transfer files.  In this case it was a Windows 7.  I need to connect to another system because I need to retrieve a lot of files.

For your information I booted up the unbootable Vista laptop with ubuntu 9.04 Desktop Edition while having it connected with a Cat5 cable to a router that had a Windows 7 Ultimate computer on the other end.

By the way I also have a ubuntu 8.04.1 LTS Desktop Edition.  If you can help me connect to another computer, that would be good.

---

### Post by healee on 2009-11-19
> **coffeecat said:**
> 
Anyway, I found it useful first to set up a Windows share in my Jaunty box. Create a folder in home, right-click on it > 'Sharing Options'. Try to create a share and let the system download and install the samba stuff. Log out and in again and then finish creating the share with that folder.

If then you still cannot browse shares on your Windows system, have a look at the first post in this thread:[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Are your instructions suitable for using live CD?  I am booting up an unbootable Windows Vista laptop with the ubuntu 9.04 CD hoping to transfer the files in the  broken Windows system to another Windows systems on the network.

Your instructions including those on the given web page require a lot of change in the ubuntu system.  How was I supposed to do while I was using a live CD?  Only thing I did was I changed the workgroup of the Windows system to "workgroup" to match that of the ubuntu's.

Could you please elaborate?  Thanks!

---

### Post by coffeecat on 2009-11-19
> **healee said:**
> Are your instructions suitable for using live CD?


Not really. I missed the last sentence in your first post about the live CD - my apologies. When I say not really, you probably could in theory, but it would need several service restarts if you had to do many of the tweaks in that page. Instead I have a different suggestion.

I notice that you are using the 9.04 (Jaunty CD). I find that samba sharing in a fresh install of 9.10 (Karmic) doesn't have the issues that were in Jaunty. Hopefully, that would be true when using the live CD of 9.10. Why not download the 9.10 ISO and try that instead?

However, you are trying to use a live Ubuntu CD to transfer data from a broken Vista box to another Windows system. Have I read that right? I might be missing something here, but why not simply plug in an external USB drive while using the live CD and use that to transfer files from one machine to another?

---

### Post by audiomick on 2009-11-19
Hate to have to say it, but there were Samba issues with 9.10 as well. My desktop stopped seeing shares after the update that it had been able to find up till then. I found a number of posts regarding the problem, which in the end seemed to have to do with a "dns redirection" function at the Internet provider. Maybe the problem would not show up in a "local only" network.

USB drive sounds like the easy way out to me too...

---

### Post by healee on 2009-11-19
> **coffeecat said:**
> However, you are trying to use a live Ubuntu CD to transfer data from a broken Vista box to another Windows system. Have I read that right? I might be missing something here, but why not simply plug in an external USB drive while using the live CD and use that to transfer files from one machine to another?

Yes, that is what I intend to do.  To transfer files from the broken one to another.  I am expecting to transfer a lot of files.  I have a 4GB USB drive.  I suppose the amount to be retrieved could well be over that.

I suppose I could re-install the current operating system in situ which is Vista.  I believe doing so would leave the documents and data files intact.

I still would like to be able to set up a network with Windows and Linux capable of sharing files among one another one day though, be with a Linux live CD or a installed Linux system.  I do have ubuntu 8.04.1 LTS installed on one of my computers multi-booted with a few Windows operating systems.

---

### Post by healee on 2009-11-20
Is there any information that can help me set up a network of two ubuntu 8.04.1 systems?  I have ubuntu 8.04.1 installed on one computer.  I am thinking of running ubuntu 8.04.1 live CD on the broken Windows laptop so that I can transfer files to the other ubuntu which multi-boots with Windows.

---

