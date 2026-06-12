---
title: "Ubuntu Screen Issues"
date: 2009-12-04
forum: General Help
---

### Post by SkintAndMinted on 2009-12-04
Hi guys, new to the forum and very unexperienced with Ubuntu. Ive tried installing Ubuntu to my mums laptop because she got a virus and we couldnt find the copy of Windows XP. I told her if she just uses it for the internet she might aswell get a free OS instead of shelling out for Windows. So I get a Ubuntu CD off my mate and install it on the laptop, formatting the HDD so its the only OS on the laptop. But now its installed the screen is all wierd and grainy, with the colours all distorted. If it helps i'll post a picture. I didnt have this problem with Windows though. Can anyone offer any help and advise?

Thanks in advance everyone :KS

---

### Post by Ichido on 2009-12-04
Which Version of Ubuntu did you install?

You say ...
"the screen is all wierd and grainy, with the colours all distorted."

What is showing on the 'Screen', the Ubuntu-Desktop?

Can you see the top Menus "Applications", "Places" & "System"?

In the Menu "System", under "Preferences" you should find "Display".

Can you try different settings in the "Display" Window?

Can you try running Ubuntu from the CD and check the Display Settings from there?

---

### Post by coffeecat on 2009-12-04
> **SkintAndMinted said:**
> If it helps i'll post a picture.

Good idea! Please do. :wink:

Also, post the make and model of the laptop, plus any specifications you can find. Most relevant is the graphics card - again, make and model.

---

### Post by earfer on 2009-12-04
is it when you login and then the loading screen (splash) picture is distorted?

i have that problem...is it that one?

---

### Post by SkintAndMinted on 2009-12-04
By grainy i mean that it looks like the graphics card is struggling, thats what i first thought but surely Ubuntu is less graphically needy that Windows? Heres a photo i took with my phone, its not great but as you can see, there are red lines across the screen. These red lines are all across the screen, its a bit like static on a television except colourful and over the desktop. The 'graininess' starts as soon as Ubuntu starts. 

[http://i49.tinypic.com/2sb4dh2.jpg](http://i49.tinypic.com/2sb4dh2.jpg)

---

### Post by Ichido on 2009-12-04
Can you see the top Menus "Applications", "Places" & "System"?

In the Menu "System", under "Preferences" you should find "Display".

Can you try different settings in the "Display" Window?

Can you try running Ubuntu from the CD and check the Display Settings from there?

---

### Post by SkintAndMinted on 2009-12-04
Yeah everything that is suppose to be there is there, its just that it all looks rubbish and grainy. And its the same when i run Ubuntu straight from the CD on the laptop, but when I run it on my PC it runs fine with no visual bitch-ups. Also, it seems that the colours are all inverted :\

---

### Post by Ichido on 2009-12-04
Post your Laptop's Make & Model and Information on your Video Card, Please.
Also, which version are you running?

---

### Post by SkintAndMinted on 2009-12-05
Its a Acer Aspire 5000, how do i get the information on my video card? 
Im running the latest Ubuntu (9.1?)

---

### Post by Ichido on 2009-12-16
Try the following:

In a Terminal;  "sudo dmidecode -q" (but don't type the quotes).


Look in the following file:  /var/log/Xorg.0.log

Also, check this link: [http://ubuntuforums.org/archive/index.php/t-1053142.html](http://ubuntuforums.org/archive/index.php/t-1053142.html)

---

### Post by DaVince21 on 2009-12-16
Grainy screen? I have that on some resolutions - my monitor starts showing weird noise through everything. My first suggestion would be to try and change the screen resolution.

---

### Post by ean5533 on 2009-12-16
Like DaVince said, try changing screen resolution to something lower, just as a test. You can find this setting in the preferences menu, called "Display".

Also, I can't remember if that control panel has the option to change the refresh rate, but if it does then you might want to try lowering the refresh rate a bit. Sometimes laptop displays aren't capable of handling normal refresh rates and turn grainy as a result.

---

