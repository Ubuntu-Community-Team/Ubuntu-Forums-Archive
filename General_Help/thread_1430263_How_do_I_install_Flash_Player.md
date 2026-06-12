---
title: "How do I install Flash Player"
date: 2010-03-15
forum: General Help
---

### Post by frankiethepill on 2010-03-15
Probably a stupid question. I want to install flashplayer- found the package on the adobe website- chosen the version (9.04+) and I then get the question 'Choose an application' - to open it with. What do I do now? This prompt simply takes me to file browser.

Or is there an easier way to do it?

---

### Post by Swagman on 2010-03-15
If it's the 32 bit version then it's probably more useful to...

```
sudo apt-get install ubuntu-restricted-extras
```

which Will install more than just flash.

[edit]

Saw your join date so my suggestion was probably like trying to teach granny to suck eggs !!

There are destructions on adobes site

> 


       1. Click the download link to begin installation. If a dialog box appears, follow the instructions to save the installer to your desktop.
       2. Save the .deb package to your desktop, and wait for it to download completely.
       3. Double-click on the .deb package and follow the instructions to complete installation.

          -or-
          Issue one of the following commands from the terminal:
              * dpkg --install [filename].deb
              * dpkg -i [filename].deb
       4. To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.



[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

Although when I installed from the site eleventy million years ago I distinctly remember having to set it to executable and ./ it

---

### Post by frankiethepill on 2010-03-15
Thank you Swagman for your prompt reply- now working a treat.

Yes I have been a member here for some time, but have dipped in and out of Ubuntu with each generation- I get so frustrated by the difficulties it produces, esp. with installing apps. Windows (sorry) is so easy just about- everything comes with an installer which makes my life so much easier. I have been playing with os' for years and am well familiar with cli's, but I don't need the hassle nowadays of a) finding the solution and b) trying to install it. So far this has always killed Linux for me, but at last this incarnation seems just about usable, I even got the wireless adapter in my netbook going last night which is a plus point. 

I am just hoping that someone sorts out the software repositories soon- to be having to type in a cli line of text around, say, the 'apt' command is *just* about ok, but my main gripe is how do I actually find the text to type in to install what I want. I know that I can ask people such as yourself, but it needs to be easier and more accessible if Linux is ever to be a mainstream product. 

Sorry to rant...... thanks again for your help!

---

### Post by ajgreeny on 2010-03-15
Simplicity is Ubuntu's second name if you forget about the windows way of installing applications and use synaptic or software-centre.

Just about everything you could possibly want, plus a lot more, is already waiting for you in the dedicated repositories.  Just do a search with either of the package management applications I mention above and all will be revealed.

---

### Post by t0p on 2010-03-15
> **frankiethepill said:**
>  
I am just hoping that someone sorts out the software repositories soon- to be having to type in a cli line of text around, say, the 'apt' command is *just* about ok, but my main gripe is how do I actually find the text to type in to install what I want. I know that I can ask people such as yourself, but it needs to be easier and more accessible if Linux is ever to be a mainstream product. 


You don't have to use a terminal command to install software if you prefer not to.  Go to **System > Administration > Synaptic Package Manager** and you'll find a software installer with a GUI.  Use the "Quick search" box to find what you want, then click on the name of the package you like in the list that appears.  Simples! :)

---

### Post by scouser73 on 2010-03-15
> **frankiethepill said:**
> Probably a stupid question. I want to install flashplayer- found the package on the adobe website- chosen the version (9.04+) and I then get the question 'Choose an application' - to open it with. What do I do now? This prompt simply takes me to file browser.

Or is there an easier way to do it?

[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

