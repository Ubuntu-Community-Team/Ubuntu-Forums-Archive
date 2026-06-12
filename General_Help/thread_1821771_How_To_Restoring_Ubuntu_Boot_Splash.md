---
title: "How To: Restoring Ubuntu Boot Splash"
date: 2011-08-09
forum: General Help
---

### Post by ssherwood on 2011-08-09
Hi Ubuntu Users,

I have noticed, as well as subscribed and posted on threads about the ubuntu boot splash and how to restore it. Now some of the replies have been useful, but my only issue with their methods where I still had the text and the graphic boot merged into one.

Now I have found a way of completely restoring the boot splash without the text, as well as the boot splash only being viewed for a split second after a minute or two of a black screen.

*[COLOR="Red"]Note: This How To was tried and tested on Ubuntu 10.10 Maverick Meerkat, but should still work in all other distributions which support the following software within this How To.[/COLOR]*

[SIZE="3"]_How To:_[/SIZE]

_Step 1:_

Open Ubuntu Software Centre and search for startup-manager and install it.

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8126[/IMG]

_Step 2:_

Open the Startup Manager (System, Administration) and your config should look similar to the image below.

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8127[/IMG]

Now if you are dual booting DO NOT change the TIME OUT config leave it other wise if you are only running ubuntu then change the config to the same as the image below apart from the screen resolution, change that in accordance with your screen resolution. Then close the manager USING the close button.

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8128[/IMG]

_Step 3:_

Now open the terminal and enter the root mode (I use 'sudo -i', without quotes, to enter into overall root user) and add the BUC ppa repository.

```
add-apt-repository ppa:ingalex/super-boot-manager
```

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8129[/IMG]

Then install the buc super-boot-manager, using the following command:

```
apt-get install buc
```

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8130[/IMG]

_Step 4:_

Now open the Super Boot Manager, located in the System Tools menu, and click on the Plymouth Manager.

Next click on the Enable button at the bottom to enable Plymouth.

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8133[/IMG]

Once enabled, go to the themes tab and choose a theme and then apply changes a the bottom.

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8134[/IMG]

Finally go to the Proprietary Drivers tab, and first CAREFULLY read the notice, if this doesn't apply to you, the follow these final few steps. Once you have read the notice check the grub2 tab (if your using the grub 2 boot manager) or burg (if your using burg boot manager) and then click the Apply Patch button to apply the config. 

[IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8135[/IMG]

_Step 5:_

Reboot your system and notice the change.

[COLOR="Red"]*Note: The change may take effect on the second or third boot, this is dependent on any updates you have installed or even the system resources.*[/COLOR]

Any questions, then feel free to leave a comment.

Stephen - *ssherwood*

---

### Post by ssherwood on 2012-02-03
Hello Ubuntu Users,

If you are having issues which restoring the boot splash in 11.04 or 11.10 then ***_[COLOR="Red"]PLEASE[/COLOR]_*** ignore Step 3.

Instead replace the Step 3 with the following:

```

[U]sudo add-apt-repository ppa:ingalex/super-boot-manager
sudo apt-get update
sudo apt-get install super-boot-manager[/U]
```

Then follow the rest of the above guide.

---

### Post by ssherwood on 2012-02-15
Hello fellow Ubuntu users,

In August last year, I put together a little *How-To* on restoring the Ubuntu Boot Splash using a tool known as Super-Boot-Manager. Now the SBM still works for Ubuntu 11.10, with great success, but this post is about restoring the Ubuntu Boot Splash using the Plymouth Manager.

*[COLOR="Red"]Note: This How-To was carried out on the Ubuntu 11.10 system. The majority of the following steps should work on earlier systems which run Plymouth.[/COLOR]*

You can install the packages via 1 of the 2 ways.

_Method 1_:

Click the install button below and run the script.

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212694&stc=1&d=1329318432[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=212695&stc=1&d=1329318507")

*[COLOR="Red"]Note: You may need to make the script executable through the script's properties.[/COLOR]*

_Method 2_:

This method will allow you to enter the commands for installing the packages manually.

First, run terminal either through the dash or by pressing [SIZE="3"]*Ctrl, Alt + T*[/SIZE] simultaneously.

Next enter the commands either line-by-line or all at once:
1. Line-by-Line:
```

sudo apt-get install startupmanager
sudo apt-add-repository ppa:mefrio-g/plymouthmanager
sudo apt-get update
sudo apt-get install plymouth-manager

```

2. All at once:
```

sudo apt-get install startupmanager && sudo apt-add-repository ppa:mefrio-g/plymouthmanager && sudo apt-get update && sudo apt-get install plymouth-manager

```

Now that we have the packages installed, we can now start to configure Plymouth.

_Step 1_:
Open Start-Up Manager from the dash by typing *Startup*. Once the Start-Up Manager is open, your visual display fo the config should look similar to the following, minus the Default OS should be the latest version.

[CENTER][IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8127[/IMG][/CENTER]

Now I caution you if you are dual booting DO NOT change the TIME OUT config, leave it as it is, other wise if you are only running ubuntu then change the config to the same as the image below apart from the screen resolution, change that in accordance with your screen resolution. Then close the manager USING the close button.

[CENTER][IMG]http://ubuntuforums.org/picture.php?albumid=2409&pictureid=8128[/IMG][/CENTER]

_Step 2:_
Now open the Plymouth Manager through the dash, and once open your display should look similar to the following:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=212697&stc=1&d=1329320197[/IMG][/CENTER]

Select a suitable resolution and click the CHANGE button. This may open an XTERM window asking for your password, you MUST proceed by entering your password and following any of the required steps.

_Step 3:_
Once you have completed Step 2, click on the BEGIN button under, 'Make Plymouth compatible with closed source video driver'. This will ensure that Plymouth is patched correctly with your graphics card, e.g. ATI, nVidia.

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=212698&stc=1&d=1329320341[/IMG][/CENTER]

_Step 4:_
Finally select the THEMES tab and select a theme(this is optional). Now for the purpose of this tutorial I kept the original boot splash for Ubuntu. 

Once you have found a theme you like click the INSTALL button and follow the prompts in the following XTERM window (This is optional). Then click APPLY INSTALLED THEME and again follow the prompts in the XTERM window.

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=212699&d=1329319102[/IMG][/CENTER]


*[COLOR="Red"]Note: The changes WILL NOT take affect until a full system reboot. If you would like to change the TIME OUT config, then follow method in Step 1.[/COLOR]*

Thank You.

Stephen,
ssherwood.

---

### Post by Mark Phelps on 2012-02-16
Update-manager doesn't work well with recent Ubuntu versions.

Instead, you should try using SBM or, instead, you could try using GRUB-Customizer:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by ssherwood on 2012-02-16
Hi,

The How-To dont use update manager. as well these How-To's have worked for me with no issues at all.

Thanks for adding an extra link for restoring the boot splash.

stephen

---

### Post by ssherwood on 2012-02-20
Hiya fellow users,

I have derived a PDF for the first tutorial I posted back in August 2011. 

[SIZE="3"]**[How To_Restore Ubuntu Boot Splash - SBM]("https://doc-10-40-docsviewer.googleusercontent.com/viewer/securedownload/khqa1ohbf1rpl2o0h7qkgd2gjbrhh2vb/0sd8vmbajmfp0ofs6ip5sh2a6r0v9mss/1329736500000/ZXhwbG9yZXI=/AGZ5hq--Z9EufykqJGMOeWunzlRh/MEJ3aVlDTWRoWlJqV016UXpOVGRsTXprdFlUbGtPUzAwTm1OaUxXRTNPR1F0T1RJMllXSTBaV00xWkRKaQ==?sec=AHSqidZrwIqAW8tSU9dAj5Utmz3DbaLDepCCUr1Z5-W0Tggy245Ft_-kKkbw23vNxXy2_CBJFA4e5bBKN-zL59emxc1rC9KOioN1E0Jo46UENIROCecRyy3v3iNEE6NUKIOnDzcH6dobIqYahrydv_lsN9ajTfcjAT73rj0nfqYYPflmL8VTQaf2t7CCdY5wRBDb8dPCNkH9b1f-KYuyJR51LEiVWgZYsaQCzkLcBpKorTa74FXlckVTH2VZcCQlPz4E14JMNYlrqfPXbfHMxubEzuvJHYJrWTyuwqZtTjVJhOaToTpyDXIRuZlLbRVFjClZxfxNWAp15iG9V1J_uY9GzM3aYwow5Eq5Z3PYtFkM0b4VQtl-S2MFnQqAaUrcRObvbvrk5dAiUOEREtzjgQqJ1DCK2oPahS05lVr7XqiGeyCws0Uk4uX9osbnWJBRr7TBv3qtdvck&a=dl&filename=How+To_+Restore+Ubuntu+Boot+Splash+-+SBM.pdf&nonce=6uv60gf9glfv4&user=AGZ5hq--Z9EufykqJGMOeWunzlRh&hash=8nq53i8pdoba3cn2hsca4111ump3997g")**[/SIZE]

Any issues please leave a comment.

Thanks Stephen

---

### Post by pete0403 on 2012-03-22
Hello,

This did not work for me in 11.10.  I followed the directions for 11.10 twice and nothing except my boot screen is black and blank rather than purple and blank.  The same Ubuntu default splash displays for 1 second before the desktop is displayed.

---

### Post by ssherwood on 2012-03-22
Which manager did you use?

---

### Post by pete0403 on 2012-03-22
I followed method #2 of post #3 using plymouthmanager

---

### Post by ssherwood on 2012-03-25
i had no issues with any of the tutorials I've done. Post the specs of our system as it could be something with the graphics card which I might not have considered. But I.ll do a video tutorial and post the link on here for you to follow. (There will be no sound just subs)

Stephen

---

### Post by ssherwood on 2012-03-31
Video Tutorial [http://youtu.be/nrHPgd4RdRg]("http://youtu.be/nrHPgd4RdRg")

---

### Post by johnaaronrose on 2012-04-07
I'm getting blank screen on startup (OK when Login screen appears) & shutdown. I've tried using SBM (but get no menu entry after install), Grub Customizer but didn't show my monitor's best resolution (1440x900) which is default i.e. as used in Login onwards. I've tried Plymouth Manager (which at least allowed me to select 1440x900) but made no difference.

I have a new desktop with Intel Sandy Bridge Integrated Graphics Controller and am using Desktop Lucid 64 bit. My 5 year old laptop has always worked perfectly with boot 'splash' screen no matter what the resolution selected: it uses Lucid Desktop 32 bit.

lspci shows graphics controller as:
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
If you need more info on spec, please let me know.

---

### Post by ssherwood on 2012-04-07
hi follow this article to restore ur boot screen

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Stephen

---

### Post by johnaaronrose on 2012-04-07
Stephen,

Thank you. It worked.

---

### Post by ssherwood on 2012-04-08
Glad I could help bud. :)

Stephen

---

### Post by neu5eeCh on 2012-05-04
The Startup Manager doesn't appear to be available for Ubuntu 12.04. 

Is there a command line method to restore the default Ubuntu splash screen in Plymouth. I installed the Xubuntu desktop and, of course, Xubuntu felt the need to replace the splash screen.

---

### Post by ssherwood on 2012-05-05
Sorry for late reply...

Ummmm is the splash screen actually displaying if so then you can just download and install the SBM(Super-Boot-Manager) or PM(Plymouth Manager) and you can change the boot splash.

If its not displaying the splash then follow this tutorial:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Thanks Stephen

---

### Post by pete0403 on 2012-05-30
I've been working on this off and on for awhile.  I'm happy to say that with help from this thread and some of my own searching and trial & error, I've solved my issue.

The problem was GRUB2's default kernel parameters (quiet splash) were not compatible with my nVidia gfx card/driver combo.  I installed GRUB Customizer and changed the kernel parameters from "quiet splash" to "nomodeset".  This completely solved my problem

Thanks for the help along the way!

---

