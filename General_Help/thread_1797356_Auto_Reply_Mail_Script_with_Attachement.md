---
title: "Auto Reply Mail Script with Attachement"
date: 2011-07-04
forum: General Help
---

### Post by japzone on 2011-07-04
Ok here's my situation. I have a Feature Phone with no Data plan but unlimited Text/Picture Messages. I want to be able to get the latest Radar on my Phone and the only way to do it would be to recieve it via a Picture message. I've already found a source for my Radar images and have already sent a Test email to my Phone proving that it works and the Images are viewable on my Phone. My problem is the Automatic sending.

What I want to do is whenever I send an Email from my Phone to my PC,  I want my PC to reply with the Radar image attached. Even better is if I could put a Keyword in the Email that would cause a Different image file to be sent from my PC (ie: Radar images of different areas).  I already found a way to have my PC Download the latest Radar every 5 minutes using this simple method:
```
watch -n 300 -x wget -O oc-radar.gif "http://radblast.wunderground.com/cgi-bin/radar/WUNIDS_composite?centerlat=38.38782120&centerlon=-75.10727692&radius=120&type=N0R&frame=0&num=5&delay=15&width=230&height=230&newmaps=1&r=1309818629"
```
This Method Works but if you can help me find a way to tie the **wget** command into the Script so it downloads the image after it recieves the email that'd be a better option then having the **waiting** command constantly running in the background.

I am very rusty with my shell language, so you can put me somewhere slightly above novice. I don't need everything spelled out for me but I do need some good assistance. I'm a bit of a visual learner and like to reverse engineer example code (I don't know why but I learn better that way). 

So any help here will be appreciated :)

---

