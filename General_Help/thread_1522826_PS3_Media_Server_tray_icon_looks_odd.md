---
title: "PS3 Media Server tray icon looks odd"
date: 2010-07-02
forum: General Help
---

### Post by Martin_sensei on 2010-07-02
Hello!

I have done a fair bit of Googling first but with no success...

I am using PS3Media server to stream audio, video etc to my PlayStation.  It works very well indeed on the PS3 end, but I have a slight annoyance that is messing with the nice look and feel of my Ubuntu desktop:  The PS3 Media Server icon seems to have a grey background, whereas my panels all have dark transparency, this makes it stand out a mile.

Is there any way of altering this icon?  I was looking in the ..../pms-linux-1.10.5 folder but couldn't find much there.

Any ideas?

Many thanks!

---

### Post by rwthelegend on 2010-07-07
PS3 Media Server is a Java application and it's won't do transparent tray icons in Gnome (or Linux all together, I don't know).

But there is a trick to make it integrate.

**1. Extract the jar file**

Inside your PS3 Media Server folder, there is a file called "pms.jar". You can right-click it and simply extract it to view it's content. Be sure to first copy that file so you can restore it later should something go wrong.

I extracted pms.jar to the desktop and I got a folder called pms.

Inside that folder, there is a folder called "resources" and in that folder there is a "images" folder.

That is where the icons are located.

[[IMG]http://img686.imageshack.us/img686/6952/screenshotimagesfilebro.png[/IMG]]("http://img686.imageshack.us/i/screenshotimagesfilebro.png/")

*(I already changed the images in the screenshot, you will see the normal green ones with the white background)*

**2. Change the original icons**

It's pretty simple actually, pick the icon you want and the background behind the icon should be the same gradient/color as your gnome-panel.

I'm using the Shiki Brave Gtk2.0+  theme, so the background image for the panel is located in /home/username/.themes/ ShikiBrave/gtk-2.0/Panels

There are 5 icons in the in the "images" with that icon, so I changed them all (make sure you don't change the filenames).

The files you are looking for are the ones called "Play1Hot_16" "Play1Hot_32" ... all the way to the two 256 ones.

*(however I do believe you only need to change the 120.jpg one, not sure, I just did them all)*

[[IMG]http://img694.imageshack.us/img694/5627/screenshotplay1hot256jp.png[/IMG]]("http://img694.imageshack.us/i/screenshotplay1hot256jp.png/")


**3. Create a jar archive**

Do not just create an archive from the folder on your desktop, you need to select all the files inside that folder and create an archive from those.

I got permission errors when trying to do it with file roller, so I had to do it from the terminal.

In the terminal:

```
cd /home/username/Desktop/pms
```*(this will navigate to the pms folder we got when we extracted the original pms.jar file, "username" should be the name you log in with)*

```
sudo zip -r pms.jar *
```*(with root permission (sudo), this will take all the files (*) and create an archive called pms.jar)*

```
chmod 777 pms.jar
```(this will make sure the file has the correct privilages)

Then all that  is left is to copy the pms.jar file inside the pms folder on your desktop to the folder where your media server is.

**4. Result**
[[IMG]http://img189.imageshack.us/img189/8851/screenshot1gt.png[/IMG]]("http://img189.imageshack.us/i/screenshot1gt.png/")

*(I just did this quick, the background on the icon doesn't match the panel background exactly, just work your gimp magic and some trial and error and it will look perfect, I just didn't bother)*

*I wonder how many blogs/sites will rip this post, lol.*

---

### Post by Martin_sensei on 2010-07-14
OK, great, thats the image file I was looking for.

I will give this a go!

So, there is no way to have a transparent background?

---

