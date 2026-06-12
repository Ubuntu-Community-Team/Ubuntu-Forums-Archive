---
title: "Karmic: Changing default desktop-login sound"
date: 2009-10-30
forum: General Help
---

### Post by Toddy on 2009-10-30
Perhaps I'm missing the obvious, but it appears that Sound (under System - Preferences) doesn't allow a user to change the default sounds, for example the login sound.  The best solution I could find was to navigate to /usr/share/sounds/ubuntu/stereo and backup the desktop-login.ogg and then copy my favourite ogg sound as desktop-login.ogg.  It doesn't seem to be the most intuitive way to change the sound.  It there a GUI way to change that I am overlooking?

---

### Post by Solarisphere on 2009-11-01
I'm wondering the same thing, and the only solution I can see is to switch out the .ogg files. This thread is all I can find on the subject with google.

---

### Post by fwre01 on 2009-11-02
This seems the same in the Netbook Remix of Karmic im using on my Dell Mini 9. Not only can I not change the sound clip, I also can't seem to disable it either.

Under Pref > Sound I clicked 'No Sounds' under the theme, this seemed to disable all of the sounds except the drums that sound when the login screen appears.

Does anyone know how to disable this?

---

### Post by sancho panza on 2009-11-02
I think you have to go via the Configuration Editor tool and search for GDM related settings.

---

### Post by fwre01 on 2009-11-02
Thanks, I looked around there, couldnt find anything, I searched for the file name of the sound clip but it didnt show anything.

The sound played is called 'system-ready.ogg' in /usr somewhere. There's another thread open for this [here]("http://ubuntuforums.org/showthread.php?t=1275436"), seems as tho there is only a work around for it atm.

I just renamed the file until theres an actual fix for it :-)

---

### Post by CaptainMark on 2009-11-03
Im having trouble with this, wierdly, ive got a sound i want to use for login and it is an ogg file. i changed it so its in the ubuntu/stereo folder with the right name, logged out and back in, nothing! I checked the permissions and they were different so i chmod'd to 644 to match all the others, logged out logged in..... Nothing!  
What the hell?? whats going on?

---

### Post by airencracken on 2009-11-04
Even changing the system sounds setting in gconf I still get the drums. Annoying.

These rollbacks in customization ability are quite Apple like and disconcerting. Hope it's just temporary.

Renamed the file. Hopefully that works. A bit of a kludge though.

---

### Post by airencracken on 2009-11-05
Has anyone filed a bug-report for this?

---

### Post by Donalb on 2009-11-05
On Intrepid the login sound used to be disabled in Sessions (only god knows why).

On Karmic, Ubuntu-Tweak still retains this setting, and is how I disabled it.
Ubuntu-Tweak is always worth having for some small fixes.
It's not in the repos but at:
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Hope this helps.

---

### Post by NTolerance on 2009-11-05
I'll file a bug report on this later today.  I simply want to disable the login sound without having to alter system files.

I guess the sound feedback is good for some people, but consider using a laptop in a pubic place.  Invariably the volume will be set very high, yet at the login screen you can't easily lower the system volume.  Everyone in the room will know you just logged in.](*,)

---

### Post by BWinc on 2009-11-05
First post and I'm sorry it's a gripe. Agreed that this needs to be bugged. Jaunty let you and I'm surprised that this simple functionality didn't transfer over.

---

### Post by NTolerance on 2009-11-05
Found the bug report:  [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429)

Some workarounds are posted.  Worth a read.

---

### Post by larryfroot on 2009-11-10
Here's another one for the record. if its not already dealt with from the previous link, or you want to save yourself a journey then this is what I did:

Actually I visited the above link and as there didn't seem to be a repetition if I posted the below there, I posted it there as well. Although it isn't an elegant workaround, I achieved it without too much stress. Those of you who require a silent login can use ubuntu-tweak as it contains an on/off switch for the login sound in Start Up / Autostart.

The ogg file causing the irritation, the login-sound is to be found in /usr/share/sounds/ubuntu/stereo

it is called desktop-login

If you have an ogg to drop in, rename it to desktop-login, change permissions on the above directory to your current username account and group, example below - remembering to seal it up again later on - again example below. 

If you haven't a handy ogg and need to convert your media type to ogg 

sudo apt-get install soundConverter 

video on using it which is very good:

