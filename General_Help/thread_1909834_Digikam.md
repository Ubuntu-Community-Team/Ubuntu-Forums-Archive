---
title: "Digikam"
date: 2012-01-16
forum: General Help
---

### Post by oldgreygary on 2012-01-16
I am not sure if this is the right place for this but I need to start somewhere. I have installed Digikam (V2.1.1) and libgphoto2 (V2.4.11-3) from the Ubuntu software centre. I am running Ubuntu v11.10.

While running Digikam I am trying to upload photos from a digital camera (Canon Poweshot G2). I use the cameras connections and connect via a USB port. The camera is recognised by Ubuntu. When I run Digikam there is an option to import. This has an option called  Camera. In there the camera is recognised and is labelled as auto-detected. However, from within the Digikam software I cannot upload the images. 

So, I am not sure where the problems lies? Is it Ubuntu, Digikam or libgphoto2. 

From within Ubuntu I can look at the images as it seems to recognise it as an external device. So, I copied them from there. However, it would be nice to be able to get Digikam working correctly. So, if anyone has any ideas or thoughts then I would be interested to hear from you.

Thanks.

Cheers for now

Gary

---

### Post by mikewhatever on 2012-01-16
Hm..., so you've been trying to upload photos from the digital camera ... to where???

---

### Post by sffvba[e0rt on 2012-01-16
This may be entirely unrelated but I tried digiKam for the first time in Ubuntu (and not Kubuntu) a few hours ago and I got the following error messages when I ran it for the first time:

```
Configuration file "/home/nlsthzn/.kde/share/config/knotifyrc" not writable.
Please contact your system administrator.
```

```
Configuration file "/home/nlsthzn/.kde/share/config/digikamrc" not writable.
Please contact your system administrator.
```

And now I can't import any photos from my local disc.  Maybe the same issue is letting digiKam see the photo's but make it impossible to import?

**EDIT: Seems my issue above is not pertaining the the issue that OP is having (when I ignored the errors and chose my Pictures folder rather than *Pictures -> Photos* as my folder I want to import from it imported *Photos* for some strange reason and seems to be working OK other wise.**


404

---

### Post by Quarkrad on 2012-01-16
I'm a newbie but I think I know what the problem is - I have another post on this site (**Autorun Digikam when Camera Switched On**) waiting for an answer.  The problem is the same in 10.10 - you cannot import.  The issue is that when you plug the camera in, Ubuntu **mounts** it - this is a problem for Digikm.  In order to import pictures you have to configure Ubuntu to _not_ **mount** the camera when it is switched on - the way to do this is in my thread/question above.  When you do this the import function works very well.  The issue is - how do we do the same thing (use configuration editor) to do something that is easy in 10.10 in 11.10?

---

### Post by oldgreygary on 2012-01-16
> **mikewhatever said:**
> Hm..., so you've been trying to upload photos from the digital camera ... to where???

Don't understand your reply? What do you mean to where? The obvious answer is onto my hard drive. Perhaps, you could be more explicit in what you are asking as it would be more helpful.

As explained in my question. I have connected it via a USB port and am trying to import via Digikam. It is recognised by Ubuntu as an external drive. I can see the images if I go through the normal Ubuntu software to view files.

What I can't do is import them via Digikam.

Gary

---

### Post by oldgreygary on 2012-01-16
> **Quarkrad said:**
> I'm a newbie but I think I know what the problem is - I have another post on this site (**Autorun Digikam when Camera Switched On**) waiting for an answer.  The problem is the same in 10.10 - you cannot import.  The issue is that when you plug the camera in, Ubuntu **mounts** it - this is a problem for Digikm.  In order to import pictures you have to configure Ubuntu to _not_ **mount** the camera when it is switched on - the way to do this is in my thread/question above.  When you do this the import function works very well.  The issue is - how do we do the same thing (use configuration editor) to do something that is easy in 10.10 in 11.10?

All the above makes sense to me as it mirrors the problems I am having. But, I don't have a solution?!

Gary

---

### Post by sffvba[e0rt on 2012-01-16
> **oldgreygary said:**
> All the above makes sense to me as it mirrors the problems I am having. But, I don't have a solution?!

Gary

Have you tried right clicking on the camera (should be in the taskbar) and selecting un-mount.  digiKam should then have access to import from it.


404

PS - I am going to go hunt for my camera to see what it does and how it works :p

---

### Post by WasMeHere on 2012-01-16
> **Quarkrad said:**
> I'm a newbie but I think I know what the problem is - I have another post on this site (**Autorun Digikam when Camera Switched On**) waiting for an answer.  The problem is the same in 10.10 - you cannot import.  The issue is that when you plug the camera in, Ubuntu **mounts** it - this is a problem for Digikm.  In order to import pictures you have to configure Ubuntu to _not_ **mount** the camera when it is switched on - the way to do this is in my thread/question above.  When you do this the import function works very well.  The issue is - how do we do the same thing (use configuration editor) to do something that is easy in 10.10 in 11.10?


> **oldgreygary said:**
> ...
As explained in my question. I have connected it via a USB port and am trying to import via Digikam. It is recognised by Ubuntu as an external drive. I can see the images if I go through the normal Ubuntu software to view files.

What I can't do is import them via Digikam.

Gary

Hi,

I'm using DigiKam in Ubuntu 10.04 LTS and I am happy with it, and I wish to help you.

What happens if you simply unmount the camera using the file browser Nautilus? You should do that pressing the eject symbol next to the drive icon and name in the left panel. If that does not work, it could be because root has mounted it. In that case try it via the terminal window (ctrl + alt + t) either by starting the file browser as root (superuser) or directly.
```
sudo nautilus
``` or
```
df
``` to find out what to unmount
```
sudo umount /dev/sdxy
``` where x and y should be selected from the information in the output of ***df***

Have fun finding out :-)
Olle

