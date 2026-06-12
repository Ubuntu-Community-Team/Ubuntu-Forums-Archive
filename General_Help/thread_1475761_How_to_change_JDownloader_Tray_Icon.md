---
title: "How to change JDownloader Tray Icon?"
date: 2010-05-07
forum: General Help
---

### Post by doko1 on 2010-05-07
Hello

I'm using JDownloader, installed as described in this thread: 
[http://ubuntuforums.org/showpost.php?p=9223353&postcount=2](http://ubuntuforums.org/showpost.php?p=9223353&postcount=2)

Now, i'm using Dust theme in Ubuntu... My JDownloader Tray Icon ends up looking like this:
(see Attachement below)

Now, i heard that Java can't handle transparency, that's why the background of the JDownloader Tray Icon is white. 

In my case, a possible workaround would be to edit the Image file which is used by the Tray Icon. (changing the background to the color of the Dust-Theme)

But which file is it / where do i find it? Can anybody help me? 

Thanks!

---

### Post by doko1 on 2010-05-07
Sorry for double-post. Image-Attachement seems not to display. 
Here another try: 

[IMG]http://img132.imageshack.us/img132/9941/tray.png[/IMG]

---

### Post by Faids on 2010-05-09
The program does not use the same file for the normal icon and the tray icon.  The tray icon is located in /home/youruser/.jdownloader/jd/img/logo

There are a bunch of different logo files in the folder.  The one that was designated as the tray icon on my system was jd_logo_128_128.png.  I edited the file so it would match the default ubuntu theme.  Kind of dirty solution since the image will need to be changed if I ever decide to switch color themes but it does the trick for now.

Image attached.

---

### Post by doko1 on 2010-05-10
Very nice! This "dirty" solution worked out for me. Thanks a lot for finding the file... i didn't expect to find it there. ;)

---

### Post by smoreno on 2010-05-25
Thank you so much!!

Working for me too!


:)

---

### Post by MatthiasA on 2010-06-20
Thanks! Worked for me too.

Does anybody have a Logo for the Ambiance Theme? Would be great.

---

### Post by plaidcounty on 2010-07-20
For An Ambience Monochrome jDownloader Icon: [http://gnome-look.org/content/show.php/JDownloader%20Ambiance?content=127361](http://gnome-look.org/content/show.php/JDownloader%20Ambiance?content=127361)

---

### Post by TLArevo on 2010-11-06
> **plaidcounty said:**
> For An Ambience Monochrome jDownloader Icon: [http://gnome-look.org/content/show.php/JDownloader%20Ambiance?content=127361](http://gnome-look.org/content/show.php/JDownloader%20Ambiance?content=127361)
Thanks lot everyone !!! :) thanks again :)

---

### Post by ernz on 2010-12-08
Here's the one I did for Ambience. It's not monochrome but it doesn't look out of place.

Replace the file at /home/ernz/.jd/jd/img/logo/jd_logo_128_128.png with [THIS ONE]("http://i.imgur.com/JFp8d.png")

Edit:
[HERE'S WHAT IT LOOKS LIKE IN THE TRAY]("http://i.imgur.com/mjBg1.png")

---

### Post by s7anley on 2011-01-10
Thanks a lot ;-)

---

### Post by pbaker on 2011-01-15
I use a panel width of 21px. I created an icon of 64x64px. The background is that of the "Gnome ambience theme" panel background. If you are using another theme you have to change the background. Simply make a screenshot of your actual panel and paste it into a 64x64px image. Then use it as background for your system tray icon.

Download the attached jd_logo_128_128.png and replace the original at "~/.jdownloader/jd/img/logo/".

If you like to create your own icon I also attached the original JDownloader icon and the panel background file for the ambience theme. The size of the JDownloder icon to fit into the 21px-panel is 48x48px. Its placed 5px from the top of the background image. If you are using a different panel width you have to figure out the perfect position of your icon.

I also have tried to us transparent background. I don't know why but it doesn't work. The background of the icon always gets white.

---

### Post by antileet on 2011-01-16
> **pbaker said:**
> If you like to create your own icon I also attached the original JDownloader icon and the panel background file for the ambience theme. The size of the JDownloder icon to fit into the 21px-panel is 48x48px. Its placed 5px from the top of the background image. If you are using a different panel width you have to figure out the perfect position of your icon.

wow, thanks! 
i made my own Ubuntu Studio-themed one, about to try it out myself and hopefully it looks alright :) because the default one with a white background while my panel is a black gradient is definitely an eyesore!

---

### Post by sid32 on 2011-03-20
A pretty good version for dark themes...[IMG]http://bayimg.com/dAeMAAaDi[/IMG]

---

### Post by faical117 on 2011-04-10
This is an icon pack for Jdownloader using Faenza icons.

Just extract it in the folder img in the directory where JDownloader is installed.

[http://rockrknight.deviantart.com/art/Faenza-for-JDownloader-178217378](http://rockrknight.deviantart.com/art/Faenza-for-JDownloader-178217378)

):P

---

### Post by the_obs on 2011-05-23
Thanks for these great tray icons!

---

### Post by Pablo Alonso on 2011-05-27
Hey Man ! I worked for me too !!!
Thanksss

---

### Post by Erik500002 on 2011-07-03
Great man worked perfectly, I really like having my tray icons neatly organized. Thanks

---

