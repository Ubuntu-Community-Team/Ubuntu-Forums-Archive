---
title: "X environment doesn't start after upgrade to 9.10"
date: 2009-11-01
forum: General Help
---

### Post by NeoAndersen on 2009-11-01
X environment doesn't start after upgrade to 9.10
I had this problem 6 months ago and I could solve it installing Kubuntu over Ubuntu Studio that was over Ubuntu... : )
I did it using aptitude...
but now when I try it the output is "read only...",
"unable to mount: Device or resource busy...", 
"could not resolve 'br.archive.ubuntu.com'..." etc

I had tried "dpkg -reconfiguge xserver-xorg" but it didn't work...
I would like to uninstall all other enviroments (kubuntu, studio, and even sugar - I never asked to install it... I don't know how it appeared here...)
and let just a clean Ubuntu with gnome...
I would like you to tell me the commands to do so... But first I need help to resolve this "unable to mount: Device or resource busy..."
or I will not be able to install, reinstall or uninstall nothing...

---

### Post by NeoAndersen on 2009-11-02
Thats what it shows:
[http://www.flickr.com/photos/garotobossanova/4065772958/sizes/l/](http://www.flickr.com/photos/garotobossanova/4065772958/sizes/l/)

---

### Post by NeoAndersen on 2009-11-02
Someone from IRC #kubuntu told me that this information would help to find the solution:
# lspci | grep VGA
01:00.0 VGA Compatible Controler: 
nVidia Corporation G71 [GeForce 7950 GT] (reva1)

---

### Post by xtremesupremacy3 on 2009-11-02
Okay, so it has found your graphics card.

It may be a long shot here, but are you able to login to graphical mode using ```
startx
```?

---

### Post by NeoAndersen on 2009-11-02
Well, before I go there to try this startx I will post what I have tried without success:
Output to fsck /dev/sd*:
[http://www.flickr.com/photos/garotobossanova/4069216589/sizes/l/]("http://www.flickr.com/photos/garotobossanova/4069216589/sizes/l/")

Output to sudo /etc/init.d/gdm stop:
[http://www.flickr.com/photos/garotobossanova/4069216603/sizes/l/]("http://www.flickr.com/photos/garotobossanova/4069216603/sizes/l/")

Output to apt-get remove nvidia-glx-180:
[http://www.flickr.com/photos/garotobossanova/4069216623/sizes/l/]("http://www.flickr.com/photos/garotobossanova/4069216623/sizes/l/")

Output of removing with aptitude:
[http://www.flickr.com/photos/garotobossanova/4069247563/sizes/l/]("http://www.flickr.com/photos/garotobossanova/4069247563/sizes/l/")

---

### Post by Steve60938 on 2009-11-02
I had a similar issue.

I did do a search but it didn't return any results so i apologize if this has been covered. After getting annoyed with XP again I drug out my 8.10 ubuntu disc I had made a few yrs back (or it seems at least) and installed it. Once done it informed me of an upgrade so I took it. this of coarse was only to 9.04 or .06 don't remember. Then again it told me to upgrade to 9.10 so I did. After the upgrade I restarted. When it booted up I was greeted with a white ubuntu symbal then instead of a pretty logon screen i got the ugly txt based login but it was flashing out of control and they keyboard was very laggy when trying to login. Restarted and chose the recovery mode and was able to login. I typed xinit (one of the only commands I remembered) and it gave an error about there being no screens attached and then it gave up.So i reinstalled 8.10, I am currently downloading an iso of 9.10 but don't have any discs for a clean install. Was going to mount it and add it to the repo for updating. Anyway now that the description of the issue is finished; my question,

Given my hardware listed below will I even be able to run ubuntu 9.10

Intel core duo prossesor at 1.80ghz
Nvidia 7100 256 on board video
Nforce 680i 
Realtek HD 7.1 onboard
17 inch flatscreen monitor connected by vga not hdmi

this is the compaq a6300f only cd\dvd drives have been changed.

---

### Post by Steve60938 on 2009-11-02
I had the nvidia issue nvm it was explained in another thread

---

