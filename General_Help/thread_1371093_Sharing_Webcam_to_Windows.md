---
title: "Sharing Webcam to Windows"
date: 2010-01-03
forum: General Help
---

### Post by fjrichman on 2010-01-03
I have a netbook with an intergrated webcam running Ubuntu Karmic 9.10 
I'm looking for a way to share the camera to a windows desktop computer to use the webcam as if I had plugged in a USB webcam. I want to do this because Windows has some really great software for Webcams but runs horribly on the netbook. Anyone have ideas for this?

---

### Post by fjrichman on 2010-01-03
Bump

---

### Post by loell on 2010-01-03
It's possible but I reckon you have to go through a nasty setup.

in windows, you need to setup a virtual webcam software (I honestly don't know if there are free ones).


while in linux you need to setup a webcam server that your windows can have access.

---

### Post by kh1116 on 2010-01-03
off topic, but just out of curiosity, what brand of netbook do you have?

---

### Post by fjrichman on 2010-01-03
Acer Aspire One

You have some sort of guide or starting point I could look at. I'm trying to avoid an FTP server because I want it to be a live feed.

---

### Post by fjrichman on 2010-01-03
Bump

---

### Post by fjrichman on 2010-01-03
Bump

---

### Post by loell on 2010-01-03
there are no existing tutorials on this field, as this is actually a rare setup. one really needs to put the pieces together.

but the basic theory should work, that is, feed the images from ubuntu's webcam server to a windows machine and identify it as webcam, like a virtual webcam device.

you may use the **webcam-server** or better yet **VLC** and set it up like this [http://blog.signalnine.net/?p=4]("http://blog.signalnine.net/?p=4")

and on windows, just point the virtual webcam software to get the images from ubuntu's webcam server.

---

