---
title: "Login Wallpaper does not changes"
date: 2012-04-26
forum: General Help
---

### Post by xedi on 2012-04-26
I read that Ubuntu 12.04 now changes your login wallpaper depending on what background you set up when logged in. This works for me, however, only with the default wallpapers.

Is it only supposed to work with the default wallpapers, or am I too stupid to setup my own wallpaper (it appears ok when logged in, but the login wallpaper is the standard purple Ubuntu background)  or is that maybe a bug?

Thanks for your replies in advance.

---

### Post by arturusch on 2012-04-26
I think you need to have the wallpapers set in the default wallpaper directory.
Those wallpapers I have in home/me/.wallpapers are not taken in consideration when changing to them.

---

### Post by xedi on 2012-04-26
Is there anyway to get your own wallpapers into the default wallpaper directory? (usr/share/backgrounds)

I could copy my wallpaper there using sudo but I can neither open the picture from that folder nor can I select it from the appearance menu, nothing happens when I select it from that source.

---

### Post by hermestrs on 2012-04-27
Ok I figured it out. If you did upgrade to 12.04, you have to remove all the pictures from the pictures gui in the set background interface, then put them back in. My guess is its copying the pictures to some other place and they then set the permissions right. when it upgrades it does not set those permissions. That is just a guess I am by no means a linux guru.

---

### Post by Stump86 on 2012-04-27
What worked for me was to first add my wallpaper to /usr/share/backgrounds. Then I added the wallpaper to the list in "Appearance" (right click on desktop > Change desktop background) by clicking on the plus button and navigating to the wallpaper I added in /usr/share/backgrounds.  The permissions for the file need to be readable by all.

---

### Post by xedi on 2012-04-28
> **hermestrs said:**
> Ok I figured it out. If you did upgrade to 12.04, you have to remove all the pictures from the pictures gui in the set background interface, then put them back in. My guess is its copying the pictures to some other place and they then set the permissions right. when it upgrades it does not set those permissions. That is just a guess I am by no means a linux guru.

I'm not sure what you mean. What picture gui?

> What worked for me was to first add my wallpaper to /usr/share/backgrounds. Then I added the wallpaper to the list in "Appearance" (right click on desktop > Change desktop background) by clicking on the plus button and navigating to the wallpaper I added in /usr/share/backgrounds. The permissions for the file need to be readable by all.


I did the first step, but I cannot add the background, nothing happens when I select the picture and click on add. The file window thingy closes but the background does not change and it does not appear in the selection.

Also, when trying to open it in Nautilus, I get an error saying "Could not load image '2560x1600.jpg'." and "Failed to open input stream for file", even though the original is fine.

So my guess is my permissions are wrong. How do I set it to be readable by all?

---

### Post by coldjeanz on 2012-04-28
Same problem. I expected this would work automatically.

---

### Post by JRV on 2012-04-28
> **arturusch said:**
> I think you need to have the wallpapers set in the default wallpaper directory.
Those wallpapers I have in home/me/.wallpapers are not taken in consideration when changing to them.

I suspect it is not looking in hidden directories. It finds mine ~/Pictures/wallpaper with no problems.

If you did an upgrade from 11.10 it will not find your wallpaper and display the standard one.  You need to change it, then change it back to the one you want.

---

### Post by xedi on 2012-04-28
I got it to work!

As Stump86 said, the permissions need to be set so it can be read by everybody, which was problematic because I did not have the rights to do so. Since I did not know the terminal commands, I ran 

```
sudo nautilus
```

and thus had root access and could then change the permissions from the properties context menu to read-only by the other users.

Thanks for the help!

---

