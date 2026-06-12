---
title: "tom.swartz07 Custom Conky Desktop!"
date: 2010-01-29
forum: General Help
---

### Post by tom.swartz07 on 2010-01-29
Over the past few weeks, Ive received quite a few compliments about my desktop and even more requests about how to create the same look. Ive decided to write up a How-To highlighting each aspect of my desktop.

[B]*[U]Before I begin, I would like to point out that I have all of this code, pre-compiled and ready to download from my Launchpad BZR page.* [https://code.launchpad.net/~tom-swartz07/+junk/main](https://code.launchpad.net/~tom-swartz07/+junk/main)

Follow the instructions on the site to grab all of my files mentioned here (with the exception of Conky). [COLOR="Red"]These will be the most up-to-date versions of the files!!!![/COLOR][/U][/B]

First up: **_[SIZE="4"]The Backgrounds[/SIZE]_**


[CENTER]**[SIZE="3"]Bing Wallpaper[/SIZE]**

[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Szlhf10IO-I/AAAAAAAAAKM/DZEXzJaomp4/s800/Screenshot.png[/IMG][/CENTER]

With the help of a few other scripts, I was able to patch together a program to grab the background image from Bing.com and set it as your wallpaper. In order to set this up, you need to add the following script to your home folder and then add it to your startup applications. 

To do this, you could save the script as .bing_changer.sh in your Home folder. Note the period at the beginning of the filename- this will assure that the file is normally 'hidden' from your usual view. Now, to add the program to startup, simply navigate to system>preferences>startup applications. Pick a name for the process, and then in the 'command' field- click "browse" and select it from your home folder (you may need to hit CTRL + H to see the hidden file)


Now the script: ```
#!/bin/bash
# bing wallpaper downloader by YoungJesus, 2009. 
# based on Siddharth Prakash Singh (http://www.spsneo.com/blog) php bing wallpaper downloader

# modify this, if you want to save to other place
#  - $HOME: your home dir
#  - %F: full date (%Y-%m-%d)
#  - other date format: man date :P
OUTPUT=`date "+$HOME/Pictures/bing/bing_bg.%F.jpg"`

# get the bing.com page, and separate the background image (DONT touch this)
IMG=`wget -q http://www.bing.com -O- | sed -r "s/[\]//g;s/.*g_img=\{url:'([^']+)'.*/\1/gp;d"`

# get the background image to the output (DONT touch this)
wget -q "http://www.bing.com$IMG" -O "$OUTPUT"
# error handle
if [ $? -gt 0 ]; then
	echo "there is a problem with downloading.."
	exit 1
fi

# setup the background
gconftool-2 -s -t string /desktop/gnome/background/picture_filename "$OUTPUT"
# set the background position
#gconftool-2 -s -t string /desktop/gnome/background/picture_options "centered"
# set the background color
#gconftool-2 --type string --set /desktop/gnome/background/primary_color "black"

exit 0
```


[CENTER]**[SIZE="3"]World View Desktop[/SIZE]**

[IMG]http://lh5.ggpht.com/_tORug_uHNu4/S2HF281EUFI/AAAAAAAAAM8/YxSg_cmYWP0/s800/Screenshot.png[/IMG][/CENTER]

This is one script that I am particularly pleased with. I currently use it as my background and have spent quite a bit of time tweaking it and optimizing it. This script also follows the same idea as the Bing changer in that it takes an image from a website and sets it as your wallpaper. This script differs in the fact that it repeats the process every 5 to 10 minutes giving you a 'live' view of the Earth. As far as memory and CPU consumption- on my system, it only uses around 2mb of RAM and practically no CPU.

Setup for this script is the same. Save the code to your home folder, and add it to your startup applications. This will run by itself in the background and keep your background up to date. The image is saved in ~/.gnome2, you could add it from there.

Heres the code: ```
#!/bin/bash
#Live View Wallpaper Changer. Created by Thomas Swartz 2009/2010
cd ~/.gnome2/
while [[ 1 ]]; do
	COUNTER=0
	while [[ COUNTER=$[ $COUNTER + 1 ] -lt 60 ]]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		if [[ $(file world.jpg | grep JPEG) ]]; then
			mv world.jpg world_sunlight_Wallpaper.jpg
			break
		fi
		sleep 5
	done
	sleep 300
done
```


Next- **_[SIZE="4"]Conky![/SIZE]_**

[CENTER][SIZE="3"]**My Conky**[/SIZE][/CENTER]

I originally was inspired to use conky when I saw a post on Lifehacker: [http://lifehacker.com/5067341/customize-conky-for-ambient-linux-productivity](http://lifehacker.com/5067341/customize-conky-for-ambient-linux-productivity)

This was the original post that inspired me to create what is now my current conky desktop. Its absolutely stunning: [http://lifehacker.com/5068294/beautifully-minimalist-conky-setup](http://lifehacker.com/5068294/beautifully-minimalist-conky-setup)

Since then, both the programming of conky and my skills have grown. I use a number of small scripts to keep up to date with useful information about my system. Programs such as lm-sensors, and a few customized scripts help make my conky look the way it does.


[COLOR="Red"]I use Dropbox to keep all of my files synced. Its a free service that allots 2GB of storage to you, letting you sync files to any computer- much like an internet based USB key. Theres a link in my signature to get Dropbox if you dont already have it. I would highly recommend that you keep all of the conky files there; they are small enough to keep synced, yet make such a great difference when you are missing them![/COLOR] You could get Dropbox here: [_[COLOR="RoyalBlue"]DROPBOX[/COLOR]_]("http://tinyurl.com/yeee6od")

To use my conkyrc file (a simple script that tells conky what to show on your desktop) you need to set up a few simple things first. 

First, lets get all of the dependent files. In a terminal (applications>accessories>terminal) type the following ```
sudo apt-get install lm-sensors
``` Once its installed, you need to set it up- majority of the time, you could just run ```
sudo sensors-detect
``` and hit Y for all of the questions. 
Once you have sensors enabled, you could test it - ```
sensors -f
``` will give you your computer's temperature in Fahrenheit. 

Now you need to install some sweet fonts. In your home folder, you will need to create a folder titled .fonts (again, a period in front so its hidden). You might already have one, if so just go there. In the attached file here, there is a zip file with fonts- simply copy them from the archive to your .fonts folder. 

Now for the conky setup. If you dont already have conky installed, get it by ```
sudo apt-get install conky
``` Copy the .conkyrc file to your home folder, and you should be 90% of the way there. Edit the .conkyrc file to point to the locations of the other files (scripts, email passwords, etc) this will allow conky to check your email (securely, and read-only) and report if you have any new messages. 

Here are all of the files you need to get started: 
[http://dl.dropbox.com/u/1864354/Shared%20Conky.zip](http://dl.dropbox.com/u/1864354/Shared%20Conky.zip)

Finally: [CENTER][SIZE="4"]**DOCKS!!**[/SIZE][/CENTER]

Many people comment about my neat looking docks. I use a combination of Avant Window Navigator and Docky. Unfortunately, neither of the versions I use are available from the standard Software Center. You could add them from these sources if youre using Karmic;

For Avant Window Navigator (trunk): ```
sudo add-apt-repository ppa:awn-testing/ppa
```
For Docky: ```
sudo add-apt-repository ppa:docky-core/ppa
```

Then update your system and add them from Synaptic package manager. The files you need for AWN are all labeled with 'awn-trunk', there are quite a few, so make sure you get them all. 
AWN has some really neat features; including a Pandora Radio applet and a Media Player applet that changes the look of the whole dock when you click to use it: 
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/S2HK32kQrAI/AAAAAAAAANE/y3dTW7_oA4o/s800/Screenshot-1.png[/IMG]

To install Docky, simply run ```
sudo apt-get install docky
```



Last but not least, I should mention that if you are really looking to get under the hood of your Ubuntu system, you could install the program Ubuntu Tweak. Available here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
This will allow you to get in and tweak some really cool things about your system that would normally take some serious command line work.


Other than that, I think Ive covered pretty much everything about my desktop so far! If you have any questions or concerns about anything mentioned here, PLEASE let me know!

Thanks again for all of the compliments and praise about my computer. I really spent a lot of time working on it and it truly means a lot to me. :D

Rock on!

~Tom

---

### Post by raktarok on 2010-01-29
Thanks for all of this, I needed that conky!

---

### Post by tom.swartz07 on 2010-01-29
> **raktarok said:**
> Thanks for all of this, I needed that conky!

Sure thing! I know you and at least 3 others were looking for this within the past week! haha

---

### Post by egalvan on 2010-01-29
One more conky page to add to my ever-growing collection of all things conky.

Many Thanks for Sharing!

---

### Post by tom.swartz07 on 2010-01-29
> **egalvan said:**
> One more conky page to add to my ever-growing collection of all things conky.

Many Thanks for Sharing!

Sure thing! Glad you like it!

---

### Post by Jordanwb on 2010-02-04
That world view looks awesome. *Yoink!*

[Edit]

Okay, so I added it to the startup apps, made the script executable and restarted my PC. In the script I saw that it renamed the jpg to world_sunlight_Wallpaper.jpg, but I could never find that file in my ~/ folder.

---

### Post by darco on 2010-02-04
> **Jordanwb said:**
> That world view looks awesome. *Yoink!*

[Edit]

Okay, so I added it to the startup apps, made the script executable and restarted my PC. In the script I saw that it renamed the jpg to world_sunlight_Wallpaper.jpg, but I could never find that file in my ~/ folder.

the wallpaper gets dumped in the ' ~/.gnome2/' per the script.

---

### Post by tom.swartz07 on 2010-02-04
> **darco said:**
> the wallpaper gets dumped in the ' ~/.gnome2/' per the script.

Forgot about that! its fixed now.

Thanks for pointing that out, you two!

---

### Post by Jordanwb on 2010-02-04
I added this directly after the move:

```
notify-send "The Wallpaper has been updated" -i /usr/share/icons/gnome-colors-common/32x32/apps/gnome-display-properties.png -t 5000
```

You need libnotify-bin

---

### Post by tom.swartz07 on 2010-02-04
> **Jordanwb said:**
> I added this directly after the move:

```
notify-send "The Wallpaper has been updated" -i /usr/share/icons/gnome-colors-common/32x32/apps/gnome-display-properties.png -t 5000
```

You need libnotify-bin

Thats a pretty cool little tweak!
Personally, I wouldnt use it because it would pop up every 5 minutes when the image is updated, but its a definite cool tweak nonetheless!

---

### Post by tom.swartz07 on 2010-02-05
Just as a Heads-Up, I fixed the offending file. I had inadvertently left my email address and password in the file, as the archive didnt update properly when I edited it.

Conky source files are back up.

---

### Post by Jordanwb on 2010-02-05
> **tom.swartz07 said:**
> Thats a pretty cool little tweak!
Personally, I wouldnt use it because it would pop up every 5 minutes when the image is updated, but its a definite cool tweak nonetheless!

That's Fine.

> **tom.swartz07 said:**
> Just as a Heads-Up, I fixed the offending file. I had inadvertently left my email address and password in the file, as the archive didnt update properly when I edited it.

Conky source files are back up.

I'll have to give that script a try.

---

