---
title: "How can I have multiple conky themes?"
date: 2012-03-21
forum: General Help
---

### Post by Spewed on 2012-03-21
Hi,

I'm trying to figure out how to have multiple conky themes running harmoniously with each other. I've tried various ways and nothing seems to work. 

I'm currently using the Gotham conky config [http://browse.deviantart.com/?qh=&section=&q=gotham+conky#/d3ebu4r]("http://browse.deviantart.com/?qh=&section=&q=gotham+conky#/d3ebu4r")

And would like to use the MNM Conky config WITH Gotham. 
[http://browse.deviantart.com/?qh=&section=&q=gotham+conky#/d3ie7uc]("http://browse.deviantart.com/?qh=&section=&q=gotham+conky#/d3ie7uc")

The MNM link says to extract all of the files to the ".conky" folder that I have in my home direction---I don't have a folder with such a name and never created one. I tried to create one, and put both the Gotham and MNM config files into it, and then got the default conky theme(which is rather ugly). So I took out the Gotham ".conkyrc" individual files and placed them in my home folder without having a subfolder in between, this brings back my Gotham Config. So I try simply doing the same with the MNM config, and nothing happens after refreshing conky. 

So, what should I do in this case? I've also tried combining the text files together and that doesn't work either. :|

---

### Post by stinkeye on 2012-03-21
If you want to use multiple conkys, start your conkys with
```
conky -c /path/to/conkyconfig
```
You can name your configs anything you want and save where you like.

Running just **conky** in the terminal will load only one specific config.
ie **~/.conkyrc**.


This is my conky start script (Needs to be executable...Rclick on file Properties > permissions and mark execute.)
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 	killall conky 
else
 	conky -c ~/conky/conkytimer &
sleep 1
 	conky -c ~/conky/conkygmail &
sleep 3
 	conky -c ~/conky/conkysb &
sleep 5
 	conky -c ~/conky/conkysro &
sleep 3
 	conky -c ~/conky/rottoswellmini &
sleep 8
 	conky -c ~/conky/conkycal
fi
```

It can be used to toggle conky on/off and
as your startup script.
eg I have this script saved as **toggleconky** in my **~/conky** folder
and to use in startup applications with a delay to allow the desktop to load
I use...
```
sh -c "sleep 15 && ~/conky/toggleconky"
```

---

### Post by HiImTye on 2012-03-21
here's mine, it starts conky, deletes some files I don't need, starts pulseaudio, etc
```
#!/bin/bash
if [ -f $HOME/bash_history ]
then rm $HOME/bash_history
fi
if [ -d $HOME/.thumbnails/fail ]
then rm -R $HOME/.thumbnails/fail
fi
cp $HOME/Launchers/.asoundrc_pulsealsa $HOME/.asoundrc
pulseaudio --start
if [ ! -z "$1" ]
then sleep 25
fi
killall conky
conky -a bm -x -20 -y 170 -d -c$HOME/Launchers/.conkyrc-time &
conky -a br -x 40 -y 0 -d -c$HOME/Launchers/.conkyrc-cpu &
conky -a bl -x 40 -y 0 -d -c$HOME/Launchers/.conkyrc-memory &
conky -a br -x 40 -y 400 -d -c$HOME/Launchers/.conkyrc-netup &
conky -a bl -x 40 -y 400 -d -c$HOME/Launchers/.conkyrc-netdown &

# ** disabled **
#conky -a br -x 80 -y 0 -d c$HOME/Launchers//.conkyrc-music &

exit
```to start it with a delay, I just pass it a variable, for instance:
```
/home/mine/Launchers/tconk.sh 1
```
otherwise it starts immediately (for instance, if I double click on it)

---

### Post by Spewed on 2012-03-21
> **stinkeye said:**
> If you want to use multiple conkys, start your conkys with
```
conky -c /path/to/conkyconfig
```
You can name your configs anything you want and save where you like.

Running just **conky** in the terminal will load only one specific config.
ie **~/.conkyrc**.


This is my conky start script (Needs to be executable...Rclick on file Properties > permissions and mark execute.)
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 	killall conky 
else
 	conky -c ~/conky/conkytimer &
sleep 1
 	conky -c ~/conky/conkygmail &
sleep 3
 	conky -c ~/conky/conkysb &
sleep 5
 	conky -c ~/conky/conkysro &
sleep 3
 	conky -c ~/conky/rottoswellmini &
sleep 8
 	conky -c ~/conky/conkycal
fi
```

It can be used to toggle conky on/off and
as your startup script.
eg I have this script saved as **toggleconky** in my **~/conky** folder
and to use in startup applications with a delay to allow the desktop to load
I use...
```
sh -c "sleep 15 && ~/conky/toggleconky"
```


Let me try and get this straight. 

By typing "conky" in the terminal I run my Gotham config, so if I want to run any other config I simply put it anywhere I want for example, in my home folder with a subfolder of ".conky" I simply would type 

conky -c ~/conky/conkytimer and that would run the other config? Except I would replace conkytimer with my configs name?

or, do I put this in the text files of my conky configs before they run?
conky -c /path/to/conkyconfig[/CODE]

Sorry, it's a little bit jibberish to me.

---

### Post by HiImTye on 2012-03-21
you call your other conky config with the -c option so, for instance, if you had two configs in ~/conkyscripts/ one named conky1 and the other named conky2 you would do something like:
[FONT=monospace][/FONT]```
conky -c$HOME/conkyscripts/conky1 &
conky -c$HOME/conkyscripts/conky2 &
```
and it would load both (basically) simultaneously

---

### Post by stinkeye on 2012-03-21
Most people only package these conkys up into folders like .conky and tell you to put
them in your home folder because they are calling included scripts.
This maintains the path to the script which is written in the conky.

Your MNM conky folder actually contains 2 separate conky configs...
**conkyrc-line** and **conkyrc-mpd**

The conkyrc-mpd will show data from the Music Player Daemon program
which is not in the default install and your probably not using anyway,
so we can disregard this config.

Now if you open with gedit the conkyrc-line config you will see a section below "TEXT" 
```
${execi 600 ~/.conky/gmail.py}
```
So you see it's calling the included **gmail.py** script from **~/.conky**
This is the reason you have been told to install here.

You can place your configs and scripts anywhere you like as long as the paths to call the scripts are correct.

The Gotham conky doesn't call any scripts so is just a standalone config 
which can be saved anywhere without having to edit.

To keep things organized I just put all my conky downloads into a  **~/conky** folder and then edit the path to any scripts.

 It's also helpful to rename the configs to something easily recognized.
eg the **.gothamconkyrc** I renamed to **dateconky**.

> By typing "conky" in the terminal I run my Gotham config, so if I want to run any other config I simply put it anywhere I want for example, in my home folder with a subfolder of ".conky" I simply would type 

 conky -c ~/conky/conkytimer and that would run the other config? Except I would replace conkytimer with my configs name?



Yes, the **-c** option tells conky to run that particular config
instead of the default **~/.conkyrc** file.
```
conky -c [COLOR="DarkOrange"]/path/to/conkyconfig[/COLOR]
```
Replace with **your** [COLOR="darkorange"]path to conkyconfig[/COLOR].

Test in the terminal 
and then use a startup script
eg
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 	killall conky 
else
 	conky -c [COLOR="DarkOrange"]/path/to/conkyconfig1[/COLOR] &
sleep 1
 	conky -c [COLOR="DarkOrange"]/path/to/conkyconfig2[/COLOR] &

fi
```

NB*** A dot in front of a file or folder makes it hidden(ctrl+h to show) 
**~/.conky** is a different folder to **~/conky**
Important when writing paths.

An easy way to get the correct paths is to go to the file in the file browser and right click on it and select copy.
You can now just paste into text editors.
For pasting into the terminal use the **Paste Filenames** Rclick option.

---

### Post by Spewed on 2012-03-21
> **stinkeye said:**
> Most people only package these conkys up into folders like .conky and tell you to put
them in your home folder because they are calling included scripts.
This maintains the path to the script which is written in the conky.

Your MNM conky folder actually contains 2 separate conky configs...
**conkyrc-line** and **conkyrc-mpd**

The conkyrc-mpd will show data from the Music Player Daemon program
which is not in the default install and your probably not using anyway,
so we can disregard this config.

Now if you open with gedit the conkyrc-line config you will see a section below "TEXT" 
```
${execi 600 ~/.conky/gmail.py}
```
So you see it's calling the included **gmail.py** script from **~/.conky**
This is the reason you have been told to install here.

You can place your configs and scripts anywhere you like as long as the paths to call the scripts are correct.

The Gotham conky doesn't call any scripts so is just a standalone config 
which can be saved anywhere without having to edit.

To keep things organized I just put all my conky downloads into a  **~/conky** folder and then edit the path to any scripts.

 It's also helpful to rename the configs to something easily recognized.
eg the **.gothamconkyrc** I renamed to **dateconky**.



Yes, the **-c** option tells conky to run that particular config
instead of the default **~/.conkyrc** file.
```
conky -c [COLOR="DarkOrange"]/path/to/conkyconfig[/COLOR]
```
Replace with **your** [COLOR="darkorange"]path to conkyconfig[/COLOR].

Test in the terminal 
and then use a startup script
eg
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 	killall conky 
else
 	conky -c [COLOR="DarkOrange"]/path/to/conkyconfig1[/COLOR] &
sleep 1
 	conky -c [COLOR="DarkOrange"]/path/to/conkyconfig2[/COLOR] &

fi
```

NB*** A dot in front of a file or folder makes it hidden(ctrl+h to show) 
**~/.conky** is a different folder to **~/conky**
Important when writing paths.

An easy way to get the correct paths is to go to the file in the file browser and right click on it and select copy.
You can now just paste into text editors.
For pasting into the terminal use the **Paste Filenames** Rclick option.


Thank you! That cleared things up a bit and reassured what I was already thinking. I'll fool around with it a little later on. Sorry for the late replies, I was visiting my father in the hospital after responding to you.

---

### Post by stinkeye on 2012-03-21
> **Spewed said:**
> Thank you! That cleared things up a bit and reassured what I was already thinking. I'll fool around with it a little later on. Sorry for the late replies, I was visiting my father in the hospital after responding to you.
Ok,hope all's well.

Also your gothamconky uses a font which is hard to find.
I've attached the font to download.
Extract the contents and place the folder into your **.fonts** folder in your home directory.
Create the .fonts folder if you don't have it.

---

