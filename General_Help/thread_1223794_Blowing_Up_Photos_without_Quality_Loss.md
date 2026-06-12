---
title: "Blowing Up Photos without Quality Loss"
date: 2009-07-26
forum: General Help
---

### Post by ki4jgt on 2009-07-26
Need a program to blow up an image without losing the quality of the image, Anyone with ideas, please and thank you!

---

### Post by lukjad on 2009-07-26
ki4jgt, when you blow up a picture, you are stretching it out, taking the amount of detail that is supposed to be put over 1" over say 3". That means the detail will go down. It may not be visible if you have a high depth image, but it still will have less and less detail.

---

### Post by merlinus on 2009-07-26
RAW and tiff can be enlarged to a far greater degree than jpeg, which will start to show dithering and pixelating with only a small increase in size.

The higher the dpi of the original, the more it can be enlarged without too much apparent corruption, but only up to a point where it becomes all-too-obvious.

That is why I shoot both RAW lossless compressed and jpeg large fine with my dSLR.

---

### Post by zarqoon on 2009-07-26
If you make a digital image bigger there will always be some quality loss. There is just not enough information to fill the additional pixels exactly.
There are some algorithms that guess color values and therefore make the image bigger but if you size a 640x480 image 1280x1024 it will look like crap regardless of the application used to do it.
In general you can use the gimp for almost all your image editing needs.
It is available through the repositories if you do not already have it installed.

---

### Post by MickS on 2009-07-26
There is a little trick which works sort of, instead of blowing the picture up say200% in one go, blow it up in many smaller stages till you get the size you want, worth trying, I have had the best results with landscapes.


Mick

---

### Post by zarqoon on 2009-07-26
The only thing that should accomplish is to blur the picture. While this makes the resizing artifacts smaller resizing it in one go and then applying a blur filter should produce a better final picture.

---

### Post by ki4jgt on 2009-07-28
The reason I ask is, I've found several windows programs online which claim to do this. They sell for around $100 and my sister was wanting to use them. I don't have a windows machine, so I'm out of luck.

---

### Post by XCan on 2009-07-28
You can only do this with excellent results if your images are in vector format, which they are not if you are talking about digital photos from a normal digital camera.

The Windows apps you see are scams, out of question. You want to upsample, which means you are to sample all pixels, spread them out and make a qualified guess of what can be between the pixels. Usually, the guess would involve that the data between the pixels is smooth with low frequency (otherwise your upsampled image will be crap due to noise). This means that you are throwing your upsampled image into a low-pass filter, which cuts off your frequencies at ~1/upsample_scale, and your upsampled image will never be lossless.

---

