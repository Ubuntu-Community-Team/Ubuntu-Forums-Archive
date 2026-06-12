---
title: "Uninstall Facial Recognition software..."
date: 2010-10-02
forum: General Help
---

### Post by Enigmapond on 2010-10-02
Hi...
I thought this was going to work well but, it doesn't and now I can't log into my computer until the application quits....about a minute.
[http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/](http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/)

I followed the install instructions which went well with no errors.

Can someone please instruct me on how to remove everything and get the GDM back to it's original state?

Your help will be greatly appreciated...:)

Thank You!

---

### Post by Enigmapond on 2010-10-02
I also seem to have a persistent service running now that I'm unable to shut off...
gdm-session-war (??) and is using an exorbitant amount of CPU...:(

---

### Post by Enigmapond on 2010-10-02
Until I find a way to uninstall this, as it doesn't show in synaptic, is there a way to reverse these two commands?

```
sudo sed -i '1i auth sufficient pam_face_authentication.so enableX' /etc/pam.d/gdm
```&

```
sudo sed -i '1i auth sufficient pam_face_authentication.so enableX' /etc/pam.d/gnome-screensaver
```These are the codes given in the above directions to add the application to the GDM...

Thanx Again...

EDIT!

Ok NOW everytime I try sudo anything in the terminal or elsewhere...the cam comes on and it tries to authenticate. Please....this is not a good thing as I am now unable to even update my system.

---

### Post by Enigmapond on 2010-10-02
desperate bump with apologies.....:(

---

### Post by Enigmapond on 2010-10-03
Well I marked this solved but really...it wasn't. I ended up re-installing Lucid...I recommend you NOT try this programme for facial recognition. No one seems to know how to work it property and from the looks of it here, with the lack of response, no one knows how to fix it to work...

Thank You............:confused:

---

### Post by kingsley404 on 2010-12-05
Sorry for bringing this back but i did this as well and now my computer has become useless please if anyone knows how to uninstall it please tell me :(

---

### Post by Enigmapond on 2010-12-05
Yea...I feel your pain. The way I "fixed" that problem was to have to re-install Lucid. No one was able to help me fix that, Sorry I can't be of any further help on that....  Good Luck...truly!

---

### Post by kingsley404 on 2010-12-05
> **Enigmapond said:**
> Yea...I feel your pain. The way I "fixed" that problem was to have to re-install Lucid. No one was able to help me fix that, Sorry I can't be of any further help on that....  Good Luck...truly!

Oh man :/ Well is there a way to do this without losing everything? like can i reinstall but keep my files? If so can you explain how to? Or how to do it in general because im lost hah

---

### Post by Enigmapond on 2010-12-05
The best way I can tell you is just to back up what you want to keep. Get it off the drive either to another partition or usb stick and just do the re-install off a LiveCD. This is what I did. I run a dual boot so I threw all my personal stuff and music on to the windows partition and re-installed. Bloody stupid programme that Facial Recognition thing. I watched some chap install it on youtube. Looked pretty straightforward but it really screwed up a lot. Sorry and best of luck.

---

### Post by karq on 2011-03-28
How to remove the facial recognition from the logon.

First
edit /etc/pam.d/gdm and remove this line
```
auth sufficient pam_face_authentication.so enableX
```

Second
edit /etc/pam.d/gnome-screensaver and remove this line
```
auth sufficient pam_face_authentication.so enableX
```

third
run 
```
sudo /etc/init.d/gdm restart
```

enjoy!!

---

