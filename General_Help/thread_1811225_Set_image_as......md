---
title: "Set image as....."
date: 2011-07-24
forum: General Help
---

### Post by Aeighty on 2011-07-24
Ok let me start off by saying that i am fairly new to linux and have run into a issue setting a image as a desktop background when using a different OS other than Ubuntu or Mint. I recently installed Xubuntu ( really like the simple xfce desktop ) but when trying to set a image from a web page as a background i run into this problem. I can select the image and choose if i want to center, stretch etc... but after clicking set image as desktop nothing happens the background wont change ? i have noticed this when running other desktop environments such as KDE. I realize this is a small issue so any help will be appreciated thanks.

---

### Post by peter d on 2011-07-24
I have often had this problem. My solution has always been to download the image and set it as background from the folder. that seems to work better for me.

---

### Post by XubuRoxMySox on 2011-07-24
That's the best way! In your browser right-click the image and select **Save As...**, then download it to your pictures or Downloads or whatever...

Then use your file manager to move it to **usr/share/xfce4/backdrops** (you'll need root permission to add stuff to that folder) where wallpapers are stored.

I use the PCManFM file manager because if I forget to go as root to that folder, I can just click *Tools > Open Folder As Root* and bingo.

-Robin

---

### Post by Aeighty on 2011-07-24
Yeah that is what i have done to set the image as a background. It just seams funny that the right click option is there but doesn't work ? is this a hardware issue ? I think not because the problem happens on both my old Desktop and my newer Laptop ? going this route to set a image as a desktop background via right click menu never seems to be a issue when using Distro's based on the Gnome desktop environment. was really wondering if this is a issue with just the Desktop environments ?

---

### Post by Toz on 2011-07-24
Here's a workaround that will allow the Firefox "Set As Desktop Background" option to work in xfce.


1. With firefox, run the "Set As Desktop Background" option on one graphic image. This will create the file **~/.Firefox_wallpaper.png**.

2. Install the package **inotify-tools** using the Software Centre, or via terminal:```
sudo apt-get install inotify-tools
```

3. Create the following script:
```
mousepad ~/setasdesktopbackground
```with the following contents:
```
#!/bin/bash
while true; do
	while inotifywait -e modify ~/Firefox_wallpaper.png; do
		DISPLAY=:0.0 xfdesktop --reload
	done
done

```

4. Make that script executable
```
chmod +x ~/setasdesktopbackground
```

5. Open xfce's Desktop Settings and set the wallpaper to **Single Image**, select the file **~/Firefox_wallpaper.png**, and change the style to **Zoomed** (or whatever you prefer)

6. Execute the file in a terminal 
```
~/setasdesktopbackground
```and use firefox to change the wallpaper.

You can add the script **setasdesktopbackground** to your startup applications.

---

### Post by Aeighty on 2011-07-25
> **Toz said:**
> Here's a workaround that will allow the Firefox "Set As Desktop Background" option to work in xfce.


1. With firefox, run the "Set As Desktop Background" option on one graphic image. This will create the file **~/.Firefox_wallpaper.png**.

2. Install the package **inotify-tools** using the Software Centre, or via terminal:```
sudo apt-get install inotify-tools
```3. Create the following script:
```
mousepad ~/setasdesktopbackground
```with the following contents:
```
#!/bin/bash
while true; do
    while inotifywait -e modify ~/Firefox_wallpaper.png; do
        DISPLAY=:0.0 xfdesktop --reload
    done
done

```4. Make that script executable
```
chmod +x ~/setasdesktopbackground
```5. Open xfce's Desktop Settings and set the wallpaper to **Single Image**, select the file **~/Firefox_wallpaper.png**, and change the style to **Zoomed** (or whatever you prefer)

6. Execute the file in a terminal 
```
~/setasdesktopbackground
```and use firefox to change the wallpaper.

You can add the script **setasdesktopbackground** to your startup applications.
Thanks will give this a try. Still though is this a common issue among KDE XFCE and other desktop environments other than GNOME ??

---

### Post by Toz on 2011-07-25
I've never known the Firefox Set As Desktop Background functionality to work in XFCE. But in fairness to the XFCE developers, I don't think this is an XFCE issue. Firefox needs to be able to support other desktop environments. Otherwise, we end up using workarounds like this one.

---

