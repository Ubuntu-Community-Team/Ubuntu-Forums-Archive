---
title: "Images not rotated correctly on upload"
date: 2010-04-18
forum: General Help
---

### Post by russianbandit on 2010-04-18
I have some pictures that were taken vertically and they show up rotated correctly in nautilus and F-spot correctly. But when I go to upload an image to the web, the preview in the image upload dialog shows the pictures on their side, or horizontal. As a result the uploaded images ends up being horizontal and not vertical, like I want it too.

To sum up, the images show up rotated correctly in the file browser, but they aren't actually rotated when uploaded to the web.

What is this strange bug and what can I do to fix it?

---

### Post by iponeverything on 2010-04-19
> **russianbandit said:**
> I have some pictures that were taken vertically and they show up rotated correctly in nautilus and F-spot correctly. But when I go to upload an image to the web, the preview in the image upload dialog shows the pictures on their side, or horizontal. As a result the uploaded images ends up being horizontal and not vertical, like I want it too.

To sum up, the images show up rotated correctly in the file browser, but they aren't actually rotated when uploaded to the web.

What is this strange bug and what can I do to fix it?

It is not a bug. Nautilus is honouring the exif orientation data. I don't know if there is a setting in Nautilus to automatically have it do the physical transform. This is what I do to rotate images to match the exif data - first install "gthumb"

Then right click on the folder containing the images and choose open with gthumb, then go to "Edit -> Select All" Then go to "Tools -> Rotate Images" and check "Apply to all images" and "Apply physical transform" and then click "Apply" and it will apply the physical transform to the all the images in which the exif data does not match the physical orientation.

---

### Post by russianbandit on 2010-04-19
Thanks for the tip!

It seems not very "user friendly" to have to install another app just to upload an image rotated correctly. Any idea why nautilus chooses to display it one way, but upload another?

---

### Post by mcduck on 2010-04-19
> **russianbandit said:**
> Thanks for the tip!

It seems not very "user friendly" to have to install another app just to upload an image rotated correctly. Any idea why nautilus chooses to display it one way, but upload another?

Simple, Nautilus works correctly, while the web site where you are uploading the images lacks support for the EXIF data that tells that you were holding your camera sideways when you took the picture.

The problem is not in the uploading process, it's in the site where you upload the image.

To make this more clear, the image itself is exactly the same regardless of how you hold your camera. Some cameras include a sensor that tells the camera when you hold it sideways, and add that information to the image. Then, some programs are able to read that information, and as a result show you the image with correct orientation. The image itself is still the same, the actual data is still in the landscape orientation.

Now, your problem is that the web site where you upload your image isnt able to check the information about the orientation of your camera when you took the picture, so it simply displays the image as it is in the image file. The only way to solve that is to actually rotate the data in the image instead of just adding information that the image should be viewed sideways.

...and no, you don't need to install any app to rotate the image. gThumb is installed by default (that's what opens when you doubleclick an image to view it on your computer), as is Fspot, and both these programs are able to rotate the image for you.

---

### Post by russianbandit on 2010-04-19
> **mcduck said:**
> 
...and no, you don't need to install any app to rotate the image. gThumb is installed by default (that's what opens when you doubleclick an image to view it on your computer), as is Fspot, and both these programs are able to rotate the image for you.

The images/photos show up rotated up (as desired) by default in both nautilus and F-spot, so rotating them is not necessary. The thing is that before the actual upload, in the "upload" browser (which is part of Ubuntu I assume) the little thumbnails in the list show the image rotated properly, but the preview of the image on the right side, show the image on it's side (not desired). Thus, I suspect that it's more than the site reading the files incorrectly.

---

### Post by iponeverything on 2010-04-19
> **russianbandit said:**
> The images/photos show up rotated up (as desired) by default in both nautilus and F-spot, so rotating them is not necessary. The thing is that before the actual upload, in the "upload" browser (which is part of Ubuntu I assume) the little thumbnails in the list show the image rotated properly, but the preview of the image on the right side, show the image on it's side (not desired). Thus, I suspect that it's more than the site reading the files incorrectly.

It is not question of correctly or incorrectly. It is a question of meta-data and how it used. The preview window showing the image in its true orientation is not a bug, it is intended behaviour as it is quite useful to see the true orientation of the image that you are uploading. 

You seem to be a "seeing is believing" kind of person. My wife will often look at me sideways, when I tell her that the image that she is looking at is in fact sideways and not vertical as it appears.

"It seems not very "user friendly" to have to install another app just to upload an image rotated correctly."

You took the picture sideways. It is your picture, your data. It seem perfectly "user friendly" to have "your" data unmolested by applications trying to guess your true intentions and doing physical transformations  (ie. changing your data) without your consent or knowledge. If that is "user friendly" , I don't want it.

---

### Post by russianbandit on 2010-04-19
I only meant not user friendly in the way that F-spot displays the picture to me upright, without me rotating it in any direction. Nautilus also shows it up right, it's only natural for me to assume that when I upload the picture to the web, it will be upright, not sideways. Perhaps it would be clearer if both, F-spot and Nautilus, left the image sideways, then I could rotate the image and modify the meta-data.

Thanks for explaining how everything works.

---

### Post by iponeverything on 2010-04-19
> **russianbandit said:**
> I only meant not user friendly in the way that F-spot displays the picture to me upright, without me rotating it in any direction. Nautilus also shows it up right, it's only natural for me to assume that when I upload the picture to the web, it will be upright, not sideways. Perhaps it would be clearer if both, F-spot and Nautilus, left the image sideways, then I could rotate the image and modify the meta-data.

Thanks for explaining how everything works.

I personally agree with you in that applications should show images in their true orientation by default, as it is perfectly reasonable to assume WYSIWYG.

---

