---
title: "Installing flash on 10.10 (noobie)"
date: 2011-03-12
forum: General Help
---

### Post by Azaz on 2011-03-12
Hello, I'm an Ubuntu noobie and I have popcorn. :popcorn:
I thing I installed Flash player properly with umm... mubuntu is it? Its the thing that lets you enter a command in the shell and it auto installs. (I'm a noobie remember) When I go to youtube the video starts playing for about half a second then stops. I cant click on any of the video stuff like pause or the volume. Id say that what I did did not work and I was wondering if someone could tell me the proper way to install flash player, I tried downloading it off the webpage but I dont know where to put the file when I download it.

---

### Post by securitymeddler on 2011-03-12
Hey dude, 

Brand new myself. But I got it to work. With the default Firefox install you just goto youtube.com or wherever and it will ask you to install. But I too had that fail. 

What you can do is goto this site, 
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

...then select the flash player version that ends in .deb . that means it's an install file for "debian" which is what Ubuntu is based on. From there it's just a next next next MacOS style install. 

Of course I am using the 32bit version since the 64 bit version is has not worked for anyone I personally know. But people claim it does. 

Let me know how it works out for you?

---

### Post by or3x on 2011-03-12
Open a terminal (Applications -> Accessories -> Terminal) and paste the following code:
```
sudo apt-get install ubuntu-restricted-extras
```Hit enter and then your password when it asks you for it. 
You'll probably have to restart firefox and then flash should work.
(This will also let you play mp3:s and dvd:s)

---

### Post by Azaz on 2011-03-12
> **or3x said:**
> Open a terminal (Applications -> Accessories -> Terminal) and paste the following code:
```
sudo apt-get install ubuntu-restricted-extras
```Hit enter and then your password when it asks you for it. 
You'll probably have to restart firefox and then flash should work.
(This will also let you play mp3:s and dvd:s)

I did that already, did not work. thanks for trying though :)

---

### Post by Azaz on 2011-03-12
> **securitymeddler said:**
> Hey dude, 

Brand new myself. But I got it to work. With the default Firefox install you just goto youtube.com or wherever and it will ask you to install. But I too had that fail. 

What you can do is goto this site, 
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

...then select the flash player version that ends in .deb . that means it's an install file for "debian" which is what Ubuntu is based on. From there it's just a next next next MacOS style install. 

Of course I am using the 32bit version since the 64 bit version is has not worked for anyone I personally know. But people claim it does. 

Let me know how it works out for you?

Fixed. Thanks :)

---

