---
title: "Copy to ISO 11.04"
date: 2011-06-04
forum: General Help
---

### Post by Drate on 2011-06-04
I can find no way to copy a cd to ISO in 11.04, either GUI or CLI.

Brasero does not have .iso option though the brasero-cdrkit is installed and is latest version.

Evidently the /dev/cdrom is no longer used?  I'm not sure what's going on there but anytime I try to use dd or cat I get and Input/Output error.

Can anybody help shed some light for me here?

---

### Post by 3xp10r3r|X13 on 2011-06-04
Weird, usually Brasero has that option (burn image to disc). However, you can try K3b. Install it (software center or sudo apt-get install K3b). Click onto more actions and select "burn image".

That should work

(if it is a hardware issue....well...sry)

---

### Post by Drate on 2011-06-04
So Brasero SHOULD have the .iso option in 11.04?

---

### Post by 3xp10r3r|X13 on 2011-06-04
I'm just used to it, referring to older versions of Ubuntu, but unfortunately I can't really check right now, because I'm running Slackware.

However, if you're still missing the option to burn an iso image, just try out Kb3. (..weird)

---

### Post by Joe- on 2011-06-04
Does your Brasero not look like this?

---

### Post by Drate on 2011-06-04
Where in K3b is the "Copy to ISO" option?

Also, Brasero does look as  indicated in your screenshot, however, when clicking on copy, telling it to copy to image, then going to properties and selecting the image type, this is what I find:

---

### Post by iclestu on 2011-06-04
> **Drate said:**
> Where in K3b is the "Copy to ISO" option?



Click 'copy medium' button then a dialogue box pops up (see attached), with 'only create image' checkbox.

Hope that helps....

---

### Post by iclestu on 2011-06-04
ooops - forgot attachement!

---

### Post by Drate on 2011-06-04
When performing the above instructions for K3B, what I get is a folder called "k3bCdCopy0" with all the files inside, I do not get an ISO.

---

### Post by dFlyer on 2011-06-04
Do I understand you correctly, you  want to create an iso from a cd?

---

### Post by dFlyer on 2011-06-04
If you want to copy a cd to an iso file. Start Brasero, select disk copy. Make sure your disk is in the drive and select disk to copy to and change that to iso. click property and name your iso

---

### Post by Drate on 2011-06-04
> **dFlyer said:**
> Do I understand you correctly, you  want to create an iso from a cd?

Yes sir!  Please tell me you have wisdom and insight in this matter in 11.04!

---

### Post by Drate on 2011-06-04
Could you please provide a screenshot of the afrementioned instructions in which ISO is an option.

I don't mean to be dense, but I can not find ISO as an option to write to.

---

### Post by iclestu on 2011-06-05
> **Drate said:**
> When performing the above instructions for K3B, what I get is a folder called "k3bCdCopy0" with all the files inside, I do not get an ISO.


My apologies, i thought it wrote an iso.

However, you can now make an iso out of that folder with the command 

```

mkisofs -o /path/to/directory/cd.iso /path/to/directory/
```Not as clean as you would have hoped... Im sure there must be a simpler way but this will get u going in meantime. :)

---

### Post by Drate on 2011-06-05
Ah, thank  you, I'll try that method soon as a work around, but I will also continue searching for an answer as to how to make bit for bit images of a CD.  It is an important function in my work.

And for those who might be wondering, it is not movie ripping, in this specific case, I was needing to make available for download a CD of unmastered music to my Uncle so he could review prior to having the CD sent off for final mastering.

---

### Post by Drate on 2011-06-05
While trying a different type of DISC (a movie DVD instead of an audio CD, purely for testing, I did not actually complete the action, thus no infringement of DMCA), I opened up Brasero and ISO is the ONLY option.

So it's apparently noting the type of media and allowing only certain selections based on that type.

---

### Post by IanW on 2011-06-05
You may also want to try "AcetoneISO", which has the option "Generate ISO from CD/DVD"

---

### Post by Drate on 2011-06-05
I just installed and tried it, and when you goto start the job, it pops up a message stating that it will be creating a TOC/IMG that can not be mounted or read in any way (it's words, not mine), so on and so forth, but ultimately, is not an ISO.

---

### Post by linuxinstalledfromhdd on 2011-06-05
> **Drate said:**
> I can find no way to copy a cd to ISO in 11.04, either GUI or CLI.

Brasero does not have .iso option though the brasero-cdrkit is installed and is latest version.

Evidently the /dev/cdrom is no longer used?  I'm not sure what's going on there but anytime I try to use dd or cat I get and Input/Output error.

Can anybody help shed some light for me here?

So you want to rip a cd into mp3s (or something like lossless if you want crystal quality etc), so you can send them to your cousin?  

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

Terminology can be a real pain sometimes.  :)

