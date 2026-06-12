---
title: "GOOGLE EARTH install help"
date: 2010-08-29
forum: General Help
---

### Post by melinda on 2010-08-29
so I am having some install problems with google earth.

I tried the Ubuntu Software Center. And installed Debian package of Google Earth.

Said it was installed but there was link/launcher.  I tried to create launcher.  doesnt work -- no such file exists.

I tired to use the Synaptic package manager to create a debian pkg of google earth.  Said installed all sorts of files.  No launcher for google earth.

downloaded bin file from google earth to desktop

opened terminal 
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

Began install
Chose quit.

launcher icon appears under internet/google earth.

open.  it opens then shortly closes. 

Tried to uninstall via terminal
Tried to unistall under synaptic pakcage manager. 

tried to reboot gnome after installs.

what am I doing wrong?

---

### Post by Vaphell on 2010-08-29
open terminal, run 'googleearth'
apps usually print what their problems are into terminal, it's a primary debug tool :)
maybe you'll find out something of substance.

---

### Post by melinda on 2010-08-29
vaphell

so do you know what I am looking at?  I sure don't

robert@robert-desktop:~$ googleearth
Warning(optionsfile.cc:22): Load: Could not open file
No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is not Gtk2 (0).
[000:005] Using Xt toolkit
** (process:2079): DEBUG: NP_Initialize
** (process:2079): DEBUG: NP_Initialize succeeded
Segmentation fault
robert@robert-desktop:~$ 


Thanks

melinda

---

### Post by Vaphell on 2010-08-29
doesn't look too good :-)

tell me, what these 2 commands return?
```
ls -la ~/.config/Google/
ls -la ~/.googleearth/
```

these are GE config/cache dirs
you can try to eradicate them both to be sure they are restored at the next GE start and are owned by you.

if purging those dirs fails, does GE run fine with sudo? (sudo googleearth)


