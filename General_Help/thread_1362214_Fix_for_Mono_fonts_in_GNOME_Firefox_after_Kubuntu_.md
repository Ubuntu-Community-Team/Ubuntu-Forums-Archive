---
title: "Fix for Mono fonts in GNOME Firefox after Kubuntu install"
date: 2009-12-22
forum: General Help
---

### Post by DukeBoxer on 2009-12-22
I know there has been quite a bit of discussion about this but I was wondering if there is a known fix yet other than taking out the fonts.conf file from /etc/fonts.  Here's the problem from the beginning

I installed from Synaptic the Kubuntu-Desktop meta package. After restarting, trying out the KDE desktop and then going back to GNOME the fonts in Firefox were all Mono, sort of like the font in the Terminal. I read and read everywhere and tried all the fixes, from the hinting to changing other files and the only thing that worked was taking out the fonts.conf file.

What I'm wondering is if there is a fix other than that, one that actually works by changing what caused the problem in the first place. In all my searches I couldn't find that fix.

-Josh

---

### Post by veko on 2010-01-17
I had the same problem: I tested Kubuntu, and when I switched back to Ubuntu, some fonts (eg. in Firefox) where messed up.

I got some advice from here:
[http://ubuntuforums.org/showthread.php?t=425579](http://ubuntuforums.org/showthread.php?t=425579)

Basically I replaced the contents of my $HOME/.fonts.conf by
```

<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

```Hope this helps you too.

---

### Post by Natty Dreed on 2010-08-01
> **veko said:**
> I had the same problem: I tested Kubuntu, and when I switched back to Ubuntu, some fonts (eg. in Firefox) where messed up.

I got some advice from here:
[http://ubuntuforums.org/showthread.php?t=425579](http://ubuntuforums.org/showthread.php?t=425579)

Basically I replaced the contents of my $HOME/.fonts.conf by
```

<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

```Hope this helps you too.


thanks veko ;)

this fixed my problem.

---

### Post by vmp on 2010-10-26
veko, thank you for the advice, it helped me solve the problem.

Here is what I did on my case:

On a fresh ubuntu installation on my laptop (with various KDE apps installed but not KDE itself) there is no $HOME/.fonts.conf file.

I run into this problem today on Maverick after I played a little bit with systemsettings. Any choice on fonts dialogue would never return the browsers (Firefox and Chrome!) fonts to the nice original state.

I deleted the $HOME/.fonts.conf file and everyting went back to normal.

I am not sure if the $HOME/.fonts.conf is needed at all. System settings creates it when adjusting anything with the fonts however the fonts used to look very nice before adjusting anything.

---

### Post by Rockroehre on 2010-10-27
Thanks vmp, worke for me, too! Deleting the .fonts.config file also made my Skype fonts look the way they used to. Still, the changes I had made to Kile's appearance (which had been the reason for installing systemsettings in the first place) seem to have been kept. I say "seem to" because I've restarted Kile, but I haven't rebooted my system so far.

---

### Post by mrcreativity on 2010-11-09
works brilliantly. thanks for this my friend.

---

### Post by Travikat on 2011-02-02
Thanks, i was bumbed also today after installing KDE4.  :frown:
Now my fonts are back \\:D/

---

### Post by Bhawani007 on 2011-02-20
Worked For Me Thank You

---

### Post by migel_wimtore on 2011-03-03
Sweet.

---

### Post by al2d2 on 2011-05-05
Thanks! Worked for me too.

For those who want to switch between GNOME and KDE desktops, creating the $HOME/.fonts.conf file as root solves the problem permenantly.


I encountered this workaround here:
[http://www.cyberciti.biz/faq/gnome-linux-firefox-smooth-fonts/#comment-50494](http://www.cyberciti.biz/faq/gnome-linux-firefox-smooth-fonts/#comment-50494)

---

