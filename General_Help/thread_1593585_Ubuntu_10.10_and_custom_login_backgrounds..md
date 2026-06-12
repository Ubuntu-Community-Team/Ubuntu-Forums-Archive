---
title: "Ubuntu 10.10 and custom login backgrounds."
date: 2010-10-11
forum: General Help
---

### Post by Sparx1337 on 2010-10-11
I'm somehow unable to use my custom backgrounds for the login screen. I'm not really fond of the login screen colors so I'm using a custom self-made one, but it doesn't look like Ubuntu can read the file (.jpg) when I copy it into /usr/share/background/. It can however read it in /Pictures/. Any idea what I might be doing wrong?

I followed the second method in this guide in order to set this up:

[http://nfolamp.wordpress.com/2010/05/18/change-the-login-screen-background-in-ubuntu-10-04/](http://nfolamp.wordpress.com/2010/05/18/change-the-login-screen-background-in-ubuntu-10-04/)

This guide worked flawlessly in Ubuntu 10.04. The root background folder is in the same folder as before so I don't understand where the problem would be, though I'm not still familiar with Ubuntu yet this is just to be expected.

Thanks for any help you might be able to provide, I appreciate it.

---

### Post by Sparx1337 on 2010-10-11
I need to bump this, sorry for the double post.

---

### Post by Sub101 on 2010-10-11
Ive also got this problem.

I set a custom login background with Ubuntu Tweak and I just get a purple background.

EDIT: Just converted the image to a PNG rather than a JPG and it works fine. Odd bug/feature.

---

### Post by Sparx1337 on 2010-10-11
I get the same issue when I use the second method above. The purple background happens when ubuntu cannot read the image. This is getting kind of annoying, I thought Ubuntu being Open Source would mean no restrictions were set to the operative system itself.

---

### Post by Sub101 on 2010-10-11
I just edited my previous post but will repost to ensure you see it.

It seems if you convert the image to a PNG it will work.

---

### Post by Sparx1337 on 2010-10-11
Confirmed, using PNG (and possibly other extensions) will work. JPEG-Layer images seem to have difficulties being read.

Thanks Sub101!

---

### Post by DJonsson2008 on 2010-11-28
the second method as described here worked for me

[http://nfolamp.wordpress.com/2010/05/18/change-the-login-screen-background-in-ubuntu-10-04/](http://nfolamp.wordpress.com/2010/05/18/change-the-login-screen-background-in-ubuntu-10-04/)

It's a bit confusing so I'll paste it here with some comments/corrections/caveats.

************** From nfolamp.
Step 1. (Optional)
Copy your favorite background .png file to /usr/share/backgrounds

AS MENTIONED BEFORE HERE USE *png *NOT* jpg 

I say optional to this step because if you 
look in /usr/share/backgrounds you may see 
background PNGs which are fine enough.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ sudo cp  my_cool_bg.png /usr/share/backgrounds
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

O.K. The above is easy enough to understand.

Step 2. 
Now you copy the command/script gnome-appearance-properties.desktop
to the /usr/share/gdm/autostart (which is a bit like the 
startup folder for MSWindows) but in this case effects
startup before the login screen.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For some odd reason the gnome-appearance-properties command/script won't work while logged in to the desktop if you try it from the command line.

So you need to - Logout of the desktop

Step 3.
When you Logout the Appearance Preferences GUI window pops up
allowing you to easily select any image in your 
/usr/share/backgrounds folder.

Step 4.
Now you need to log back in.
Delete the autostart folder gnome-appearance-properties item so it won't be there every time you login.

One way to do this is as the blogger said. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

That should do it.

BTW: (Other notes)

* Ubuntu-tweak on my Xubuntu box did not
  have any start up controls, although 
  provided lots of other neat switches.
     
* GDM2Setup setup utility as well had 
  no effect with my background login image
  and seems to not be fully compatible/maitained with/for  
  versions 10+

---