also google returns something like this for segfault with GE, this one looks good - something about missing library
[http://basicubuntu.blogspot.com/2009/07/segmentation-fault-in-google-earth.html](http://basicubuntu.blogspot.com/2009/07/segmentation-fault-in-google-earth.html)

---

### Post by melinda on 2010-08-29
command 1:

robert@robert-desktop:~$ ls -la ~/.config/Google/
total 12
drwxr-xr-x  2 robert robert 4096 2010-08-29 15:26 .
drwxr-xr-x 20 robert robert 4096 2010-08-29 15:26 ..
-rw-r--r--  1 robert robert  795 2010-08-29 16:30 GoogleEarthPlus.conf
robert@robert-desktop:~$ 


command 2:

robert@robert-desktop:~$ ls -la ~/.googleearth/
total 12
drwx------  3 robert robert 4096 2010-08-29 16:30 .
drwxr-xr-x 47 robert robert 4096 2010-08-29 16:30 ..
drwxr-xr-x  4 robert robert 4096 2010-08-29 16:30 Cache
lrwxrwxrwx  1 robert robert   10 2010-08-29 16:30 instance-running-lock -> /proc/2079
robert@robert-desktop:~$



how do you eradicate them?

Melinda

---

### Post by uRock on 2010-08-29
cd ~/Desktop
chmod +x Goog*
then right click the google file and then open with, then enter sh in the custom command.

---

### Post by melinda on 2010-08-29
So here's what happens with sudo googleearth:

It opened and then closed ....same deal.  here's the Terminal info:


robert@robert-desktop:~$ sudo googleearth
[sudo] password for robert: 
Warning(optionsfile.cc:22): Load: Could not open file
No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is not Gtk2 (0).
[000:005] Using Xt toolkit
** (process:2187): DEBUG: NP_Initialize
** (process:2187): DEBUG: NP_Initialize succeeded
Segmentation fault
robert@robert-desktop:~$ 



melinda

---

### Post by jcolyn on 2010-08-29
uninstall what you have installed. Everything related to googleearth.

Once done  enter into the terminal the below info.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated 
install medibuntu-keyring && sudo apt-get --quiet update
```

Once you are done enter ```
sudo apt-get update
```

Now go to your package manager (synaptic for gnome or Kpackage for KDE) and type googleearth.

Make sure it is the package from Medibuntu then install it..

---

### Post by melinda on 2010-08-29
uRock ..

What is that command to do?
sorry for my ignorance.  Im like a wee little baby just learning to speak linux.

melinda

---

### Post by melinda on 2010-08-29
jcolyn

this is the uninstall code I have/use:

sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth




perhaps it isnt working?  
is there another way to uninstall it?

---

### Post by melinda on 2010-08-29
jcolyn:

great I tried a uninstall using that code and this is my terminal:

robert@robert-desktop:~$ sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
rm: cannot remove `/usr/share/mimelnk/application/vnd.google-earth.*': No such file or directory
rm: cannot remove `/usr/share/applnk/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/share/gnome/apps/Google-googleearth.desktop': No such file or directory
robert@robert-desktop:~$ 


however -- the launcher/icon under Applications>Internet>Google Earth is GONE.   so confusing.  Because I used that code before and it asked me my password and then uninstalled.  ???

how do I know if its all uninstalled??

---

### Post by melinda on 2010-08-29
jcolyn:

was that code for mediunbuntu correct?  this is what my terminal spit out:

robert@robert-desktop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
robert@robert-desktop:~$ http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
> sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated 
bash: http://www.medibuntu.org/sources.list.d/lucid.list: No such file or directory
robert@robert-desktop:~$ install medibuntu-keyring && sudo apt-get --quiet update
install: missing destination file operand after `medibuntu-keyring'
Try `install --help' for more information.
robert@robert-desktop:~$ 


Melinda

---

### Post by melinda on 2010-08-29
> **melinda said:**
> jcolyn:

was that code for mediunbuntu correct?  this is what my terminal spit out:

robert@robert-desktop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
robert@robert-desktop:~$ http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
> sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated 
bash: http://www.medibuntu.org/sources.list.d/lucid.list: No such file or directory
robert@robert-desktop:~$ install medibuntu-keyring && sudo apt-get --quiet update
install: missing destination file operand after `medibuntu-keyring'
Try `install --help' for more information.
robert@robert-desktop:~$ 


Melinda


NEVER MIND.  I got the correct code:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by melinda on 2010-08-29
jcolyn:

Well I don't know what all that other install biz did for me but waste my time I guess. 

 Medibuntu repository was the way to get it. I guess the other files were missing some files? I don't know.  But don't care cuz for now ..its open, working and not closing on me. 


WOOT WOOT!

Thanks

Melinda

---

### Post by melinda on 2010-08-29
ummm... ok.  will check into that?

---

### Post by uRock on 2010-08-29
> **melinda said:**
> uRock ..

What is that command to do?
sorry for my ignorance.  Im like a wee little baby just learning to speak linux.

melinda
It will properly install Google Earth.

---

### Post by uRock on 2010-08-29
> **melinda said:**
> ummm... ok.  will check into that?
Do not go there, it is spam, I have reported it.

---

### Post by jcolyn on 2010-08-30
> **melinda said:**
> jcolyn

this is the uninstall code I have/use:

sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth




perhaps it isnt working?  
is there another way to uninstall it?

Go to your package manager Kpackage for KDE or synaptic for Gnome and type googleearth in the search box and uninstall from there.

---

### Post by jcolyn on 2010-08-30
> **melinda said:**
> jcolyn:

Well I don't know what all that other install biz did for me but waste my time I guess. 

 Medibuntu repository was the way to get it. I guess the other files were missing some files? I don't know.  But don't care cuz for now ..its open, working and not closing on me. 


WOOT WOOT!

Thanks

Melinda

The .deb file that many download from google and other sites lack the additional files needed to run googleearth.

---

### Post by uRock on 2010-08-31
> **jcolyn said:**
> The .deb file that many download from google and other sites lack the additional files needed to run googleearth.
Nope, I didn't add anything when I went through the steps in a previous post and Google Earth works flawlessly.

---

### Post by jcolyn on 2010-08-31
> **melinda said:**
> 
perhaps it isnt working?  
is there another way to uninstall it?

If a program installs it will show up in synaptic.

In all probability since the Medibuntu version is working the original one you tried to install failed so there is nothing to un-install.

---

