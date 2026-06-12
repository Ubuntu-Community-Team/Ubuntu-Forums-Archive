---
title: "Is this installation command correct?"
date: 2012-04-30
forum: General Help
---

### Post by GameX2 on 2012-04-30
Hi,


I'm going to reinstall Ubuntu 12.04 LTS soon; It's working great, but maybe I've put the mess and I can't get VMware to work proprely.  Instead of uninstalling and trying again, maybe it'll be more clean to do another reinstalltion.

I'm trying to do this as productive and quick as possible.  I exported my Compiz configuration, and I'm going to launch this command, to install nearly all my softwares in a single line (I love you Linux)!

```
sudo apt-get remove gnome-screensaver & shotwell & simple-scan & thunderbird & vino & remmina & remmina-common && sudo add-apt-repository ppa:danielrichter2007/grub-customizer && sudo add-apt-repository ppa:tualatrix/ppa && sudo add-apt-repository ppa:cinelerra-ppa/ppa && sudo apt-get update && sudo apt-get install -y grub-customizer & ubuntu-tweak & cinelerra & p7zip & p7zip-full & pzip7-rar & clamtk & pysdm & screenlets & screenlets-pack-all & evolution & verbiste-gnome & gimp & pinta & chromium-browser & wine1.4 & playonlinux & audacity & cheese & minitube & winff & alacarte & compizconfig-settings-manager & gparted & gufw & gconf-editor & mplayer & synaptic & xscreensaver & xscreensaver-gl-extra & xscreensaver-data-extra & xscreensaver-screensaver-bsod & devilspie & gdevilspie & bleachbit & lame & clementine
```

Is the line correct?  It's really necessary to put "&" everywhere?  I would like to install all these softwares without any confirmation (Well, one or 2 it's fine, but not 30..).

I'm not too sure about this part:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer && sudo add-apt-repository ppa:tualatrix/ppa && sudo add-apt-repository ppa:cinelerra-ppa/ppa && sudo apt-get update
```

I'm adding 3 PPA at the same time..  Is the structure correct?


Last question - using the command:

```
sudo apt-get install wine1.4
```
Will install Wine 1.4, and all of his dependancies, right?  Like Winetricks?  Is this completely similar to installing Wine from the Software center?


Thanks for your advice!

---

### Post by pqwoerituytrueiwoq on 2012-04-30
you can separate command with a semi-colon [noparse](;)[/noparse] i find it much easer than dealing with the & symbols
you could also make a bash script and have then on separate lines

---

### Post by GameX2 on 2012-04-30
Allright, so from what I've read here: [http://www.comptechdoc.org/os/linux/manual2/runningcommands.html](http://www.comptechdoc.org/os/linux/manual2/runningcommands.html)

Using a ";" - which is better in my case - : The command is executed in the order it was written, but command 2 is executed even if there was an error in command 1.

As for using "&" : The command command2 is executed only if command1 was successful, no errors.

```
sudo apt-get remove gnome-screensaver & shotwell & simple-scan & thunderbird & vino & remmina & remmina-common ; sudo add-apt-repository ppa:danielrichter2007/grub-customizer ; sudo add-apt-repository ppa:tualatrix/ppa ; sudo add-apt-repository ppa:cinelerra-ppa/ppa ; sudo apt-get update ; sudo apt-get install -y grub-customizer & ubuntu-tweak & cinelerra & p7zip & p7zip-full & pzip7-rar & clamtk & pysdm & screenlets & screenlets-pack-all & evolution & verbiste-gnome & gimp & pinta & chromium-browser & wine1.4 & playonlinux & audacity & cheese & minitube & winff & alacarte & compizconfig-settings-manager & gparted & gufw & gconf-editor & mplayer & synaptic & xscreensaver & xscreensaver-gl-extra & xscreensaver-data-extra & xscreensaver-screensaver-bsod & devilspie & gdevilspie & bleachbit & lame & clementine
```

So this seems to be the most trouble-free way to do it. :)
Please correct me if something's wrong in the command!

(Have to say I never did a bash script, so I have no idea where to start XP)

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-04-30
```
sudo apt-get remove gnome-screensaver & shotwell & simple-scan & thunderbird & vino & remmina & remmina-common
```
no & needed in that

---

### Post by Cheesemill on 2012-04-30
Instead of doing it all on one line I'd put it in a script to make it more readable:
```
#!/bin/sh
apt-get remove gnome-screensaver shotwell simple-scan thunderbird vino remmina remmina-common
add-apt-repository ppa:danielrichter2007/grub-customizer
add-apt-repository ppa:tualatrix/ppa
add-apt-repository ppa:cinelerra-ppa/ppa
apt-get update
apt-get install -y grub-customizer ubuntu-tweak cinelerra p7zip p7zip-full pzip7-rar clamtk pysdm screenlets screenlets-pack-all evolution verbiste-gnome gimp pinta chromium-browser wine1.4 playonlinux audacity cheese minitube winff alacarte compizconfig-settings-manager gparted gufw gconf-editor mplayer synaptic xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod devilspie gdevilspie bleachbit lame clementine
```
Save the above as installscript.sh
Make it executable:
```
chmod +x installscript.sh
```
Then to run it:
```
sudo ./installscript.sh
```

---

### Post by GameX2 on 2012-04-30
> **Cheesemill said:**
> Instead of doing it all on one line I'd put it in a script to make it more readable:
```
#!/bin/sh
apt-get remove gnome-screensaver shotwell simple-scan thunderbird vino remmina remmina-common
add-apt-repository ppa:danielrichter2007/grub-customizer
add-apt-repository ppa:tualatrix/ppa
add-apt-repository ppa:cinelerra-ppa/ppa
apt-get update
apt-get install -y grub-customizer ubuntu-tweak cinelerra p7zip p7zip-full pzip7-rar clamtk pysdm screenlets screenlets-pack-all evolution verbiste-gnome gimp pinta chromium-browser wine1.4 playonlinux audacity cheese minitube winff alacarte compizconfig-settings-manager gparted gufw gconf-editor mplayer synaptic xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod devilspie gdevilspie bleachbit lame clementine
```
Save the above as installscript.sh
Make it executable:
```
chmod +x installscript.sh
```
Then to run it:
```
sudo ./installscript.sh
```

Thanks you very much. ;)
It's also more useful, since I can always add content to the script, if I need to!

Amazing that I can do this operation automatically, something that would take all day long on Windows (Find the software.  Download the software.  Install the software. :P)!

Solved. ;)

---

### Post by GameX2 on 2012-04-30
Blown away!
That's just nonsense! :O

Installation took 15-20 minutes, then reinstalling all those packages (1,2 GB in size) took like.. 10 minutes?!
I thought it was going to take like an hour!

Manually downloading all these softwares from the Software Center would have took hours!
Total genius.  Why Linux is AWESOME! :O

---

