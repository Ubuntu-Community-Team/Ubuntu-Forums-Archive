---
title: "no startup sound?"
date: 2012-04-11
forum: General Help
---

### Post by gandalf3 on 2012-04-11
i am new to linux, and am running Ubuntu 11.10
i recently gave up on my previous sound card, and got a cheap used (old) sound blaster live. as far as i can tell, everything is working as it should, but when I saw another machine startup ubuntu 11.10, it made a sound on startup that mine never made.. (and coudn't find anything in settings that would seem to affect it)
my question is, is it possible this is not the only thing not working? 
and of course, why is it not working.. did i miss a setting some where?
:confused:

---

### Post by kolinab on 2012-04-11
If you somehow have a system where the start up sound doesn't work, you can count yourself among the lucky ones. Disabling the startup sound it usually the first thing I do on a new Ubuntu install. 

You can check that 'sound effects' are not muted in your sound settings. Go to 'system settings,' then 'sound,' then check the entry for 'sound effects.' Next, you can launch the 'startup programs' utility and see if 'login sound' is in the list, and the box is checked for it.

Do all other system sounds play ok?

---

### Post by gandalf3 on 2012-04-11
they were not muted, and "gnome log on sound" was turned on..
i don't if they play or not, (because i don't know when they are supposed to) but im guessing no, because i never notice anything..
however, skype makes noise, and browser sounds seem to be working.

---

### Post by Frogs Hair on 2012-04-11
This worked for me on 11.10.

Install the following. 

sudo apt-get install dconf-tools


Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

On the theme name line click directly on the word free desktop. Completely delete and replace that word with the word ubuntu in lower case.
  
close and open the configuration editor to make sure the setting was saved .

---

### Post by gandalf3 on 2012-04-12
i can't get it to save.. 
it reverts to "freedesktop" if i even click outside the window, let alone close it..
:/

---

### Post by philinux on 2012-04-12
Dash > startup apps > enable login sounds.

---

### Post by gandalf3 on 2012-04-12
> **philinux said:**
> Dash > startup apps > enable login sounds.

it is enabled..
i clicked edit, and went to the directory that it had in the edit dialog box, but i couldn't get the executable to play..
(is it supposed to do that?)

---

