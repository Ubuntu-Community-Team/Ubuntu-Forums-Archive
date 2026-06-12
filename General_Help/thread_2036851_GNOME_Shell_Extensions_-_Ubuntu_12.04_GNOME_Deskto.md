---
title: "GNOME Shell Extensions - Ubuntu 12.04 GNOME Desktop"
date: 2012-08-03
forum: General Help
---

### Post by tecknomage on 2012-08-03
**RE:** Ubuntu 12.40, GNOME Desktop (classic)

I already have the **GNOME Shell** and **Tweak Tool** installed.

The Tweak Tool shows NO Extensions. I found a site that says to use the below Terminal Command:

**sudo apt-get install gnome-shell-extensions**

Did this, rebooted, but still no Extensions listed in Tweak Tool.

**Help** :confused:

---

### Post by Cheesemill on 2012-08-03
I get all my extensions directly from the website.
[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by tecknomage on 2012-08-03
> **Cheesemill said:**
> I get all my extensions directly from the website.
[https://extensions.gnome.org/](https://extensions.gnome.org/)

Thanks for the site.

Please, just HOW do I download install these extensions :confused:

**Example:**  "*Alternative Status Menu* " I don't see an actual download link on the page for this. And the "Extension Homepage" is even more confusing.


**FINALLY:** You are likely misunderstanding my problem as stated. **The GNOME Tweak Tool is NOT displaying ANY Extensions options.** I suspect that getting any extensions from the site in quote will not work until the Tweak Tool gets fixed.

---

### Post by Cheesemill on 2012-08-03
> **tecknomage said:**
> Thanks for the site.

Please, just HOW do I download install these extensions :confused:

**Example:**  "*Alternative Status Menu* " I don't see an actual download link on the page for this. And the "Extension Homepage" is even more confusing.


**FINALLY:** You are likely misunderstanding my problem as stated. **The GNOME Tweak Tool is NOT displaying ANY Extensions options.** I suspect that getting any extensions from the site in quote will not work until the Tweak Tool gets fixed.

Just click on the on/off switch in the top left corner of the extensions web page (see screenshot 1).

gnome-tweak-tool won't display the extensions until you have installed them from the web site. Also it is unlikely to be a problem with gnome-tweak-tool, you don't even need to install it if you don't want to. All of your Gnome extensions can be managed through the web site from the 'Installed extensions' page (see screenshot 2).

---

### Post by tecknomage on 2012-08-03
> **Cheesemill said:**
> Just click on the on/off switch in the top left corner of the extensions web page (see screenshot 1).

gnome-tweak-tool won't display the extensions until you have installed them from the web site. Also it is unlikely to be a problem with gnome-tweak-tool, you don't even need to install it if you don't want to. All of your Gnome extensions can be managed through the web site from the 'Installed extensions' page (see screenshot 2).

Nope. The "Installed Extensions" tab shows nothing (*see screenshot*).

Note that according to **Software Center** I _do have the extensions installed_, and I found them in **/usr/share/gnome-shell**.

---

### Post by Cheesemill on 2012-08-03
I've never had any luck installing extensions through the software centre, what happens if you try installing them from the web site.

Also are you actually using gnome-shell? It doesn't look like it from your screenshot.

---

### Post by tecknomage on 2012-08-03
> **Cheesemill said:**
> I've never had any luck installing extensions through the software centre, what happens if you try installing them from the web site.

Also are you actually using gnome-shell? It doesn't look like it from your screenshot.

I asked this before, HOW :confused:

There is no download link that I understand. **I need specific step-by-step procedure to download from site**.

---

### Post by Cheesemill on 2012-08-03
> **tecknomage said:**
> I asked this before, HOW :confused:

There is no download link that I understand. **I need specific step-by-step procedure to download from site**.
As I told you earlier, click on the on/off switch in the top left of the web page.
I've annotated my screenshot to make it clearer for you.

---

### Post by Cheesemill on 2012-08-03
I've just noticed in your first post that you are using Gnome classic mode, I think that this is your problem.

Surprisingly enough gnome-shell extensions only work if you are actually using gnome-shell.
Try logging out and then back in to a gnome-shell session and see if this fixes your problem.

---

### Post by tecknomage on 2012-08-03
> **Cheesemill said:**
> I've just noticed in your first post that you are using Gnome classic mode, I think that this is your problem.

Surprisingly enough gnome-shell extensions only work if you are actually using gnome-shell.
Try logging out and then back in to a gnome-shell session and see if this fixes your problem.

**I AM using GNOME Classic**.

[quote= System Profiler tool]

**Version**
 KernelLinux 3.2.0-27-generic-pae (i686)
 Compiled#43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012
C Library Unknown
Default C CompilerGNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)
Distribution **Ubuntu 12.04 LTS**

**Current Session**
Computer Name LC2100SN
User Nametecknomage (Tecknomage)
Home Directory/home/tecknomage
Desktop Environment **GNOME (gnome-classic)**[/quote]

---

### Post by Cheesemill on 2012-08-03
> **tecknomage said:**
> **I AM using GNOME Classic**.

In that case you can't use gnome-shell extensions.

You can only use gnome-shell extensions if you are actually running gnome-shell :)

---

### Post by wheeze on 2012-08-03
> **tecknomage said:**
> **I AM using GNOME Classic**.

GNOME Classic != GNOME Shell

---

### Post by Frogs Hair on 2012-08-03
> I AM using GNOME Classic. Gnome shell extensions simply don't work in Gnome Classic and won't appear in the Gnome Tweak Tool.

