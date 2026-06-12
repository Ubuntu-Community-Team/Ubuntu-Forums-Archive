---
title: "How do you change the login sound in Ubuntu 10.4"
date: 2010-06-29
forum: General Help
---

### Post by Brii on 2010-06-29
Before you can just go to sys>prefs>sound

and you can change it there, but in 10.4 it doesn't work that way. how would one go about putting there own custom login sound?

---

### Post by nacho32 on 2010-06-29
good question I looked and founnd nothing on customizing your own sounds, besides theme packages

---

### Post by Brii on 2010-06-29
> **nacho32 said:**
> good question I looked and founnd nothing on customizing your own sounds, besides theme packages

Yeah, I was thinking of getting the sound file I want and then do a switcharoo with the default sound file [usr/share/sounds/ubuntu/stereo/desktop-login.ogg]. Not sure if it would work. 

Why would they take out that feature?

---

### Post by sgosnell on 2010-06-29
Rename any .ogg file you like to desktop-login.ogg, and it should play.  You obviously need root permissions to do this.  You can also go through System/Preferences/Startup Applications/Gnome Login Sound, and change "desktop-login" to the name of whatever .ogg file you want to use, without the .ogg extension.  I haven't tried that, but it should work.

---

### Post by nacho32 on 2010-06-29
yes very odd , but I think your method, should work. Wonders if mp3 or wav format would work. But still shocked it is not just a one click choose file deal.. I like the 10.04 but a few things they went backward on and this is one of them besides the buttons to the windows on the left but their was a easy fix for that..

---

### Post by Brii on 2010-06-29
> **sgosnell said:**
> Rename any .ogg file you like to desktop-login.ogg, and it should play.  You obviously need root permissions to do this.  You can also go through System/Preferences/Startup Applications/Gnome Login Sound, and change "desktop-login" to the name of whatever .ogg file you want to use, without the .ogg extension.  I haven't tried that, but it should work.

In Startup Applications under Login sound its:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Do we just change desktop-login to the file name that we want, don't we have to change the path too?

---

### Post by Pmaw10 on 2010-06-29
What I did was just replace the default desktop-login.ogg file with my own.

---

### Post by Brii on 2010-06-29
> **Pmaw10 said:**
> What I did was just replace the default desktop-login.ogg file with my own.

How? I can't edit that folder. How do I get root permissions to do that?

---

### Post by ajgreeny on 2010-06-29
> **Brii said:**
> How? I can't edit that folder. How do I get root permissions to do that?
Use sudo before the command in terminal or use gksudo nautilus for a root file manager.

[COLOR=Red]BE CAREFUL![/COLOR] You can cause a lot of damage if you don't know what you're doing when you use a root command with sudo, or even more easily in root enabled nautilus.

---

### Post by Brii on 2010-06-29
> **ajgreeny said:**
> Use sudo before the command in terminal or use gksudo nautilus for a root file manager.

[COLOR=Red]BE CAREFUL![/COLOR] You can cause a lot of damage if you don't know what you're doing when you use a root command with sudo, or even more easily in root enabled nautilus.

Oh sweet. Thanks for that. I just went in and swapped out the default for the one I wanted, and it worked! 

Now whenever my computer turns on I hear the landing sound effect of the TARDIS =P

---

### Post by sgosnell on 2010-06-29
> Do we just change desktop-login to the file name that we want, don't we have to change the path too?
 Yes, you have to change the path, if the file is in another directory.  Change /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
to /usr/bin/canberra-gtk-play --id="/path/to/file/filename" --description="GNOME Login".  That should work, although I haven't actually tried it on my system.

---

### Post by linux_virus on 2010-12-09
If not for the lack of winxp CD when I laptop caught the virus and if not for the vanity of showing others I could "type some cmd" I would never use ubuntu.
The login sound of ubuntu is just disgusting --- it's like the Buddhism worship every time. Why should I do that? I want to delete that login sound right now!!

---

### Post by sgosnell on 2010-12-10
"Buddhism worship"??  lol.  Project much?

---

### Post by odh1412 on 2011-06-17
Hey. So I was messing around trying to figure out how to change the login sound and I 
added a file to the sounds/ubuntu or w/e folder (where desktop-login.ogg) is stored and changed the gnome login sound settings from 

"/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login""

to

/usr/bin/canberra-gtk-play --id="wos" --description="GNOME Login"  (wos being the name of my new file)

This did not work and no sound played.

I then changed the file name wos to desktop-login and changed the original settings.

Still. no sound.

I then tried to cut my losses and revert to the original settings with the original sounds but that wont even play. 

