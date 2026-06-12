---
title: "HOWTO: create ISO images and burn ISO and AUDIO CD's from terminal"
date: 2011-02-13
forum: General Help
---

### Post by linuxsyst on 2011-02-13
To burn cd from terminal you will need to use wodim. It comes preinstalled, but if you don't have it installed you can install it typing:
```
sudo apt-get install wodim
```
Next thing is to find out the location of the cd/dvd-rw burner in dev folder. Type:
```
wodim --devices
```
The output will be something like this:
[IMG]http://ubuntuhowtos.com/wodim/1.jpg[/IMG]
The underlined part is the location of your cd/dvd burner.Next type:
```
wodim -v -dao speed=4 dev='/sda/scd0' myimage.iso
```
Here's the short explanation:

-v - shows the progress bar
-dao - burn disk at once
speed=4 - determines the speed of burning process
dev='/sda/scd0' - location of your cd burner determined by wodim --device command
myimage.iso - complete path to your iso image

If you don't have iso file ready, you can create one like this. Type:
```
mkisofs -o myimage.iso /path/to/folder/containing/files
```
To burn audio CDs you will need to convert your music to wav. You can do this as follows. Navigate to the folder where are located only those mp3 files that you want to burn to cd, then type:
```
sudo apt-get install mpg123
find . -name "*.mp3" | xargs -i mpg123 -w {}.wav {}
```

Now you will have the .wav files that you can burn to cd. To do this type:

```
wodim -v -dao speed=4 dev='/dev/scd0' -audio *.wav
```

Good Luck

---

