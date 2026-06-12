---
title: "Lirc to control sound"
date: 2011-09-20
forum: General Help
---

### Post by SNIFFER_dog on 2011-09-20
11.04 Natty Narwhal
Lirc 0.9.0

My Lirc and remote are working to control programs

How can I configure .lircrc file to adjust the sound on the laptop just like my sony vaio sound  function keys do?

Any ideas?


Kind regards,

SNIFFY.

---

### Post by SNIFFER_dog on 2011-09-22
Does anyone know what command in the terminal will cause the volume to go up and down using the sony-laptop module? This I believe is talking to the apci?

Basically I am able to use irxevent or irexec for LIRC to do cursor movements. as its a standard keyboard input. But for some reason my sony vaio function keys are not working this way so I was wondering if there is a command that you can use to map these function keys into the .lircrc file to control the volume directly.

I have got the volumesort of working working with this mapping:
```

begin
        prog=irexec
        remote=Hauppauge_350
        button=VOL+
        config=amixer set Master 5%+ > /dev/null
end
 
begin
        prog=irexec
        remote=Hauppauge_350
        button=VOL-
        config=amixer set Master 5%- > /dev/null
end
```but there is no desktop visualization of the  sound changing. It would be nice to see them, and when you change the volume with the vaio sound keys you get it.

Regards

SNIFFY

---

### Post by SNIFFER_dog on 2011-10-19
Just for my own write-up and for those interested, this is how I solved it.

Thanks to this website, and it's author: [http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/](http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/)

I found the information I needed to achieve my goal.

Here's what I did:

First install the package xautomation:
```
sudo apt-get install xautomation
```This allows control of the commands like 'xte key XF86AudioRaiseVolume', 'xte Key XF86AudioLowerVolume' and 'xte Key XF86AudioMute' that will be used later in a bash script.

Create the following bash script in a text editor of you choice, I used gedit:
```

#!/bin/bash
 
gnome-screensaver-command -q | grep inactive
activess=$?
if [ $activess == 1 ]; then
    gnome-screensaver-command -d
fi
 
if [ $1 == "u" ]; then
    xte 'key XF86AudioRaiseVolume'
    rating=0
elif [ $1 == "d" ]; then
    xte 'key XF86AudioLowerVolume'
    rating=0
elif [ $1 == "x" ]; then
    xte 'key XF86AudioMute'
    rating=0
fi
 
if [ $activess == 1 ]; then
    sleep 3s
    gnome-screensaver-command -l
fi
```I believe the first line looks to see if your screen saver has been activated, if so it disables it. Then depending on what your remote inputed, it will either raise, lower or mute your volume. Then the script will wait 3 seconds and then activate the screen saver again. If the screen saver is not active it will run the script leaving the screen saver alone.

Once that's done save the file and then give it executable properties. Hence navigate to the directory the saved file is in and then issue the following command:
```
chmod +x volume-script.sh
```Assuming the files name has been saved as 'volume-script.sh' otherwise substitute the name you saved it as.

Now the file is ready to be treated as a bash script.

The lircd file config is as follows:
```
begin
    prog=irexec
    remote=Hauppauge_350  # Substitute your remote name here and for the ones below
    button=VOL+           # Place your key bind here and for the ones below
    config=~/your-path-to/volume-script.sh u & echo "Master Volume up"
end

begin
    prog=irexec
    remote=Hauppauge_350
    button=VOL-
    config=~/your-path-to/volume-script.sh d & echo "Master Volume Down"
end

begin
    prog=irexec
    remote=Hauppauge_350
    button=Mute
    config=~/your-path-to/volume-script.sh x & echo "Mute Toggle"
end
```The 'your-path-to' bit needs to be substituted with the path to the bash script file. The '~' indicates the home directory. Once that is done it should all work.

Hope that helps someone, if not to remind me in the future.


Regards

SNIFFY

---

