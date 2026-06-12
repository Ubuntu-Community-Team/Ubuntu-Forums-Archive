---
title: "Installing Adobe Flash Player to Ubuntu."
date: 2010-08-02
forum: General Help
---

### Post by Vocapex on 2010-08-02
Hello everyone,

First of all, I want everyone to know that I'm really new to Ubuntu (10.4)as I have only installed it yesterday from a USB stick to my 3 years old laptop. With this message I will try to be as much specific as I can explaining exactly what happens when I'm trying to install Adobe Flash Player.

Soon as I opened the Firefox I tried to see a music video on Youtube.com, on the top of the page writes.."Additional plugins are required to display all the media on this page."and right next to it a box which writes.."Install Missing Plugins..".
When Im pressing the button the Plugin Finder Service box comes out and asks me to 

"Chooses a plugin for media type application/x-shockwave-flash: 
1.Adobe Flash Player (Installer) 
2.Swfdec SWF player
3.Gnash SWF player

..when Im choosing 1.Adobe Flash Player, another window comes out saying..

"Completing The Plugin Finder Service.
No plugins were installed.
Adobe Flash Player (Installer) Failed."

Then I press finish.


Second thing that I tried,

On the top of the Youtube screen that I supposed to watch the video writes.."You need to upgrade your Adobe Flash Player to watch this video." and under this has a link "Download it from Adobe"

As the link takes me to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) it asks me to select the version that I want to download. I tried downloading the .deb for Ubuntu 8.04+ and a window comes out telling me "what should Firefox do with this file?" 
1.Open with GDebi Package Installer. (default)
2.Save file.
I choose the first and then the package installer comes out and the downloads with this "install_flash_player_10_linux.deb", then the screen is changing to grey and after a bit i get this message..

"Software index is broken.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I'm looking at my downloads and there is nothing that has been just or ever downloaded.

I would be grateful if someone could help me with this.
Looking forward hearing your ideas.

V.

---

### Post by Smart Viking on 2010-08-02
Hey, write this into the "terminal", press enter and then write your password:

```
sudo apt-get install ubuntu-restricted-extras
```

after that, restart firefox and flash will be installed. :)

---

### Post by snowpine on 2010-08-02
I would recommend 

1. Fully update your system using the Update Manager or the following terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If there are any error messages, stop, copy & paste them back here, otherwise proceed...

2. Install Flash using the Ubuntu Software Center (your one-stop source for trusted and tested applications) or the terminal command:

```
sudo apt-get install flashplugin-installer
```

3. Restart Firefox.

---

### Post by Vocapex on 2010-08-02
Thank you very much for your quick replies.

i tried all things you guys said but it didnt worked another thing that might help you realise the problem is that when I start my computer there is a list of lines coming out saying "error" but now im not sure what exaclty the say because i cannot pause it and see. 

I was considering installing again Ubuntu.
or even formating all the computer.

 Please let me know what you are thinking.


V.

---

### Post by snowpine on 2010-08-02
A fresh reinstall might be a good idea; I had to reinstall a bunch of times when I first discovered Ubuntu, but each time was a good learning experience. :)

---

### Post by Smart Viking on 2010-08-02
> **snowpine said:**
> A fresh reinstall might be a good idea; I had to reinstall a bunch of times when I first discovered Ubuntu, but each time was a good learning experience. :)

Yes, i have been using Linux for a while now but i still install about every week, not because i have to but because i try different distros, screw things up, just for fun ect...

A linux install is quick and painless, and you learn much that way too. :)

---

### Post by Vocapex on 2010-08-02
Kool, I will to the same.

I got one more question,
Do all files and all information get erased when Im installing Ubuntu?
I dont wanna have anything in my computer since im doing a fresh start. 

V.

---

### Post by Smart Viking on 2010-08-02
> **Vocapex said:**
> Kool, I will to the same.

I got one more question,
Do all files and all information get erased when Im installing Ubuntu?
I dont wanna have anything in my computer since im doing a fresh start. 

V.

If you have a seperate /home directory than you have the "option" to not format it, which means you will keep your files, but if you format everything then you will not keep any files, it will be a completely new start. :)

---

### Post by snowpine on 2010-08-02
> **Vocapex said:**
> Do all files and all information get erased when Im installing Ubuntu?

Correct. The installer will give you several partitioning options, including the option to replace your existing Ubuntu partition. Do you want to give Ubuntu the whole drive, or are you dual booting?

---

### Post by SunnyRabbiera on 2010-08-02
> **Vocapex said:**
> Kool, I will to the same.

I got one more question,
Do all files and all information get erased when Im installing Ubuntu?
I dont wanna have anything in my computer since im doing a fresh start. 

V.

Just reformat the drive, it should do the trick for the most part.

---

### Post by Vocapex on 2010-08-02
Yesterday at my first install i gave all the drive to Ubuntu, Im going the same tomorrow.
Once reinstall Ubuntu, will all information be deleted?
To my understanding..my computer will be as new. right?

---

### Post by snowpine on 2010-08-02
> **Vocapex said:**
> Yesterday at my first install i gave all the drive to Ubuntu, Im going the same tomorrow.
Once reinstall Ubuntu, will all information be deleted?
To my understanding..my computer will be as new. right?

Yes; give it the whole disk and it will erase everything!

Next time, you will know the answer how to install Flash. :)

---

### Post by Smart Viking on 2010-08-02
> **Vocapex said:**
> Yesterday at my first install i gave all the drive to Ubuntu, Im going the same tomorrow.
Once reinstall Ubuntu, will all information be deleted?
To my understanding..my computer will be as new. right?

Yes, if you mark the drive to be formatted(if you choose the option to erase and use the whole disk, that will do it for you), then everything will be deleted, and your good to go. :)

---

### Post by Vocapex on 2010-08-02
Thank you all for you help!

;)

---

### Post by Vocapex on 2010-08-03
I reinstalled Ubuntu and this time i did download Adobe FLash Player from the link in Yotube.com and t works.

Thanks again!

---

### Post by Cavsfan on 2010-08-03
Man you probably could have just download lovinglinux's FF Flash addon from [[COLOR=blue]_here._[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/161939/")
You still can and it will keep your flash up to date.

Also, you may notice YouTube videos pause, stop, etc. buttons do not work and here is the fix if that happens to you:

[B]gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
[/B]
Then add: "**export GDK_NATIVE_WINDOWS=1**" before the last line of text
(without the quotes).

Save it and restart browser.

---

### Post by Vocapex on 2010-08-03
Thank you for the tips!

---

### Post by Cavsfan on 2010-08-03
> **Vocapex said:**
> Thank you for the tips!

If you mean me, you are very welcome! There are many kind people in this forum 
ready to help! There is always a way and a solution to every problem. 
I think some of the smartest minds that exist are in this forum.

---