[http://www.youtube.com/watch?v=Q7H2dS4uhD4](http://www.youtube.com/watch?v=Q7H2dS4uhD4)

then change permissions on the folder that holds the desktop login sound, 

in a terminal type

sudo chown username:username -R /usr/share/sounds/ubuntu/stereo

This will change all the files permissions to your user account (using the recurser switch -R) it is by far best practice to hand it all back to root when we finish here.

Then open up sound converter and click to open a file, the one you want to play instead of the god awfull roll of drums. Its costing me a fortune in bananas needed to pay my monkey cus of all the bloody somersalts he pulls off.

Anyways, check the file filter in sound converter is set to spot the file type you wish to convert to ogg, get it up in the app, and press convert. I think it defaults to ogg, cus that's what mine did. Then copy paste the freshly ogged sound into /usr/share/sounds/ubuntu/stereo and then seal the directory up with 

sudo chown root:root -R /usr/share/sounds/ubuntu/stereo

entered into a terminal.

and press enter.

log out and back in again and away you go. the same rig-maroll for every sound event that the desktop plays one supposes...

---

### Post by CaptainMark on 2009-11-11
I got another .ogg file and put it in the right place but now i get no sound at all, i cant even get the old sound back if i put the original ogg back in place, im sure i have all the permissions correct ```
mark@mark-desktop:~$ ls -lah /usr/share/sounds/ubuntu/stereo/
total 424K
drwxr-xr-x 2 root root 4.0K 2009-11-11 18:46 .
drwxr-xr-x 3 root root 4.0K 2009-11-11 18:46 ..
-rw-r--r-- 1 root root 4.9K 2009-10-12 01:01 bell.ogg
-rw-r--r-- 1 root root 8.8K 2009-10-12 01:01 button-pressed.ogg
-rw-r--r-- 1 root root 4.0K 2009-10-12 01:01 button-toggle-off.ogg
-rw-r--r-- 1 root root 4.0K 2009-10-12 01:01 button-toggle-on.ogg
-rw-r--r-- 1 root root 102K 2009-11-03 19:24 desktop-loginbackup.ogg
-rw-r--r-- 1 root root 102K 2009-10-12 01:01 desktop-login.ogg
-rw-r--r-- 1 root root  27K 2009-10-12 01:01 desktop-logout.ogg
-rw-r--r-- 1 root root  11K 2009-10-12 01:01 dialog-error.ogg
-rw-r--r-- 1 root root 5.3K 2009-10-12 01:01 dialog-information.ogg
-rw-r--r-- 1 root root 9.7K 2009-10-12 01:01 dialog-question.ogg
-rw-r--r-- 1 root root  12K 2009-10-12 01:01 dialog-warning.ogg
-rw-r--r-- 1 root root  23K 2009-10-12 01:01 message-new-instant.ogg
-rw-r--r-- 1 root root  29K 2009-10-12 01:01 phone-incoming-call.ogg
-rw-r--r-- 1 root root 7.9K 2009-10-12 01:01 phone-outgoing-busy.ogg
-rw-r--r-- 1 root root  17K 2009-10-12 01:01 service-login.ogg
-rw-r--r-- 1 root root  15K 2009-10-12 01:01 service-logout.ogg
lrwxrwxrwx 1 root root   19 2009-11-11 18:46 system-ready.ogg -> dialog-question.ogg
-rw-r--r-- 1 root root 6.9K 2009-10-12 01:01 window-slide.ogg

``` Any know whats going on here? its winding me up

---

### Post by larryfroot on 2009-11-11
Thats nuts.

What could in essence be different in what I did and what you did? Essentially it's about knowing where the file is, changing permissions on the folder and contents, slotting the ogg in, then changing the permissions back on the folder and the contents. 

This is a probable stupid shot in the dark, but I used the recursive switch and changed all the files in the folder to my user name and group. The file I copied in obviously was chown'd to said name and group. 

After I slotted it in I recursively switched the folder and all the contents back to root all in one command. 

Could there be some thing in how I did it that you didn't? To be honest, I was well surprised at how easy it was, I return here and its still not that easy for people. :(

---

### Post by skykooler on 2009-11-18
Well, I found a workaround that does not require modifying system files:

[LIST=1]
[*]Move your new sound to your home folder.
[*]Go to Startup Applications.
[*]Uncheck Gnome Login Sound.
[*]Add new launcher. In command box, type ```
aplay mysound.wav
```.
[*]Make sure your new launcher is checked. Now your sound will play on startup.
[/LIST]

---

### Post by daniel_w93 on 2009-11-22
okay this worked for me...it's pretty easy.

1. Open a terminal and copy your .Ogg file into /usr/share/sounds/ubuntu/stereo  

```
sudo cp /your/source /usr/share/sounds/ubuntu/stereo
``` 

2. click on the system button in your main panel. Go to Preferences, select Startup Applications. Now look for the <GNOME Login Sound> Launcher and deselect it.
Then click the add button. Give it any name (something like startup sound would make sense to avoid confusion). 
In the <Command> line type:

```
/usr/bin/canberra-gtk-play --id="YOUR FILE NAME" --description="GNOME Login"
```

!!!JUST WRITE THE FILE NAME WITHOUT THE .Ogg EXTENSION!!!

Hit save, check if it's selected...Then reboot and try :P

---

### Post by CaptainMark on 2009-11-23
i tried to paste to the command from the start up apps line into the terminal and got back an error. Ive just added a line in the startup apps to run a bash script that plays the sound. Wierd workaround but it worked.

---

### Post by brianfactors on 2009-11-23
I really am confused as to why this was changed. I had the login disabled in Jaunty, updated to Karmac, and all of a sudden, it greeted me with the drum roll. Which is cool when I'm at home, but not when I'm in class or at the library.

There is this update:
[http://www.webupd8.org/2009/10/turn-off-login-sound-in-ubuntu-karmic.html](http://www.webupd8.org/2009/10/turn-off-login-sound-in-ubuntu-karmic.html)

It just seems really strange to me to run this command for something I could do in OLDER versions.

---

### Post by skykooler on 2009-11-23
> **CaptainMark said:**
> i tried to paste to the command from the start up apps line into the terminal and got back an error. Ive just added a line in the startup apps to run a bash script that plays the sound. Wierd workaround but it worked.
What was your error message? Have you tried just typing the command in the terminal?

---

### Post by CaptainMark on 2009-11-23
yes, sorry i was at work on my phone when i posted this so couldnt get much detail in, copying and pasting from startup apps is get : ```
mark@mark-desktop:~$ /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

(canberra-gtk-play:4230): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
```Means nothing to me. What really threw me off is putting this code into start up apps does nothing ```
aplay /home/mark/.sounds/zelda/stereo/desktop-login.wav
``` but i put the same code in a bash script and added a line in startup apps to run the script and it works fine, that confused the hell outta me???

---

### Post by firedrake on 2009-11-23
> **brianfactors said:**
> I really am confused as to why this was changed. I had the login disabled in Jaunty, updated to Karmac, and all of a sudden, it greeted me with the drum roll. Which is cool when I'm at home, but not when I'm in class or at the library.

There is this update:
[http://www.webupd8.org/2009/10/turn-off-login-sound-in-ubuntu-karmic.html](http://www.webupd8.org/2009/10/turn-off-login-sound-in-ubuntu-karmic.html)

It just seems really strange to me to run this command for something I could do in OLDER versions.

If you want the drum roll sound disabled, then

alt+F2
gconf-editor

untick the *active* key in order to **disable the login ready drums sound** in
 /apps/gdm/simple-greeter/settings-manager-plugins/sound/

Hope it helps...:)

---

### Post by undoIT on 2009-11-24
> **firedrake said:**
> If you want the drum roll sound disabled, then

alt+F2
gconf-editor

untick the *active* key in order to **disable the login ready drums sound** in
 /apps/gdm/simple-greeter/settings-manager-plugins/sound/

Hope it helps...:)

That did not work for me. I've tried everything and the only thing that actually worked was the command mentioned in the link above:

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

It is crazy that there is no way to turn this off without running that command. If I were trying out Ubuntu for the first time and couldn't get it turned off, even after exhausting all the options in the Sound preferences etc, I'd probably decide not to use Ubuntu.

---

### Post by Frdbrkl on 2009-11-26
Larryfroot-thanks and a cuppa joe to ya.  Your method worked flawlessly!

One caveat-make *sure* you correctly reinstate permissions.  The folder and file must be executable or silence will ensue....(hint to all the silence lovers).

Thanks for the help folks!

---

### Post by hobo14 on 2009-12-03
> **undoIT said:**
> That did not work for me. I've tried everything and the only thing that actually worked was the command mentioned in the link above:

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```


That's the only one that worked for me, too.

---

### Post by Roshan_Kulkarni on 2010-01-17
Found one quick way to disable the login sound (the sound played before the desktop load, after user has entered the credentials).

**System > Preferences > Startup Application**
In that listing uncheck the item "GNOME Login Sound". 

However I wonder why such an option is not offered in the System > Preferences > Sound.

---
[Roshan Kulkarni]("http://www.it.iitb.ac.in/~roshan/")

---

### Post by dspisak on 2010-06-05
daniel_w93, thank you for the  tip.  It also worked for me.  However, I had to save the default login file "desktop-login.ogg" to something else and rename my login sound file to "desktop-login.ogg".

I still have not been able to stop the "bongos" sound when ubuntu starts.

I'm using 10.04 LTS, Lucid Lynx.

Dan

---

### Post by mlnease on 2013-02-16
I realize this thread is pretty ancient, but the correct fix (for my install of Lucid) doesn't appear in this thread so I thought I'd post it here:  Go to System > Administration > Login Screen > Unlock; at the top left of the window, uncheck the box marked 'Play Login Sound'.  Hey, presto!  Problem SOLVED.

---

### Post by CaptainMark on 2013-02-16
Necromancy! No no no!

---

