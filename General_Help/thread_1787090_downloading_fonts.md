---
title: "downloading fonts"
date: 2011-06-20
forum: General Help
---

### Post by linux-l-lhead on 2011-06-20
This is probably a beginner question, but...  I'm looking for the font "University Roman".  We have an Epson printer and use Linux.  I see lots of sites for downloading fonts - some charge and some don't.  Web searches seem to indicate that you pay for fonts, one way or the other - either up front or via "readers".  I'm more concerned about viruses than cost.  Any thoughts or suggestions?  Thanks.

---

### Post by jerrrys on 2011-06-20
[http://packages.ubuntu.com/maverick/ttf-ubuntu-font-family](http://packages.ubuntu.com/maverick/ttf-ubuntu-font-family) has free ones.  the complete listing only seems to appear in synaptic package manager.

you running natty?

[http://packages.ubuntu.com/natty/ttf-ubuntu-font-family](http://packages.ubuntu.com/natty/ttf-ubuntu-font-family)

there must be a couple of hundred fonts in synaptic

[ATTACH]195611[/ATTACH]

---

### Post by linux-l-lhead on 2011-06-20
Jerry - I missed whatever you took back, but thanks for whatever you said...

Because I'm new to this, I don't know if it's OK to ask about the site fontineed.com.  They have a facebook page - does that make them legit?

---

### Post by Rasa1111 on 2011-06-20
No, having a facebook page does not make them "legit".

Anyway,
Is this the font you need?
[http://www.fontcubes.com/University-Roman-Normal.font](http://www.fontcubes.com/University-Roman-Normal.font)

I just downloaded/installed it, just to see..
and it's fine.

So if that's what you need, grab it up. 

After you download it, Just double click the TTF file, and when the font window opens,
Just click "Install". 

good luck.

---

### Post by jerrrys on 2011-06-20
the site itself seems fine to me.  did you read the about page?  anyone with a font can post to this site so let the buyer beware

---

### Post by Cheesehead on 2011-06-20
Well, most viruses will not work or propagate in Linux - they are intended for other platforms. You can always run ClamAV for additional peace of mind. Someday the situation may be different, but right now you're reasonably safe with Linux.

Any free legit fonts will be in recognizable common formats, like .ttf. If you don't recognize the format, you may not be able to install it anyway.

If you don't know how to install fonts manually, here is one way that is safe and easy to understand. If you're not a fan of shell commands, then just pay attention to the comments:
```
# Extract your font from the zip file
mkdir ~/Stuff-I-have-Installed                                 # Good practice, keep track of your changes
mv ~/Desktop/downloaded-fonts.zip ~/Stuff-I-Have-Installed/    # Move the zip into the directory
unzip ~/Stuff-I-Have-Installed/downloaded-fonts.zip            # Unzip it
ls ~/Stuff-I-Have-Installed/                                   # Check the result of the unzip
downloaded-fonts.zip NEWFONT.TTF
rm ~/Stuff-I-Have-Installed/downloaded-fonts.zip               # Don't need the zip anymore

# For user-level use (try this first)
if [ ! -d ~/.fonts ]; then mkdir ~/.fonts; fi                  # If there is no user-level ~/.fonts folder, then create one
ln -s ~/Stuff-I-Have-Installed/NEWFONT.TTF ~/.fonts/           # Put a link to the font in the fonts folder

# Once you are satisfied that the font is ready for system-level (multi-user) use
rm ~/.fonts/NEWFONT.TTF                                        # Remove the user-level link. You don't need it anymore.
if [ -s ~/.fonts ]; then rmdir ~/.fonts; fi                    # Remove the user-level ~/.fonts directory if it's empty
sudo chown root ~/Stuff-I-Have-Installed/NEWFONT.TTF           # Change the owner and file permissions for system use
sudo chgrp root ~/Stuff-I-Have-Installed/NEWFONT.TTF
sudo chmod 755 ~/Stuff-I-Have-Installed/NEWFONT.TTF
sudo ln -s ~/Stuff-I-Have-Installed/NEWFONT.TTF /usr/bin/fonts/truetype/  # Link the font to the appropriate system folder.

```

---

### Post by jerrrys on 2011-06-20
i did not mean to imply viruses.  have not seen any of that, but there is a lot of poorly design thirdparty-ware

---

### Post by Rasa1111 on 2011-06-20
He said he was a noob..
why make things more difficult/confusing than they need to be?

2 very simple ways to install fonts, neither requiring the terminal/command line.

1. double click .ttf file, and click the "Install" button when it appears.

2. drag .ttf files into your .fonts folder, within your home folder. 
If you do not already have a .fonts folder in your home directory, 
simply create one. 

the . (.period) before the folder name means it will be hidden. 
So press Ctrl H to show hidden files/folders. 

Once hidden folders are visible, If you see a **.fonts** folder, you're good to go, and can just drag your font files into the folder. 

If you don't see a **.fonts** folder 
simply right click an empty space in your home folder, and "create new folder"
name it *.fonts, *and hit enter. But none of this should be necessary if you have already installed at least one font already. 
The moment you install your first font, (by method 1.), it creates a .fonts folder for you. 

So you shouldnt have to do anything but # 1.

Double click font, click "Install", font is installed, done.

---

### Post by Cheesehead on 2011-06-20
Double-click on fonts to install?
Nifty. Always a new feature to amaze us old-timers.

Yet I stand by the basic procedure of keeping customizations in one place in the home folder and linking out - that way the originals (and your notes) get backed up. Had to reinstall from /home-only backups a couple times in 10 years, and it really paid off to have all the reconstruction material in one place. You aren't required to...but it's best practice.

Being able to document and reconstruct what you did is still an important skill. Noobs gotta learn that skill, too - noobs hose their systems sometimes.

---

### Post by linux-l-lhead on 2011-06-20
Thanks SO much.  yeah, I've got lots to learn and you've helped - a lot.  I'm going to try to take it from here (and will post this as "resolved" as soon as I figure out how to).

You guys are the best!

---

### Post by linux-l-lhead on 2011-06-21
What is wrong?  When I try to install the font I get the message:

file://tmp/kde-____/arkf7mSQc//UNIVERSI.TTF is not a font.

It installed fine on a Windows laptop, which is a temporary back-up that I don't want to use.  I want the font on my computer.  Is something blocking?

---

### Post by jerrrys on 2011-06-21
try this

sudo apt-get install ttf-mscorefonts-installer

---