### Post by gandalf3 on 2012-04-13
oh.. hmm that's interesting..
well, no idea why, (i didn't change anything after i rebooted) but it's working now! Thanks!
i started up this morning, and for what ever reason it worked.. now i can turn it off :p..
but the system sounds are working too, which is the main thing.
(they were definitely not working before)
:-D

---

### Post by Shadius on 2012-04-14
> **philinux said:**
> Dash > startup apps > enable login sounds.

Hey, total Ubuntu noob here. Did you mean *Startup Applications*? If you did, I don't see an *Enable Login Sounds*. It opens up the *Startup Applications Preferences* window where it shows "Gnome Login Sound" under "Additional startup programs:". Am I doing something wrong? :-k

---

### Post by gandalf3 on 2012-04-14
hmm good point.. i didn't either.. i just took it to mean check the check box next to gnome login sound.
I'm not sure if that's what fixed mine, but it's working now :)

---

### Post by Shadius on 2012-04-14
Mine used to work, but now I don't know what happened. LOL I've unchecked and checked the box, restarted, and still nothing. I really didn't notice that my login sound stopped working until I came across this thread. I've found the sound files, and they play just fine in Banshee. I'm stumped.

---

### Post by gandalf3 on 2012-04-16
did you try the suggestions in these posts?

> **Frogs Hair said:**
> This worked for me on 11.10.

Install the following. 

sudo apt-get install dconf-tools


Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

On the theme name line click directly on the word free desktop. Completely delete and replace that word with the word ubuntu in lower case.
  
close and open the configuration editor to make sure the setting was saved .

> **kolinab said:**
> If you somehow have a system where the start up sound doesn't work, you can count yourself among the lucky ones. Disabling the startup sound it usually the first thing I do on a new Ubuntu install. 

You can check that 'sound effects' are not muted in your sound settings. Go to 'system settings,' then 'sound,' then check the entry for 'sound effects.' Next, you can launch the 'startup programs' utility and see if 'login sound' is in the list, and the box is checked for it.

Do all other system sounds play ok?

also, my startup sound stopped working the other day too..
anyone have a clue why?:confused:

---

### Post by gandalf3 on 2012-04-16
hmm
try running the command under startup apps "gnome login sound" in the terminal. here's a screen shot

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216151&stc=1&d=1334630603[/IMG]

here's what happened when i tried it (something is clearly not working)

```
 /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

(canberra-gtk-play:2360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:2360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:2360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(canberra-gtk-play:2360): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Failed to play sound: File or data not found

```the file is there, but it can't figure out how to play it with banshee..

---

### Post by kolinab on 2012-04-19
For those of you still experiencing this issue, apparently there is a documented bug for this problem. Maybe it affects you?

There is a link to a workaround posted in the following link, just two clicks away . . . 

[http://ubuntuforums.org/showpost.php?p=11434159&postcount=85](http://ubuntuforums.org/showpost.php?p=11434159&postcount=85)

---

### Post by gandalf3 on 2012-04-20
:biggrin:Thanks! 
works good! (although i haven't actually tried logging out and back in yet.. just running it in the terminal)

>                         Same behavior in oneiric. No login sound.
canberra-gtk-play looks for sound file in /usr/share/sounds/
 oneiric@VirtualBox:~$ canberra-gtk-play --id="desktop-login"
Failed to play sound: File or data not found
 oneiric@VirtualBox:~$ /usr/bin/canberra-gtk-play --file /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
woks as expected...
 Copying /usr/share/sounds/ubuntu/stereo/desktop-login.ogg to
/usr/share/sounds/desktop-login.ogg solves the problem
 I'm not sure if this has to be filed against libcanberra or  ubuntu-sounds since sound theming is disabled or not yet implemented  under gnome3.

              
instead of Copying /usr/share/sounds/ubuntu/stereo/desktop-login.ogg to
/usr/share/sounds/desktop-login.ogg, i just put ```
/usr/bin/
canberra-gtk-play --file /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```in the "command box" in startup apps..
Thanks! (hmm i wonder.. if maybe i replaced desktop-login.ogg with my own file i could have a custom login.. hmm)
anyway, thanks for fixing!:grin:

---

### Post by kolinab on 2012-04-20
> **gandalf3 said:**
> :biggrin:Thanks! 
Thanks! (hmm i wonder.. if maybe i replaced desktop-login.ogg with my own file i could have a custom login.. hmm)
anyway, thanks for fixing!:grin:

Yes, I'm sure you if you place a different file there and rename it that you could have a custom login sound. This also works as a second method to disable it -- if you want, rename the file to something like desktop-login-disabled.ogg and it will stop working again.

---

### Post by gandalf3 on 2012-04-20
> **kolinab said:**
> Yes, I'm sure you if you place a different file there and rename it that you could have a custom login sound. This also works as a second method to disable it -- if you want, rename the file to something like desktop-login-disabled.ogg and it will stop working again.
or take it out of startup apps.. or put the old command back.. or.. well, making it stop seems easy now..:P

---

### Post by cominatyalive on 2012-06-14
> **gandalf3 said:**
> hmm good point.. i didn't either.. i just took it to mean check the check box next to gnome login sound.
I'm not sure if that's what fixed mine, but it's working now :)


Hello, Good advice here. But I had a no log in sound issue for a month or so before I finally found my issue. Leave your Freedesktop setting alone in dconf-editor. 

Yes, make sure your startup application command says:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

in startup applications.

And here's the kicker where I believe everyone is being fooled. If you go to the upper right hand of your desktop to your volume control, right click, go to sound settings, click sound effects, and make sure the volume bar for (ALERT VOLUME) is set more than 1/2 way up. I had mine set at about a 1/3 way up & it went unheard for two months. In all this time, I tried to find out what was wrong.  

Set it at about 3/4 or 7/8 of the way up. And you will be good.
Anything below 1/2 on the alert volume adjuster bar, and chances are you will not hear the log in sound. 

Also, leave the (freedesktop) word alone in dconf-editor. It is only for (Event Sounds) not the Log In sound.  

After setting it farther up, Open your terminal up and paste the same start up command in there & hit enter. It should play. If it does not there is something else going on. With a fresh 12.04 install, this is the reason why. No-one is hearing it, that's all. Or the start up command box was not in your start up commands.

I hope this helps hundreds of people out here who have been pulling their hair out ever since 12.04 LTS has been released.

Good luck,

James

---

### Post by gandalf3 on 2012-06-15
thanks
my volume was at max... however i was using 11.10
and replacing the default command in startup apps with ```

/usr/bin/ canberra-gtk-play --file /usr/share/sounds/ubuntu/stereo/desktop-login.ogg 
```

is what fixed it
(also, i couldn't even get "freedesktop" to change..)

---

### Post by cominatyalive on 2012-06-16
> **gandalf3 said:**
> thanks
my volume was at max... however i was using 11.10
and replacing the default command in startup apps with ```

/usr/bin/ canberra-gtk-play --file /usr/share/sounds/ubuntu/stereo/desktop-login.ogg 
```

is what fixed it
(also, i couldn't even get "freedesktop" to change..)

Great you have it working. I too did it your way before. It was probably working with the .ogg file. However, the alert volume level was too far down for me to hear it. But I'm glad to know that this too works. cheers!

---

