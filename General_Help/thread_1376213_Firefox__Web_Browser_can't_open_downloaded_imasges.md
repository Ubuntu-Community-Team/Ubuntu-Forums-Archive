---
title: "Firefox / Web Browser can't open downloaded imasges"
date: 2010-01-08
forum: General Help
---

### Post by L a r r y on 2010-01-08
**Firefox / Web Browser Can't ipen downloaded images**
I have been using Firefox 3.0 with good success, and recently switched to Firefox 3.5 (unbranded version,  called A Web Browser).

I was looking around in Google images and downloading a few images in Web Browser 3.5, when my problems began.  Firefox and Web Browser run off the same profile, and neither browser will open image files correctly.  I call Web Browser WB for short.
All of a sudden I cannot open jpg images.  I saved image as... and when the download was complete, I tried to open it.  WB needed an application to open with, so I selected to open the containing folder instead.  WB needed an application to open with again.  It has all of a sudden gotten stupid.

Not knowing the name of the Ubuntu image viewer, (which is eog for Eye of Gnome) I went over to /usr/bin and selected the document viewer, evince, to open the jpg image, which didn't work, so I selected nautilus as the application to open the folder with.

Now I can open the folder all right, and from there, I can open the jpg picture from within that folder, but I am now told in the WB and Firefox download window that /path/to/picture.jpg is not a folder in response to my trying to open the downloaded image.

I performed some other checks:

I can successfully download and open a pdf document;
I cannot open a png or gif image, for they are not folders.

A check of Preferences and Applications tab shows no listing for jpg, gif or png or the word image under content type.  There is no provision there to create a  new entry, either.

I checked and compared Firefox Preferences Applications tab with that of Web Browser.  They appear to be identical in content.

What do I do next?  I will log out of 9.04 and back in again, and if that doesn't work, I will restart the computer after I finish my post.  Then I will come back with the findings.

---

### Post by L a r r y on 2010-01-08
[SIZE="4"]Firefox / Web Browser can't open downloaded images[/SIZE]
Further information:  Log out and log in did not solve the problem.  I ran a ```
sudo touch /forcefsck
``` and rebooted.  Still no help, but the filesystem checks out good.

Helper applications are chosen by mime type, and it seems that some mime tyoes are not accounted for.> Firefox / Web Browser can't open downloaded images
I have been using Firefox 3.0 with good success, and recently switched to Firefox 3.5 (unbranded version, called A Web Browser).

I was looking around in Google images and downloading a few images in Web Browser 3.5, when my problems began. Firefox and Web Browser run off the same profile, and neither browser will open image files correctly. I call Web Browser WB for short.
All of a sudden I cannot open jpg images. I saved image as... and when the download was complete, I tried to open it. WB needed an application to open with, so I selected to open the containing folder instead. WB needed an application to open with again. It has all of a sudden gotten stupid.

Not knowing the name of the Ubuntu image viewer, (which is eog for Eye of Gnome) I went over to /usr/bin and selected the document viewer, evince, to open the jpg image, which didn't work, so I selected nautilus as the application to open the folder with.

Now I can open the folder all right, and from there, I can open the jpg picture from within that folder, but I am now told in the WB and Firefox download window that /path/to/picture.jpg is not a folder in response to my trying to open the downloaded image.

I performed some other checks:

I can successfully download and open a pdf document;
I cannot open a png or gif image, for they are not folders.

A check of Preferences and Applications tab shows no listing for jpg, gif or png or the word image under content type. There is no provision there to create a new entry, either.

I checked and compared Firefox Preferences Applications tab with that of Web Browser. They appear to be identical in content.

What do I do next? I will log out of 9.04 and back in again, and if that doesn't work, I will restart the computer after I finish my post. Then I will come back with the findings.


---

### Post by L a r r y on 2010-01-09
[SIZE="4"]Firefox / Web Browser can't open downloaded images[/SIZE]
Update:  I opened a link in an email, which opened the default Firefox 3.  Firefox was working OK until I fired up Web Browser 3.5 and tried to download an image.

I disabled a few add-ons, and while doing so, I found the Ubuntu Firefox Modifications 0.7 were disabled due to incompatibility.

I could not resolve Web Browser's issues, so I uninstalled it.  Web Browser was all set to be upgraded to Firefox 3.57, according to information in Synaptic Package Manager, so I may try again with an installation of Firefox 3.57.  It was working at one point, or so I thought.

Call this one solved.  It turns out to be an incompatibility issue in Ubuntu 9.04.

> **L a r r y said:**
> [SIZE="4"]Firefox / Web Browser can't open downloaded images[/SIZE]
Further information:  Log out and log in did not solve the problem.  I ran a ```
sudo touch /forcefsck
``` and rebooted.  Still no help, but the filesystem checks out good.

Helper applications are chosen by mime type, and it seems that some mime types are not accounted for.

---