---

### Post by Drate on 2011-06-05
I appreciate your response, it is good to be watching for opportunities to help and of course the more eyes watching the better the likelihood that the needs of the Original Poster will be met; but no, I am not wanting to rip a CD into MP3s.

My intention was to do exactly this: to take an audio CD (comprised of about 16 .wav files of unmastered music), then copy the CD to an ISO image, at which point I was going to make it available for download on my home website that I maintain for just such an occasion (yeah, I'm that kind of dork), thus allowing my Uncle to download the ISO, right click it, and do a "write image to disk", which is super simple, thus, less room for error.

Instead what I had to do was send him a zip of the files, and have him unzip it, at which point he had to use some other third party program to burn the files into an audio cd.  Which ultimately worked out fine, but you can see where right-click -> burn would be much simpler than unzip -> open third party program -> navigate program to burn feature -> burn.

Also, it is quite frustrating that a common tool for linux users is not being as simple to use (or else I am missing some fundamental step) as it has been for some years previous.  Though I'd like to point out that the job Canonical and the Developer Community have been doing is just brilliant.  This is one power user's present gripe about one issue.

I would have been happy to do a Disk Dump, but even dd is failing me at this point.  I have tried this on two different machines.  I am gathering that /dev/sr0 represents the CDROM based on dmesg output, but I keep getting I/O errors when I try to execute a

```
dd if=/dev/sr0 of=./test.iso
```

So at this point I'm honestly stumped.  I can't seem to make a bit for bit image of my discs, and also I cannot seem to point Wine to a cd drive (which prevents me from using, say, Infrarecorder).

Honestly, I could create an interface to handle using DD if I could just find out what device to point dd (or wine) to that would work.

I just was trying to avoid saying all of that because it tends to muddy the issue, which is: I can't rip to ISO.

But seriously, I'm excited about the prompt and informative responses, and appreciate all the attention and time taken thus far.

---

### Post by Drate on 2011-06-05
AHA (sort of)!  Apparently the issue is that I am specifically working with an audio cd.

I am gathering that Movie DVD's will have issues of there own as well.

But when working with a regular Data Disc (specifically puppy linux 525) I had NONE OF THE DESCRIBED ORIGINAL ISSUES.

Disk Dump works, Brasero works, Infrarecorder works (under wine).

Now I just have to figure out how to work around this audio cd business... I suppose I can mark this thread as solved as I can in fact copy a cd to ISO file now, just not ANY cd.

---

### Post by iclestu on 2011-06-06
> **Drate said:**
> AHA (sort of)!  Apparently the issue is that I am specifically working with an audio cd.

I am gathering that Movie DVD's will have issues of there own as well.

But when working with a regular Data Disc (specifically puppy linux 525) I had NONE OF THE DESCRIBED ORIGINAL ISSUES.

Disk Dump works, Brasero works, Infrarecorder works (under wine).

Now I just have to figure out how to work around this audio cd business... I suppose I can mark this thread as solved as I can in fact copy a cd to ISO file now, just not ANY cd.

curious. Looks like that the devs just didnt think audio-->iso was a necessary option anymore. 

Modern desktop OS's (of all flavours) are generally able to rip and burn audio cd's seamlessly without ever having to see or worry about the image files so if my assertion is correct you can understand their reasoning but why remove it rather than just hiding it away somewhere? maybe there is a configuration option hidden in the darkest depths somewhere???

---

### Post by Drate on 2011-06-06
Oh, if I really felt like monkeying around with how the CDROM is mounted I'm sure I could.  But I try to work within the default and recommended environments as much as possible.  Of course, having said that, I am curious how one might temporarily alter the way the CD is viewed for purposes of creating "an app for that".

The most curious part, though, is that "dd" didn't work.  I have verified that /dev/cdrom still refers to the CD, so why was I getting an I/O error?  My only guess is that it could be an attempt to build in a security measure against the illegal use of ripping CD's and DVD's.  If that is the case I have to both applaud and be frustrated with the developers.  Perhaps in the future, when they have some downtime from all the other uber-awesome things they do, they might put in some way to check if the disc is intended to be copy protected or not?  Perhaps that is not possible with the way audio CD's are made?

---

