---
title: "Totally screwed up audio and mounts"
date: 2010-06-29
forum: General Help
---

### Post by MasterShihoChief on 2010-06-29
I recently installed kde4 ontop of my ubuntu to try it out and well i killed it i think :(

I had it working perfectly everything worked including my headset. The only problem was certain programs were too quiet for my taste and seeing as i have a laptop and cant manually turn up the speakers i looked for a solution and found
```
http://www.webupd8.org/2009/08/increase-maximum-sound-level-in-ubuntu.html
```

I followed those directions to try and boost the poor sound volume that has plagued me in ubuntu distros. Instead sound sparsly works. It is quieter than was, and if chrome is open at all no sound will play at all in rhythmbox or amarok(the play button dont even works it just sits at 0:00) Only after chrome closes does it play my music files again but only on this partition. As now my windows partition thats also located on this fakeraid just magically disappeared. 

I have no idea how to fix this as i dont even know what i did to begin with. Please help or at least tell me how i can trash kde and start over from within gnome(havent tried to see if it works there yet though)

EDIT: Logged back in to gnome and everything works fine. The missing partition is auto mounted like i wanted, the sound is perfectly fine. Obviously something got screwed up in the kde config but i dont know what or what to look for as i have never used kde before.

---

### Post by dabl on 2010-06-29
> **MasterShihoChief said:**
> I recently installed kde4 ontop of my ubuntu 



Did you do exactly that, or did you 

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

If you didn't do the latter, try it that way.  Then I would advise

```
sudo apt-get install pavucontrol padevchooser paman
```

Open Kmix and make sure it's not muted, and the volume slider is up.

Then open pavucontrol and check the PCM volume.

---

### Post by MasterShihoChief on 2010-06-29
yes thats exactly what i did to install kde and it was working perfectly (sound and the other partition were fine)until i messed with that blank config file to try and increase the maximum volume and then all this happened. In kmix the volume sliders are all up and like i said sound only works as long as chrome isnt running now for some reason (wasnt like that before i edited that file)

---

### Post by dabl on 2010-06-29
I have not personally found it necessary or helpful to edit /etc/asound.conf on my Kubuntu system, but I don't question that it may be helpful on some hardware.  However, note that his system has pulseaudio installed, and my suggested additional packages will give you more access to pulseaudio's controls, including the "device chooser" and volume control.

---

### Post by MasterShihoChief on 2010-06-29
ya i installed those inside gnome then logged into kde. Good news for some reason my other partition that vanished from /Media magically reappeared and i can access my music from my windows partition once again. Sound works again in amarok. sound doesnt work from within chrome. I dont know why but for some reason no sounds come from chrome anymore, and i didnt even touch chrome and it was working before.

EDIT: no other sounds work on any other apps including mangler, firefox, amsn, nothing. only programs that run sound is system sounds and amarok. Nothing else will remotely work. Movie player, world of warcraft or any games for that matter, notification sounds are also not working. Only system sounds and amarok. All these things work perfectly fine in GNOME.

---

### Post by MasterShihoChief on 2010-06-29
So i opened up amarok in gnome now since i got tired of using something broken. And now it breaks gnome if any kde program is started in gnome meaning no sound for anything, SO NOW EVERYTHING IS BROKEN AND I HAVE NO DAMN SOUND AT ALL!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1 I am extremely frustrated and my patience is wearing thin with all the problems i have with this distro. I'm about ready to just reformat the drive with windows 7, and just go back to what i know i can fix and maintain myself.

---

### Post by dabl on 2010-06-29
If you wish to use the KDE desktop, then the thing to do would be to install Kubuntu, rather than just KDE on top of Ubuntu.

To chase the audio issue, I don't know how much of this you have seen or tried to use:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

For the browser issues, you probably need to follow this first:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Then install Chrome or Firefox or whatever, and you should already have the plugins you need.


You say you are comfortable and able to fix and maintain a Windows system.  About how long did it take you to acquire that knowledge?  About how long have you given Linux?  ;-)

---

### Post by MasterShihoChief on 2010-06-29
just forget it, im tired of constantly having to spend hours upon hours just trying to fix things that just break for no damn reason or dont work to begin with. I have numerous other problems like webcam not working and im just sick of it, i give up on ubuntu im going back to windows where at least if something dies i can reimage and be back online in 5 minutes or just reinstall a driver. Seems ubuntu is just not friendly with any computer i ever own. cheers for the help anyways but ive had enough of the constant bs and lack of working things and lack of support for my other problems that have problems years old that still arent fixed.

---