any suggestions?

Thanks.

---

### Post by Sky Aisling on 2011-07-18
Hello,
I am having same issue as **odh1412.**
Using the GUI screens provided in System/Preferences - I attempted to change login sound with my sound without success then* lost original login drum roll sound* when attempting to set login sound back to original.

Here is what didn't work:

Opened System/Preferences/Startup Application Preferences/ GNOME Login Sound/ Edit Startup Program.
Replaced Command: /usr/bin/canberra-gtk-play with /home/sky/Music/Doctor_Who_theme_excerpt.ogg.
This did not work.

Then I  replaced the original file /usr/bin/canberra-gtk-play into the Command box. 
Now, I have no sound.  
The original file appears to be deleted? 
To test, I attempted to *open* canberra-gtk-play by placing it in Rhythm Box, GNOME MPlayer to see if it was there.  Negative.
There is a faint *click* sound where the drum roll should be at startup, but, no more login sound.  

Note: all the work I did was with *GUI* input not *terminal* input.
Note: where is the file extension on canberra-gtk-play?  This does  not look like a file but an executable?  Are we mixing apples and  oranges here?
I also checked system/administration/login screen.  *Play login sound* was checked.  To see screen I had to *unlock* screen then I *closed* screen.  I did this several times.

My machine configuration is:
[B]ZaReason Big Lap
3  gigs RAM[/B]
My OS is:
**Lucid Lynx 10.04**

Included is a screen shot of the replacement of the original path and file name.

Any suggestions are appreciated.  Thank you.

---

### Post by Sky Aisling on 2011-07-18
[COLOR=SeaGreen]Partial Success:[/COLOR]

Reference:
[http://ubuntuforums.org/archive/index.php/t-1630965.html](http://ubuntuforums.org/archive/index.php/t-1630965.html)

**satish_j** Writes:

> /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
this one?

Replace it with foll:

/usr/bin/canberra-gtk-play --file=/path to your sound file

Logout and Login again.It should play your sound file.This works to play my choice of sound. (note: it also slows down the login startup just a bit where the Ubuntu system sound does not)

Note: You can find the *Ubuntu* original login sounds in */user/share/sounds*.

Now, how to get original back?  Reverse[FONT=Helvetica, Arial, sans-serif] psychology?

**EDIT:**
[COLOR=SeaGreen]Success [/COLOR] 
I found the answer to how to get the original login sound back:
Go to this forum:
[http://www.pclinuxos.com/forum/index.php?topic=73117.0](http://www.pclinuxos.com/forum/index.php?topic=73117.0)
Follow **MBantz**'s direction to insert the following command into the *Command* box of the GNOME Login Sound (*system/preferences/startup applications/GNOME Login Sound/edit*):

[/FONT]/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

I guess the moral of this story is "if it ain't broke, don't fix it".

---

### Post by darkwalt on 2011-10-18
Easy solution:

```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

change NoDisplay=true to NoDisplay=false

```
sudo apt-get install sox libsox-fmt-mp3
```

Go to startup applications.  Uncheck Gnome login sound.  Create a new startup program

```
play /dir-name/soundname.extension
```

Even if your home folder is encrypted, this should work because the sox program plays the file after you are logged in, therefor your home folder will be open for sox to read.

Tested and true solution for me from 10.4 - 11.10.

---

### Post by gbd on 2011-10-22
Thanks darkwalt. Your solution worked perfectly in Oneiric. 

I fiddled about and broke the default desktop-login sound in a very similar manner to that described by odh1412. I did the NoDisplay=false thing, I modified the path to my favorite UbuntuStudio login sound, but nothing. I undid everything back to default but still nothing, not even the default desktop-login sound.

Installed sox as above and created a startup application and it worked first time. So confirmed as a solution in 11.10. Thanks again darkwalt.

---

### Post by darkwalt on 2011-10-22
No prob, glad I could help.  Did the same thing everybody else did here and borked the gnome login sound too.  The only thing I do notice is that there is a little bit of a longer delay from the original.

---

### Post by krt on 2012-01-08
When I run: ```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
``` I get the following:

> [Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound

Where is the "NoDisplay" part that I should modify?

Thank you,

krt

Edit: You know this is really peculiar that one cannot put back the original sound and have it work . . .

---

### Post by darkwalt on 2012-08-19
Sorry, been gone for a while.  Yours seems to be missing two lines of code.  

after your last line, it should have two more lines

```

X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=false
NoDisplay=false

```

Changing or borking the sound in 12.04 via the sox method works as well.

---