---

### Post by sffvba[e0rt on 2012-01-16
FTR - Trying digiKam in 12.04 I have unmounted the camera and digiKam does see it but clicking on import does absolutely nothing.

Opened up Shotwell and importing merrily.

Bug perhaps?



404

---

### Post by WasMeHere on 2012-01-16
Well, maybe it is a bug. Do you have a card reader? In that case, what happens if you insert your flash memory card into it and try to import from there?

If it is a bug in DigiKam, I suggest you use ***not found***'s information and import the photo files using Shotwell. Or simply import via the file browser.

---

### Post by oldgreygary on 2012-01-16
I also tried unmounting and did not make a difference. However, I think that when the camera is connected via USB it is owned by something called gphoto2. I think(?) that is what is being used by Digikam to say that the camera has been autodetected. So, possibly the problem is in this suite of programs, Gphoto2, libgphoto2 etc. 

The version of Digikam I have is 2.1.1(came from software depository) which I noticed is a few behind the current version on the Digikam site. Perhaps, there is a mis-match of software?

Gary

---

### Post by WasMeHere on 2012-01-16
> **oldgreygary said:**
> I also tried unmounting and did not make a difference. However, I think that when the camera is connected via USB it is owned by something called gphoto2. I think(?) that is what is being used by Digikam to say that the camera has been autodetected. So, possibly the problem is in this suite of programs, Gphoto2, libgphoto2 etc. 

The version of Digikam I have is 2.1.1(came from software depository) which I noticed is a few behind the current version on the Digikam site. Perhaps, there is a mis-match of software?

Gary
Yes, it could be a mismatch, particularly if the other software (Gphoto2) was not installed from the repositories.

---

### Post by oldgreygary on 2012-01-16
I just tried a couple of things to help clarify things. Digikam uses a number of functions which come from gphoto. These include libgphoto2. There is also a program called gphoto2. The lib functions(I think) are what digikam uses. Gphoto2 is a command line argument that you can use to manually load images. (It can be downloaded from software depository).

I thought I would try running gphoto2 from the command line to see what happens. I connected the camera via USB port. When I tried to run gphoto2 it error'd saying it was already in use. So, as suggested in previous posts I unmounted the camera.

This then allowed me to run gphoto2 from the command line. Example commands

gphoto2 --list-ports (checks what ports are available)
gphoto2 --auto-detect (checks for connected cameras)
gphoto2 --summary (Lists details about the camera
gphoto2 --List-files (shows files on camera)
gphoto2 --get-all-files (uploads files to current directory)

I was able to run these commands and to manually upload images from the camera.

So, to summarise there seems to be two issues. Firstly, once the camera is connected it needs to be unmounted (as suggested). The second issue seems to be that it is Digikam which is not working. As manually operating the 
gphoto software is ok and can access and upload images ok.

I will try and report to Digikam to see if they can offer a solution.

Response from Digikam forum as follows:

Yes, the official digikam 2.1.1 packages from Ubuntu 11.10 have disabled the gphoto2 support during build so it doesn't matter if you have installed what's needed. 

Gary

---

### Post by Quarkrad on 2012-01-16
Seems a retrograde step - wonder why they did that?  Having built in the functionality strange they disable it???? Another reason not to move to 11.10

---

### Post by oldgreygary on 2012-01-17
> **Quarkrad said:**
> Seems a retrograde step - wonder why they did that?  Having built in the functionality strange they disable it???? Another reason not to move to 11.10


It seems as though Ubuntu's preferred software for photos is Shotwell. I think it uses the same functions. The photo2 functions are the current ones. In an earlier response someone said Shotwell worked ok, But, it does not have the same functionality as Digikam.

I cannot see the point of having it in the software depository if it is not going to run with all the functions?!

Anyway, I think that I might opt to use GIMP for editing and use another program to manage photos.

Gary

---

### Post by WasMeHere on 2012-01-17
> **oldgreygary said:**
> It seems as though Ubuntu's preferred software for photos is Shotwell. I think it uses the same functions. The photo2 functions are the current ones. In an earlier response someone said Shotwell worked ok, [COLOR="Red"]But, it does not have the same functionality as Digikam[/COLOR].

I cannot see the point of having it in the software depository if it is not going to run with all the functions?!

Anyway, I think that I might opt to use GIMP for editing and use another program to manage photos.

Gary

I agree that Digikam is much better for organizing photos. I'll stick to it, even if it means that I will have to import photos via another program or simply via the file browser. I run 'vanilla' Ubuntu 10.04 LTS, where Digikam is still working well. By the way, when I installed it, I also received a lot of KDE software, that I use occasionally. Maybe I will switch to Kubuntu, when it's time to upgrade to the next LTS version.

---

### Post by Quarkrad on 2012-01-18
Seems Ubuntu is going the way of Apple Mac - where 'they' decide what software you will use on a Mac. Apple have an argument that their software works and tightly controlled but if you prefer to other software there is little/no support.  Personally I find this a bit arrogant but I guess there is a point.  Just look at the Apple forums where people are trying to get all sorts of things to work properly (such as Thunderbird) - Apple don't care, they have decided what you will use on their platform even if there is something better or you prefer to use something else.  It will be a pity if Ubuntu go the same way.

---

### Post by ianp5a on 2012-01-21
Well they do have the responsibility to deliver a distro that works reliably. Which can be tricky. 

I had  the same problems with DigiKam. I changed over to Shotwell for importing my pictures. Which works well now they've included videos too.

You can still use DigiKam for managing, after you have imported them with Shotwell.

---