If you should choose to use the Gnome Shell, I have had good luck with this extension PPA . [http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

---

### Post by Frogs Hair on 2012-08-03
> **wheeze said:**
> GNOME Classic != GNOME Shell

They are not the same, When logging in Gnome = Gnome Shell
 
Gnome Classic and Gnome Classic no effects = Gnome Fallback session , which was intended as a work around for those who like the Gnome 2 style desktop.

---

### Post by wheeze on 2012-08-04
> **Frogs Hair said:**
> They are not the same,...

:rolleyes: That's what != means.

---

### Post by tecknomage on 2012-08-15
Tried an experiment.

[LIST=1]
[*]Purged GNOME Shell
[*]Went to *GNOME Extensions* site and it had a message-bar that said I did not have the current GNOME installed
[*]Reinstalled GNOME Shell
[/LIST]

Still no extensions listed in *GNOME Tweak Tool*, at *GNOME Extensions* site all extensions are greyed out BUT no message-bar (*I assume the site does see I have the correct version of GNOME installed*).

](*,) Any more ideas?

---

### Post by Cheesemill on 2012-08-15
Which session are you choosing fromthe logon screen?
 
[IMG]http://it-diary.com/wp-content/uploads/2012/04/lightdm-unity-greeter-session-chooser.jpg[/IMG]
 
If you are choosing anything except GNOME then Gnome shell extensions will not work.
 
Gnome shell extensions do not work if you are using GNOME Classic or any other session.

---

### Post by 23dornot23d on 2012-08-15
To check ..... and ensure that you are using gnome-shell  open a terminal and type ......        

**gnome-shell --replace**

 (then see if you see a difference)   go to the top left of the screen and another window will open up in here type in 

**settings**

....   choose advanced settings ......  The Tweak tool should then display.  Post a full screen shot of what you see ...... after you do  gnome-shell --replace

__________________________________ if you have any problems ______

make sure all below are installed too ....

[B]sudo apt-get install gnome-shell
sudo apt-get install gnome-tweak-tool
[/B]**sudo apt-get install gnome-shell-extensions**

---

### Post by tecknomage on 2012-08-17
> **Cheesemill said:**
> As I told you earlier, click on the on/off switch in the top left of the web page.
I've annotated my screenshot to make it clearer for you.

When I go to the same page I do not see the option buttons to left.

---

### Post by tecknomage on 2012-08-17
The attached screenshot is where I see **GNOME Shell Extensions** installed.

Could anyone confirm that the location and contents are correct.

---

### Post by tecknomage on 2012-08-23
:redface: Just realized something.

Since installing GNOME I never actually use the 'pure' version. Always use **GNOME Classic**.

Well the **'pure' GNOME** does NOT work. It just shows the background and mouse, nothing else. This is likely why GNOME Extensions do not work.

Since I prefer **GNOME Classic** anyway, I can live without the extensions.

Thanks to those who tried to help ):P

---

### Post by 23dornot23d on 2012-08-23
The naming is confusing - they maybe should have called it something more obvious.

Gnome-Shell ...... does not stand out enough ...... from Gnome

Which was later recalled Classic as it was the old version that is no longer supported now.

But another version was created based on it using a newer code base ...... GNOME 3

Here is a link to the Gnome site ...... 

[http://www.gnome.org/](http://www.gnome.org/)

and video ........

Gnome-Shell-Remix video which is similar to what you had before .....

[http://www.youtube.com/watch?v=VMoYBOZbxQ8](http://www.youtube.com/watch?v=VMoYBOZbxQ8)

Gnome-Shell 3.4 ( which is the newer look )

[http://www.youtube.com/watch?v=9DDfu4Wkebs](http://www.youtube.com/watch?v=9DDfu4Wkebs)

---

### Post by fattyz on 2012-09-18
OMG I have been trying to figure this out for about six months I cant believe it.  So when I select gnome from the login menu I get compiz only.  The cube spins and I can see the skydome but nothing else does this mean I have to stop compiz from loading at startup and how do I do that?

I will not be able to believe it if I actually see the Gnome shell extensions and themes in tweak tool. 

Thanks in advance:P

---

### Post by fattyz on 2012-09-18
Wow I got it.  I tried it a couple more times and finally it loaded.  The website works for extensions and everything. (meaning the f%$#ing little switch appears)  I can't believe it.  That was the worst thing to figure out, I had NO IDEA even after reading that stuff over and over that gnome classic in 12.04 is NOT gnome.  WTF.  Ubuntu is great but it takes ALOT of research and getting used to.

I am going to keep using classic/compiz/emerald since this is seemingly just another way of doing what I'm doing already(?) but it sure was nice to understand this.

Thanks i'm SO glad I found this thread!

---

### Post by cmcanulty on 2012-09-18
Boy did this help me! I kept trying to do extensions and never got the install options, not knowing I had to be in pure gnome, not gnome-classic, thanks.

---

### Post by pinoytechie on 2013-03-02
interesting thread.

several replies say that extensions don't work with gnome shell **classic**, and yet... 

by the way, extensions still don't work with 12.10, gnome shell classic.

---

### Post by eddytheeagle on 2013-06-20
> **23dornot23d said:**
> To check ..... and ensure that you are using gnome-shell  open a terminal and type ......        

**gnome-shell --replace**


Oh man, THANK YOU!!! It took me hours to switch to the shell that uses the extensions :)

---

