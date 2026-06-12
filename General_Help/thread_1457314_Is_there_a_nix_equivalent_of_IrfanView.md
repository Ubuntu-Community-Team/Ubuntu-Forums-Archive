---
title: "Is there a *nix equivalent of IrfanView?"
date: 2010-04-18
forum: General Help
---

### Post by HHx66 on 2010-04-18
I used the software a lot on Windows, and I was wondering if theres a *nix equivalent of it somewhere?

---

### Post by carl4926 on 2010-04-18
Maybe this:
Phatch

---

### Post by jmszr on 2010-04-18
HHx66,

Here are a couple of possibilities: [http://www.xnview.com/en/xnview.html](http://www.xnview.com/en/xnview.html) and: [http://www.techishare.com/blog/tech/how-to-install-irfanview-on-ubuntu-9-10/](http://www.techishare.com/blog/tech/how-to-install-irfanview-on-ubuntu-9-10/) .

---

### Post by HHx66 on 2010-04-19
Thanks for all the help (sorry for the late reply) I'm going to try XnView and Phatch and if they don't fit my needs I'll just install IrfanView under wine.

---

### Post by mgco on 2010-05-12
I agree with you on this.
I don't see F-Spot or Eye-of-Gnome as much of a help (can't even crop!)
Right now I'm checking out gThumb, which imho has better features than F-Spot, but I still miss Irfanview's bulk editing features. Any app suggestions that don't require wine? thanks

---

### Post by Orange Kingdom on 2010-05-12
There is no app like irfanview unfortunately.
Perhaps [http://gwenview.sourceforge.net/](http://gwenview.sourceforge.net/) is something similar for you.

---

### Post by Phrea on 2010-05-13
> **Orange Kingdom said:**
> There is no app like irfanview unfortunately.
Perhaps [http://gwenview.sourceforge.net/](http://gwenview.sourceforge.net/) is something similar for you.

Looking into this too, but it is originally a KDE app.
But, if it does what we want, I'm all for it then.

---

### Post by Midnighter on 2010-05-13
I was seeking a replacement myself a while ago. In the end, installed it under wine, and setup a simple script to associate it with my image files. Works great. Can give a copy of the script if anyone wants. Just ask. Cheers. :)

---

### Post by emarkay on 2010-05-13
Nothing beats IrfanView for editing and painting of simple and semi-complex images - have been using for years and even when I had CS3 Photoshop it was quick, effective and easy!! 

Just WINE it and: 

  	 	 	 	 	 	  [SIZE=2]Insure that MFC42.DLL is installed in the WINE/System32 directory as in Windows. | Insure the "Set INI file" setting is set to "IrfanView folder" when installing. | Once installed, edit "i_view32.ini" and delete all lines following *"[Toolbar]"*.[/SIZE]

---

### Post by HC48 on 2010-05-17
Hello,
I also like Irfanview and it worked ok in Karmic with Wine. However it won't work in Lucid, I've tried following some advice in this thread:
[http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot](http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot)
in order to get F-spot working, but gave up and got digicam instead.
But I really would like to get Irfanview working, I've tried an older version and changing permissions, configuring Wine etc but nothing works. I have Unfreez which is working ok ... 
Can anyone help? I'm afraid I'm a beginner so can only follow simple instructions and I'm still afraid to make a mess if I use the terminal.
H :)

---

### Post by HC48 on 2010-05-17
> **emarkay said:**
> Nothing beats IrfanView for editing and painting of simple and semi-complex images - have been using for years and even when I had CS3 Photoshop it was quick, effective and easy!! 

Just WINE it and: 

                                 [SIZE=2]Insure that MFC42.DLL is installed in the WINE/System32 directory as in Windows. | Insure the "Set INI file" setting is set to "IrfanView folder" when installing. | Once installed, edit "i_view32.ini" and delete all lines following *"[Toolbar]"*.[/SIZE]

I'm afraid this is a bit too complicated for me unless you have the patience to give me a step by step guide.....:frown: Sorry...

H :)

Later: found system 32 directory, I don't have MFC42.DLL.
I have tried this document:
[https://help.ubuntu.com/community/Wine/IrfanView](https://help.ubuntu.com/community/Wine/IrfanView)
which seemed good and have downloaded everything but it gets downloaded to the downloads file and I can't transfer the downloaded files to 'home' as is advised in the document. I tried the terminal anyway but can't get past the first command as it doesn't find irfanview. I suppose that is because it's in the wrong place.
So, how do I change the setting to download to 'home'? (An easy way). I may find out by myself meanwhiles...

---

### Post by HC48 on 2010-05-17
Tried Xnview, installed all by itself when downloaded and put an icon on the bureau. Seems interesting but haven't found the batches tool. Have I missed it?
H :)

Yes, it seems to be there in the tools menu. Will try later.

---

### Post by nechus on 2010-07-27
Hi, HC

Did you solve your problem with IrfanView already? Were you able to install it?

---

### Post by HC48 on 2010-07-29
Hi nechus,
No, not in Lucid, I have managed with Xnview and Gimp for what I need to do. However I had no problem with Irfanview in Karmic. I downloaded and installed, I don't remember doing anything special and I'm not an expert at all.
Good luck!
HC

---

### Post by foxmulder881 on 2010-07-29
You probably will  not find an all-in-one solution on Linux but rather a collection of different tools with the same capabilities. It's all possible, for sure.

---

### Post by nechus on 2010-07-30
I was asking because, even though I haven't tried installing IrfanView in Lucid, I have kept a copy of MFC42.DLL ever since I first installed it years ago. It's available if you need it.

---

### Post by HC48 on 2010-08-01
Thank you nechus, I'll keep you posted when I've had another go! I just need to get round to it again... I think I have an old copy of the program too somewhere...
Have a nice day.

---

### Post by nechus on 2010-09-09
I prepared an IrfanView icon:
[http://www.glowfoto.com/static_image/09-222054L/4193/png/09/2010/img4/glowfoto](http://www.glowfoto.com/static_image/09-222054L/4193/png/09/2010/img4/glowfoto)

---

### Post by HC48 on 2010-10-30
As promised here is an update, I have finally solved the problem by using an older version of Irfanview, recuperated from an old computer, which I hadn't deleted ie. version 4.20  which works with Wine.
I hope this helps if some people are still looking for solutions...

H  :)

PS sorry I took so long...
PPS can't get the music files to work for slideshow and the help notes don't work... I'll try again later.

---

### Post by berlinblue on 2010-11-29
Could anyone tell me, where to find the **deb-package** for [[COLOR="Red"]XNVIEW[/COLOR]]("http://www.xnview.com/en/downloadunix.html"), or any other **newb-tutorial** to get it working under Ubuntu 10.10??

Really, imho XNVIEW is one of the best tools for image management & editing, which I consider more useful then IRFANVIEW, too.

Is it just me, wondering why it's not available from the Ubuntu Software Center ... ??? 

:o // Thanks!

---

### Post by Chronon on 2010-11-29
Probably a big reason is that it is freeware rather than free software.

---

