---
title: "Ubuntu login screen on xubuntu?"
date: 2012-02-24
forum: General Help
---

### Post by Genocyber on 2012-02-24
I installed xubuntu on my laptop, cause it isnt so potent.
But the login screen that come with ubuntu are so more cool.

There is any way to replace that?

Thanks

---

### Post by HeroOfCanton on 2012-02-25
I actually prefer the simple XFCE look, but to each their own. :)

You can change the background image and a few other tweaks in the file /etc/lightdm/lightdm-gtk-greeter.conf

From what I've seen the same ubuntu greeter theme MIGHT make it in Xubuntu 12.04. Although 11.10 was also a might...

---

### Post by HeroOfCanton on 2012-02-25
Okay, I just realized that this is your first post and I'm probably talking gibberish. :D

First, you need a text editor. I prefer gedit which is not a default in xubuntu. To stick with what I know one extra step will be required.

First, install the text editor. From terminal:
```
sudo apt-get install gedit
```Next, we want to backup that config file just in case.
```

cd /etc/lightdm
sudo cp lightdm-gtk-greeter.conf lightdm-gtk-greeter.bak

```Once it's backed up we can edit it
```
sudo gedit lightdm-gtk-greeter.conf
```You can change the background, theme, etc. in this file. (Screenshot of my settings attached).

Save the file and reboot to see your new look.

For the rounded corners and slicker login look you'll just have to wait until the developers make that change, but you can at least tinker with a little customization this way.

---

### Post by Toz on 2012-02-25
Have a look at this post for instructions on how to install and use the unity-greeter in xubuntu: [http://ubuntuforums.org/showpost.php?p=11434924&postcount=4]("http://ubuntuforums.org/showpost.php?p=11434924&postcount=4")

---

### Post by Genocyber on 2012-02-25
Thank you both, I will try :)

---

### Post by HeroOfCanton on 2012-02-25
> **Toz said:**
> Have a look at this post for instructions on how to install and use the unity-greeter in xubuntu: [http://ubuntuforums.org/showpost.php?p=11434924&postcount=4](http://ubuntuforums.org/showpost.php?p=11434924&postcount=4)

Proven wrong and loving it :) Even though I liked the default style, since it could be done I just had to try it. Actually looks pretty sweet with a few tweaks. Thanks!

---

### Post by imachavel on 2012-02-25
is this an interface change or a back ground change? Text editor? I thought at first he was referring to for example ubuntu can use the gnome interface, the unity compiz plug in interface, or the kde interface. You need text editor to change the back ground? One painful thing about looking on the internet for how to change the background screen, is that it might lead you to ways to change background screen with a different interface, for example if you use kde, then it might give you the instructions to change the background in gnome or unity, even if you specify a search otherwise, as web sites aren't updated that much. I hate web design html tags (<body> <head> <p> </p>) also, but none the less updating a web site is usually as simple as uploading the files you want to upload with ftp transfer or if you can ssh it somehow, then there you go index.html is changed and you can view a brand new URL, if the file was edited properly and the dns server is hosted correctly with back end apache, etc. etc. etc. etc. etc. etc. etc.

Anyway back on track, here is how to change the desk top background wall paper:

[http://www.ehow.com/how_2323495_change-desktop-wallpaper-ubuntu.html](http://www.ehow.com/how_2323495_change-desktop-wallpaper-ubuntu.html)

and to change the interface google how to install a new interface through the terminal. It is simple once done, you log out, click the (wrench icon I believe?) then it will select the interface, and you can log back in. You figured it out anyway though?

---

### Post by brenttauro on 2012-11-02
Hey Toz, thank you for sharing the link. I was able to change the login screen. But I have one issue: there seems to be a grid of white dots that are spread across the login screen 1 cm apart from each other. I wish I could attach a screen capture but it's not possible when you're logging in. Is there any way to fix this?

---

### Post by Toz on 2012-11-02
> **brenttauro said:**
> Hey Toz, thank you for sharing the link. I was able to change the login screen. But I have one issue: there seems to be a grid of white dots that are spread across the login screen 1 cm apart from each other. I wish I could attach a screen capture but it's not possible when you're logging in. Is there any way to fix this?

Hello and welcome to the forums.

You can test out lightdm greeters by running the following command in a terminal window:
```
lightdm --test-mode
```
...this will also allow you to take screenshots of the greeter (to quit the preview, you need to press Ctrl+C in the terminal window).

To answer your question about removing the dots, do the following:
[LIST=1]
[*]Create the override file:
```
gksu leafpad /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override
```
[*]Enter the overrides:
Copy/paste the following into the new file:
```
[com.canonical.unity-greeter]
draw-grid = false
```
[*]Recompile the schema:
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
[*]Test:
```
lightdm --test-mode
```
[/LIST]

---

