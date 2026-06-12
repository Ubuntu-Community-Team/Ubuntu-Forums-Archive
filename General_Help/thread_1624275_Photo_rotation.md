---
title: "Photo rotation"
date: 2010-11-17
forum: General Help
---

### Post by electroconvulsive on 2010-11-17
I have almost switched all of my computing tasks whilst traveling to Ubuntu. However there is just one thing that drives me insane and makes me boot into windows. When managing photos from my camera. After transferring them to the computer the rotation of the pictures in the folders has them rotated as they are on the camera, I.e it uses the exif rotation information used by the camera. Lets say for instance that I have a photo that I shot in portrait orientation. When transferred to my computer it displays it in nautilus correctly? rotated. Now lets say for instance I upload this photo to facebook it appears rotated on its side after upload or if I open the same photo under Windows it is displayed rotated in landscape orientation. Now lets say I use one of the Linux photo managers to rotate the photo correctly I have to rotate the photo into the opposite orientation and then back for it to be rotated properly. After doing this nautilus actually displays the photos rotated the wrong way.

So the question at hand is, can I get nautilus to behave in the same way as Windows or even Mac OSX when handling digital photos. i.e. can I get nautilus to ignore exif rotation information provided by the camera? IS this a bug in Nautilus that needs to be filed or is it something a little tweaking can fix?

And whoever who says that nautilus has it right has got to be joking!

Oh and one other thing. It seems that thumbnails take ages to load under Ubuntu so is there any way to speed this up. A folder with 150 or so photos can take up to a minute to load the thumbnails.

---

### Post by Frogs Hair on 2010-11-17
Have you tried using Shotwell photo manager ?

---

### Post by SeijiSensei on 2010-11-17
Or gwenview.  After rotation in the gwenview image viewer it asks if you want to save the altered file.

---

### Post by electroconvulsive on 2010-11-17
Thanks for your replies guys. I have tried many different photo management apps however my question is basically how to get nautilus to ignore exif rotation information the same way that w$ and O$X do. All photo management apps act about the same and the problem is with nautilus. Having nautilus fixed will be what I want. I do appreciate your suggestions though. Ive already been through the configuration editor and there is no setting there for it so I am hoping to get someone in the know with nautilus configuration to help me.

---

### Post by tgm4883 on 2010-11-17
> **electroconvulsive said:**
>  IS this a bug in Nautilus that needs to be filed or is it something a little tweaking can fix?

And whoever who says that nautilus has it right has got to be joking!

Why would you say that nautilus has it wrong? If I want to view a photo, why would I want to view it sideways?

---

### Post by electroconvulsive on 2010-11-18
> **tgm4883 said:**
> Why would you say that nautilus has it wrong? If I want to view a photo, why would I want to view it sideways?

Please read my original post more carefully. If you look at the postyou will realise that there is actually a problem with how nautilus handles digital photos. Funny that I had to state fact that W$ gets it right. Maybe yopu should do a little experiment with your digital camera and come up with the same result. I would really just like to know how to get nautilus to act the same as the other file browsers.

---

### Post by tgm4883 on 2010-11-18
> **electroconvulsive said:**
> Please read my original post more carefully. If you look at the postyou will realise that there is actually a problem with how nautilus handles digital photos. Funny that I had to state fact that W$ gets it right. Maybe yopu should do a little experiment with your digital camera and come up with the same result. I would really just lioke to know how to get nautilus to act the same regardless of whether you think it is the right way or not.

Ok, so I've now read your post 4 times (twice the first day and twice now), and I'm still not sure why you think the TOP of a photo should ever be on any other side than the TOP. Seems to me that Windows/Facebook should read the exif data in the image. Sounds more like a bug on those platforms.

Perhaps I'm just not understanding what the heck you are talking about. I certainly don't understand this statement.

> Now lets say I use one of the Linux photo managers to rotate the photo correctly I have to rotate the photo into the opposite orientation and then back for it to be rotated properly. After doing this nautilus actually displays the photos rotated the wrong way.

That sounds like you are changing the orientation of the image without changing the exif data. If that is the case, how can you expect nautilus to be correct at all? It relies on the exif data (as it should).

---

### Post by yetiman64 on 2010-11-18
The package nautilus-image-converter when installed allows for easy rotation of an image. Any picture not how you want it can easily be right clicked and the "rotate images" option used.

This package installs imagemagick to do the work of rotating or resizing and puts two entries in the nautilus menus for easy access.

Edit: On rereading just realized the question is more than just what to use, sorry OP.

---

### Post by electroconvulsive on 2010-11-20
> **tgm4883 said:**
> Ok, so I've now read your post 4 times (twice the first day and twice now), and I'm still not sure why you think the TOP of a photo should ever be on any other side than the TOP. Seems to me that Windows/Facebook should read the exif data in the image. Sounds more like a bug on those platforms.

Perhaps I'm just not understanding what the heck you are talking about. I certainly don't understand this statement.



That sounds like you are changing the orientation of the image without changing the exif data. If that is the case, how can you expect nautilus to be correct at all? It relies on the exif data (as it should).

Thanks for your well thought out reply. After being an ubuntu user for 4 years I am stumped as to why as a member and possibly a moderator at these forums you would 

1. Refuse to experiment using the example I have given you so you can understand what I am talking about. (Admitedly it is hard to explain however if you try it yourself you will see exactly what I mean) 

2. Suggest that Mac OSX, Windows and Facebook have a problem and Nautilus does not. (I understand that the nautilus configurartion is probably correct however not convenient if you catch my drift especially if you use other platforms as well as linux)

But anyway, I have a technical question and as a member of these forums as long as I have been. My expectation is for technical help. I made the mistake of adding my opinion so I have been given opinion in return so let me rephrase this for you. 

Regardless of my or your opinion on the situation I would like to have nautilus set up so it behaves the same as OSX or Windows when handling digital photos. It is not a matter of opinion, it is actually a matter of preference. So if you are an expert at this maybe you can give me some technical assistance in helping me configure nautilus to behave how I as a user would like it to behave.

---

### Post by electroconvulsive on 2012-10-04
I am marking this solved because it was solved by developers in 12.04.

To those who sorted this out I give a big thanks.

---

