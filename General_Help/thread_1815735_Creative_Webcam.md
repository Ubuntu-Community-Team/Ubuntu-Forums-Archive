---
title: "Creative Webcam"
date: 2011-07-31
forum: General Help
---

### Post by CainFoool on 2011-07-31
My creative webcam is not showing up on any sort of webcam applications.

(Cheese, Camorama)

Also, whenever I talk the microphone is very squeaky and fast.
Any help here?

---

### Post by Kooothor on 2011-07-31
Give the webcam model #

---

### Post by CainFoool on 2011-07-31
> **Kooothor said:**
> Give the webcam model #

Should of linked that, sorry.
[http://support.creative.com/Products/ProductDetails.aspx?catID=218&CatName=WebCam&subCatID=846&subCatName=Live!%20Cam%20Series&prodID=16733&prodName=Live!+Cam+Video+IM+(VF0350](http://support.creative.com/Products/ProductDetails.aspx?catID=218&CatName=WebCam&subCatID=846&subCatName=Live!%20Cam%20Series&prodID=16733&prodName=Live!+Cam+Video+IM+(VF0350)

---

### Post by Kooothor on 2011-08-01
Did you check if it was Linux compatible before buying it ?

Try to load all you might need as kernel modules to make it work.
Also, give the output of "dmesg" when you plug it in.

---

### Post by no2498 on 2011-08-01
put this in a terminal dmesg click enter
after it stops type lsusb click enter
lsusb should give you the name and number for the cam

---

### Post by CainFoool on 2011-08-02
Bus 001 Device 015: ID 041e:4067 Creative Technology, Ltd

---

### Post by tredegar on 2011-08-02
That should be supported. Try 
```
sudo modprobe gspca_ov519
```
Then plug in your camera.
See if it works now. If not then please *tell us the output of* ```
dmesg
``` after you have plugged the camera in.

---

### Post by no2498 on 2011-08-03
if it still does not come on 
look in your package manager for xawtv install it
if still not on 
try wxcam
you can get it in a deb file

 [http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by fragos on 2011-08-03
I've a Live! Cam Notebook Pro (VF0250) which works fine with Cheese. I haven't come across a web cam that didn't work with Cheese. Did you try looking the device selection in Preferences. You may have another video class device like a TV card that UDEVed the video0 dev. In that case your web cam should be in the list of devices select-able.

---

