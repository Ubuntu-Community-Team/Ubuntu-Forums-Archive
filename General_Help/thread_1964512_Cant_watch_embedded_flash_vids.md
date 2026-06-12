---
title: "Cant watch embedded flash vids"
date: 2012-04-24
forum: General Help
---

### Post by tygsxr on 2012-04-24
Hi can someone please help me, did some updates on 10.04 and since then i havent been able to watch embedded vids on sites like break.com or metatube. The weird thing about it is that i can watch youtube vids. The other sites when i try to watch them all i get is a black square where the player should be.. i tried flash aid but its no go. I think that mozilla is having trouble loading the player.. Thanks  Ps i am now running mozilla 11.0

---

### Post by isalovell on 2012-04-24
Have you installed all addons?

---

### Post by tygsxr on 2012-04-24
Hi, under Extensions i have Ubuntu Firefox modification 0.9.4, Flash Aid 2.2.3. Under plugins i have Adobe reader 9.4, DivX webplayer 1.4.0.223, Quick time plugin 7.6.6, Shockwave flash 11.2.ror2, VLC multimedia plugin (compatible Totem 2.32.0), Windows media player plugin 10 (compatible Totem)..  Cheers

---

### Post by zdeuyo on 2012-04-24
Hello,

Try to install all updates in the update manager and see if this fixes your issue.

---

### Post by ph4nt0m117 on 2012-04-24
Chromium Chrome or Opera

Different browser.  Just sayin.

---

### Post by zdeuyo on 2012-04-24
> **ph4nt0m117 said:**
> Chromium Chrome or Opera

Different browser.  Just sayin.

This is correct.

There are many browsers,

1. Google Chrome
2. Chromium
3. Opera
4. Firefox
5. etc.

---

### Post by tygsxr on 2012-04-24
Hi, I think it was the updates that gave me the issue. Ill give another browser a try. Hopefully if one of these work it will cancel out the operating system as the problem and it will just be firefox the issue. Keep ya posted Cheers.

---

### Post by techsupport on 2012-04-24
> **tygsxr said:**
> Hi, I think it was the updates that gave me the issue. Ill give another browser a try. Hopefully if one of these work it will cancel out the operating system as the problem and it will just be firefox the issue. Keep ya posted Cheers.

I've had this happen.

Install bleachbit in terminal:

```
sudo apt-get install bleachbit

sudo bleachbit
```Yeah, I know you are supposed to use gksu but it doesn't really matter when you are using bleachbit at all. Don't delete your passwords accidentally. And don't select memory, free disc space, or localizations or it takes forever. Just leave those unchecked and hit delete. You should be good to go.

---

### Post by tygsxr on 2012-04-24
Hi i tried Opera and it still is doing the same thing. I got an error message where the video should be saying that i dont have the relevant Adobe flash player. So i checked the player i am running and it is the most up-to-date version(that being Player 11).. It seems that it is struggling with the Shockwave-Flash plugin. I only say this because thats what you use when trying to watch these vids.. I checked the version of this plugin and i have the most recent version as well.. I will try bleachbit now.. Fingers crossed.. Cheers

---

### Post by techsupport on 2012-04-24
> **tygsxr said:**
> Hi i tried Opera and it still is doing the same thing. I got an error message where the video should be saying that i dont have the relevant Adobe flash player. So i checked the player i am running and it is the most up-to-date version(that being Player 11).. It seems that it is struggling with the Shockwave-Flash plugin. I only say this because thats what you use when trying to watch these vids.. I checked the version of this plugin and i have the most recent version as well.. I will try bleachbit now.. Fingers crossed.. Cheers

I'm guessing that your problem might be your caches. They can get huge with the types of media files that are on the Internet these days. Usually when the flash starts to get bogged down and it isn't running right anymore, I do a bleachbit from the command line (sudo bleachbit) and my flash playback issues are gone. 

:guitar:

---

### Post by lovinglinux on 2012-04-26
See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

Clearing the cache and cookies is a good start tho.

---

### Post by tygsxr on 2012-04-28
Hi I tried bleachbit and nothing has changed. It seems to be the operating system thats having the problem. Any other suggestions. Cheers

---

### Post by tygsxr on 2012-04-28
Hi, i have temporarily fixed the problem by reverting back to Flashplayer 11.1r102.63. I had to do it through Flash aid all be it the playback is a little jerky( could be my pc or connection). I found this fix through this post [http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=5](http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=5). Thanks for everyones suggestions while trying to solve this problem. I am still not contented with the answer. I cant see why the newest flash plugin(11.2.r202) wont work. Cheers

---

### Post by lovinglinux on 2012-04-28
> **tygsxr said:**
> Hi, i have temporarily fixed the problem by reverting back to Flashplayer 11.1r102.63. I had to do it through Flash aid all be it the playback is a little jerky( could be my pc or connection). I found this fix through this post [http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=5](http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=5). Thanks for everyones suggestions while trying to solve this problem. I am still not contented with the answer. I cant see why the newest flash plugin(11.2.r202) wont work. Cheers

Look 2 posts above yours ;-)

---

