---
title: "sideways photo thumbnails."
date: 2010-11-02
forum: General Help
---

### Post by avocadorange on 2010-11-02
Greeting Ubuntu brothers and sisters, I am a new forum member, been using Ubuntu since July 2010. It is also my first experience w/Linux. I am rather unsophisticated with computer stuff (installing Ubuntu was probably my single greatest technical accomplishment to date).


I am having the exact same problem as russianbandit:
[http://ubuntuforums.org/showthread.php?t=1457699&highlight=sideways+picture+thumbnails](http://ubuntuforums.org/showthread.php?t=1457699&highlight=sideways+picture+thumbnails)

Namely some of my photo thumbnails appear "sideways"; these photos also upload to websites sideways as well. See my profile pic, for example.

To correct the problem, I tried to download gthumb as was suggested, but got this message from the gthumb website: 

"Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I'm out of my depth here. Can someone explain how I "check the file permissions and correctness of the file"?

Thanks everyone

---

### Post by cprofitt on 2010-11-18
I would guess that the meta-data embedded in the photo may indicate the orientation of the photo. Have you tried editing the photo in GIMP or another bitmap image editor?

---

### Post by avocadorange on 2010-11-20
Thanks for the response! Sorry but I don't know what Gimp is. I do use the the F-Spot photo manager provided with Ubuntu, and things look fine there. It's just the thumbnails that are sideways. This results in the photos I upload to websites such as this one *also* being sideways.

Actually my post was more about this particular message: "Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

This is incomprehensible to a newbie like me. If anyone can help me understand the above instructions, your input will be most welcome.

---

### Post by avocadorange on 2010-11-20
To update my previous post(s) I was able to install gthumb but it doesn't appear to make any difference to this problem. The original problem of the sideways photos persists.

---

### Post by harry1868 on 2010-11-20
Software index broken is due to some of the installed packages are corrupt or the pacakage you are trying to remove may not fully removed.
Can you try 

apt-get -f install
 and post here the results, so that i can help You

---

### Post by harry1868 on 2010-11-20
Software index broken is due to some of the installed packages are corrupt or the pacakage you are trying to remove may not fully removed.
Can you try 

apt-get -f install
and post here the results, so that i can help You

---

### Post by yetiman64 on 2010-11-21
A simple fix is,
```
sudo apt-get install nautilus-image-converter
```this will install the nautilus menu entries for resizing and rotating (what you need here) images. Imagemagick is also installed as it is the package that does the actual alterations.

To use after installation, right click a file and select "Rotate images" from the menu. Set the correct rotation and choose "rotate in place" or "append" to rename the rotated file and preserve the original (whichever is your preference, Edit2: though note that multiple files can be rotated at the same time if you choose the "append" option, while only a single file can be rotated with the "rotate in place" option).

_*If you prefer to use gthumb*_, use the Image > Transform > (choose the suitable rotation option) toolbar options. Then save the file. Installing gthumb won't automatically fix the problem as I believe it just loads the file in accordance with the exif data embedded in the file.

---

### Post by avocadorange on 2010-11-21
Thanks, pasted that command into the terminal, this is what I got:


~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by yetiman64 on 2010-11-21
> **avocadorange said:**
> Thanks, pasted that command into the terminal, this is what I got:


~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

needs "sudo" before it. (without the quotes)

---

### Post by avocadorange on 2010-11-21
> **yetiman64 said:**
> A simple fix is,
```
sudo apt-get install nautilus-image-converter
```this will install the nautilus menu entries for resizing and rotating (what you need here) images.

Thanks very much for your reply. Actually I tried both nautilus image converter and gthumb and neither solved my problem. Let me attempt to be clearer about the problem. 

I previously mistated that the problem was with the photo thumbnails. A more exact description is this: When I first look at my photos through Nautilus thumbnails, or F-spot, or Eye of Gnome, or Gthumb, the images are "correctly" oriented, i.e. they appear as I intended them to.

The problem is mainly when I try to upload profile pictures on sites such as this one or Facebook. You click on the upload button, and the pictures look fine in thumbnail mode until you select one. In the preview mode, photos taken vertically appear "sideways" and are also uploaded in that position as well. Nor can I seem to edit the photos to appear "right side up". Neither gthumb or nautilus image converter make any difference. 

The problem doesn't seem to effect "non-profile" pictures. 

Again, any suggestions are appreciated.

---

### Post by avocadorange on 2010-11-21
> **yetiman64 said:**
> needs "sudo" before it. (without the quotes)

Thanks, tried that and this is what came out:


xxx@xxx-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

(Guess you guys are going to tell me to upgrade those 25?)

---

### Post by yetiman64 on 2010-11-21
> **avocadorange said:**
> Thanks, tried that and this is what came out:


xxx@xxx-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

(Guess you guys are going to tell me to upgrade those 25?)Yes :) good idea to keep up to date.

No problems with your install by the looks (-f switch means fix-broken and nothing showed up, which is good), those 25 can be updated with Update manager (worth doing to see what they are at least)

Or to do the job in terminal that the update manager does you can use,
```
sudo apt-get update && sudo apt-get upgrade
```Thanks for the clarification in your previous post, I'll have to leave it to someone who has experienced that problem, and hopefully found a fix, to help you out more. Best of luck with finding a fix.

---

