---
title: "Firefox graphics bug found and replicated"
date: 2012-01-22
forum: General Help
---

### Post by DMustaine on 2012-01-22
I have a problem with some pictures posted to imgur and I can replicate it every time. I don't know the best place to post this, and am looking for direction to properly report this issue.

I have 2 that I can show, and have had several others I can't find those links though.

Each time I have verified the image linked to was taken from an iPhone.

I am running 11.10, all current updates in place, and using version current recommended NVIDIA driver for my system. I have a Dell vostro 1510 laptop with Intel® Core™2 Duo CPU T5870 @ 2.00GHz × 2. I run a dual-boot system with Windows 7 Professional 32 bit as the secondary.

I can open these links in Windows, but each time I open them in Ubuntu I crash my entire system. the screen is still active in a sense, but completely pixelated, unusable, and I have only 1 option, hard reboot. Here is a picture from my Droid of what happens to the screen if I try and open the pictures below:
[IMG]http://i195.photobucket.com/albums/z125/JB73Mustaine/error.jpg[/IMG]


I will gladly share system specifications, I just don't know what is needed.

WARNING, both of these links completely crash my system. I have verified they are not malicious, they are simply photos taken from an iPhone with the 3D option enabled.

Here is link 1:
[http://i.imgur.com/GC7sR.jpg](http://i.imgur.com/GC7sR.jpg)
Here is link 2:
[http://i.imgur.com/BxzRt.jpg](http://i.imgur.com/BxzRt.jpg)

---

### Post by conradin on 2012-01-22
what version of firefox are you running? Current version is firefox 9.

---

### Post by DMustaine on 2012-01-23
9.0.1

Per updates I don't have any available as I am posting this.

Also, this has been for almost 6 months, I just got fed up enough to post about it.

---

### Post by lovinglinux on 2012-01-24
Type **about:config** in the address bar, then type **webgl.disabled** then double click the resulting preference in the list to make it bold/true.

Test the same web sites to see if it crashes. Restore the previous setting  if it doesn't help.

---

### Post by DMustaine on 2012-01-29
> **lovinglinux said:**
> Type **about:config** in the address bar, then type **webgl.disabled** then double click the resulting preference in the list to make it bold/true.

Test the same web sites to see if it crashes. Restore the previous setting  if it doesn't help.
That stopped the permanent screen flicker, but still froze the entire system and had to hard boot. Before I could still move the cursor around and click things I just couldn't see what I was doing. This time just a pure freeze.

Thank you for the suggestion though.

---

### Post by lovinglinux on 2012-01-30
> **DMustaine said:**
> That stopped the permanent screen flicker, but still froze the entire system and had to hard boot. Before I could still move the cursor around and click things I just couldn't see what I was doing. This time just a pure freeze.

Thank you for the suggestion though.

You probably have a webgl incompatibility that is making your video driver freeze.

---

