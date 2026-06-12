---
title: "Switching over to Ubuntu"
date: 2010-12-04
forum: General Help
---

### Post by Cheetah05 on 2010-12-04
Hi there,

I am switching my laptop over to Ubuntu full time. (It's a Dell 13z). I'm running 64bit as I have 4GB of RAM.

I've managed to get most things working how I want but just wanted some help and opinions on a few things.

I have installed Compiz settings manager so I can change the desktop effects and setup an Expose and Dashboard effects. I have done this and everything is working fine.

- I also want a Dock....currently I am using Docky and it appears quite stable, but I just wanted to know whether this is the best option.

- Is there a file explorer that doesn't make the folders and browsing the file system look so cartoony?

- Is there any way to get things to mount on the right hand side of the desktop rather than the left?

- I am running Chrome as my fulltime browser, how do I get flash to work? Does it work in 64bit?

- Would the best way to get Office 2010 working be through a virtual machine? I'm a bit conssious of the face that virtual machines would probably drain the battery...what do you think?


That's all I can think of at the moment.

Thanks.
Ben.

---

### Post by Jahid65 on 2010-12-04
1 Docky is good. But I personally use cairo-dock. I like it very much. 

2 Have any problem with nautilus. I find it very nice. However you can use other file manager like Dolphin, Thuner etc.

3 After mounting any partition, select it & drag it to right side of the desktop. Now whenever you mount or unmount this drive , the drive will be showed in right side. Please Do not use **Clean up by name in **click. Otherwise this will reverted to left side.

4 I don't use 64 bit version. But I think 64 bit version of flash is not very good.

5 Personally I don't like using windows application on linux. you can use 2007 in wine. Not sure for 2010. But you can take a look at the IBM Lotus Symphony (Free) or Softmaker Office ($60). Both have Linux version & compatibility with MS Office is very good.

---

### Post by Spyderkid on 2010-12-04
If you want a Apple style desktop you can visit this link its completely trusted as its from source forge (download it if you want, It's easy to uninstall (I've done it myself ))

[Macbuntu]("http://sourceforge.net/projects/macbuntu/")   <----Link
Also you can move the dock around and it makes your desktop EXTREMELY COOL!!




To get Flash, Java etc... for chrome go to software centre and download "Ubuntu Restricted Extras"






2010 always work on linux, best bet is 2007 and its a bit of a faff.
But give 2010 a try here's how... [link]("https://help.ubuntu.com/community/Microsoft_Office")






You can download more appearances go to appearances and click find more.

---

### Post by akand074 on 2010-12-04
> **Cheetah05 said:**
> Hi there,

I am switching my laptop over to Ubuntu full time. (It's a Dell 13z). I'm running 64bit as I have 4GB of RAM.

I've managed to get most things working how I want but just wanted some help and opinions on a few things.

I have installed Compiz settings manager so I can change the desktop effects and setup an Expose and Dashboard effects. I have done this and everything is working fine.

- I also want a Dock....currently I am using Docky and it appears quite stable, but I just wanted to know whether this is the best option.

- Is there a file explorer that doesn't make the folders and browsing the file system look so cartoony?

- Is there any way to get things to mount on the right hand side of the desktop rather than the left?

- I am running Chrome as my fulltime browser, how do I get flash to work? Does it work in 64bit?

- Would the best way to get Office 2010 working be through a virtual machine? I'm a bit conssious of the face that virtual machines would probably drain the battery...what do you think?


That's all I can think of at the moment.

Thanks.
Ben.

- Docky is good, another good dock is AWN, I'm currently using AWN Lucido style, it's really cool but it's only available in the development version so you'll have to install that one. 
- 64 bit flash works flawlessly now. Just download it from the Adobe website.
- I probably wouldn't run a virtual machine on a laptop on battery, I would imagine it would be draining. Wine can run office 2007 fine, not 2010 yet though as far as I'm aware. Depending on your uses, you can look up other Linux alternatives if you don't like open office.

---

### Post by The Cog on 2010-12-04
For a file explorer, both thunar and dolphin look good to me. Installing dolphin will pull in hundreds of megabytes of KDE libraries, but I think thunar will be quite a small install.

For flash, I think installing ubuntu-restricted-extras will probably do the trick.

---

### Post by Cheetah05 on 2010-12-05
Thanks for everyone's responses. I am not trying to get ubuntu to look like a mac, i just like some of the things i have seen on a mac.

> **The Cog said:**
> 
For flash, I think installing ubuntu-restricted-extras will probably do the trick.

I already tried this and it didn't work :( Flash in firefox seems to work, but not in Chrome.

When I goto about:plugins in Chrome it doesn't show flash either.

---

### Post by oldos2er on 2010-12-05
Use this to install 64-bit flash: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
In my opinion it works better than the 32-bit flash which ubuntu-restricted-extras installs.

---

### Post by Cheetah05 on 2010-12-05
> **oldos2er said:**
> Use this to install 64-bit flash: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
In my opinion it works better than the 32-bit flash which ubuntu-restricted-extras installs.

But I am using Google Chrome as my browser....would that still work?

...Also, is there anyway to have the mail widget thing that is in the sytem tray open googlemail in browser and check for mail there rather than use evolution or whatever the default mail thing is.

---

### Post by oldos2er on 2010-12-05
Just run Firefox to install flash, Chrome should find it after a restart.

If you're referring to the Gnome panel applet, I don't know whether it "does" gmail or not; but 'checkgmail' works fine for that purpose.

---

### Post by Cheetah05 on 2010-12-05
> **oldos2er said:**
> Just run Firefox to install flash, Chrome should find it after a restart.

If you're referring to the Gnome panel applet, I don't know whether it "does" gmail or not; but 'checkgmail' works fine for that purpose.

Ah it worked...great...thank you very much!

I installed gm-notify and that seems to work fine in the Indicator Applet in gnome.

---

### Post by Mark Phelps on 2010-12-05
For a file explorer, look into Gnome-Commander.  It's a 2-pane file explorer similar in look and feel to some of the older Windows products.

---

### Post by Cheetah05 on 2010-12-09
Sometimes when I leave my computer idle for a while, when it goes to screensaver (its a blank screen) it comes up with a load of error text. When I move the mouse after a few seconds it comes back to the desktop fine....what is this?

This also happens everytime I put my computer to sleep and wake it up. It shows the error message for a few seconds and then loads the desktop.

Is this a common issue or would you need the error message to debug this?



....also, completely different topic, what is the keyring used for, why is it useful?

---

