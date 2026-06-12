---
title: "How to get netflix working with ubuntu?"
date: 2011-06-24
forum: General Help
---

### Post by trizrK on 2011-06-24
When i go to watch a show on netflix with ubuntu, i get a message saying netflix isn't compatible with my os. Is there any way to get around this?
thanks

---

### Post by doas777 on 2011-06-24
At present, there is no (good) way to get netflix going on linux. the problem is the silverlight DRM layer. MS will not license it to the moonlight project, so we cannot decode the data stream.

your best bet is to dualboot or run a virtualbox VM of XP or whatever windows OS, just for netflix. I know, it sucks, but for now, thats the skinny.

hopefully, soon we will be able to take advantage of the recent release of [Netflix for Android]("http://lifehacker.com/5804109/install-netflix-on-your-unsupported-android-device-no-rooting-required"). we shall see.

---

### Post by crispy_420 on 2011-06-24
Sorry but +1 not going to happen right now.

---

### Post by trizrK on 2011-06-24
thanks for the replies.
closed

---

### Post by inameiname on 2011-06-24
I ran across this article a little while back about Chrome adding a plugin that will allow Linux to use Netflix. I don't think its ready yet, but its another potential down the road.

[http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/](http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/)

---

### Post by trizrK on 2011-06-25
> **inameiname said:**
> I ran across this article a little while back about Chrome adding a plugin that will allow Linux to use Netflix. I don't think its ready yet, but its another potential down the road.

[http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/](http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/)
Lets hope so, it sucks using a virtual machine to play. It's glitchy and slow.

---

### Post by slooksterpsv on 2011-06-25
> **trizrK said:**
> Lets hope so, it sucks using virtual machine to play. It's glitchy and slow.

I can give you some optimization tips for XP:

You need to give it at least 1GB of RAM.
Turn off all effects.
Use Firefox or Google Chrome.
Make the page file a set number, not between 1504-3017 - 2048 is good, so max and min = 2048
Don't use 2D or 3D acceleration (if using VirtualBox)
If you can, only update to SP2, avoid SP3.
Don't install Antivirus programs (if you only use it for Netflix)
Make sure your CPU supports AMD-V or VT-X and you have it enabled before installing XP.
Allocate at least 24MB of Video RAM to the VM (if using VirtualBox).

I think that's about it =D.

---

### Post by trizrK on 2011-06-25
> **slooksterpsv said:**
> I can give you some optimization tips for XP:

You need to give it at least 1GB of RAM.
Turn off all effects.
Use Firefox or Google Chrome.
Make the page file a set number, not between 1504-3017 - 2048 is good, so max and min = 2048
Don't use 2D or 3D acceleration (if using VirtualBox)
If you can, only update to SP2, avoid SP3.
Don't install Antivirus programs (if you only use it for Netflix)
Make sure your CPU supports AMD-V or VT-X and you have it enabled before installing XP.
Allocate at least 24MB of Video RAM to the VM (if using VirtualBox).

I think that's about it =D.
Thanks for the tips. 
I can probally pull all that off except i installed XP from a CD that already had service pack 3 :(. Oh well again thanks

---

### Post by DuxWonder on 2011-06-25
If Netflix and Steam were both made to be Linux native, I would have seldom use for Windows.

---

### Post by slooksterpsv on 2011-06-25
> **trizrK said:**
> Thanks for the tips. 
I can probally pull all that off except i installed XP from a CD that already had service pack 3 :(. Oh well again thanks

No worries, I installed SP3 on my Netflix VM just because.. Actually come to think of it, I think you HAVE to have SP3 for Silverlight which is used for Netflix, I just know my VM slowed after installing SP3.

---

### Post by trizrK on 2011-06-25
> **DuxWonder said:**
> If Netflix and Steam were both made to be Linux native, I would have seldom use for Windows.
Yes one day hopefully... btw you can run Steam through wine or play on linux(you still have to have wine installed, playonlinux is based on it it believe) i'm running it as we speak.

---

