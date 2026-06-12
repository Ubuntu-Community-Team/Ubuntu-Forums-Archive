---
title: "Volume control doesn't seem to affect volume."
date: 2012-04-14
forum: General Help
---

### Post by LOLCLEVER on 2012-04-14
I'm running Xubuntu now, I didn't have this problem on regular Ubuntu although I'm not sure why that would make a difference. When I click the volume icon to adjust the slider, or use the controls on my keyboard/headset, the volume slider will change - and stay that way - but it seemingly makes no effect on my actual volume. To change my volume, I have to click the volume icon, go to 'sound settings', and change the volume this way:

[IMG]http://www.zimagez.com/full/d84689a4d2843e2a329a618ec91320d40b45283b1b9a8f2f6924c0fb25bf0a9d33ae6e5a0fe08b6b542657c05d89ad73956698ba1fcfc798.php[/IMG]

---

### Post by callmemahavir on 2012-04-15
Check if you selected appropriate Connector in Connector combo box.

---

### Post by LOLCLEVER on 2012-04-15
I don't see an option to change connectors anywhere. Where would it be?

---

### Post by callmemahavir on 2012-04-15
Goto -> System Settings -> Click Sound -> Goto Output tab -> Check correct connector is selected.

Check changing sound for each connector.

---

### Post by LOLCLEVER on 2012-04-15
I feel daft, but I can't find that path anywhere on Xubuntu. I checked the Settings Manager and everything else that looks like something like that and anything I could find related to my hardware earlier but none of it had "Sound" listed or any way to change the "connector".

---

### Post by callmemahavir on 2012-04-15
Download GvTray tool to adjust the volume.

See the URL ...

[http://xubuntu.wordpress.com/2007/08/15/gvtray-a-volume-control-for-your-system-tray/](http://xubuntu.wordpress.com/2007/08/15/gvtray-a-volume-control-for-your-system-tray/)

---

### Post by kazztan0325 on 2012-04-15
Hi LOLCLEVER,

I cannot see the screen shot which you attached.
Would you please edit your initial post?
Thank you.

---

### Post by Jose Catre-Vandis on 2012-04-15
@ LOLCLEVER

Not great advice so far as most seems to apply to **U**buntu and not **Xu**buntu.

Not sure what the solution to your problem is. When you click on the Volume icon you should get a mixer dialog open up. Click on "Select Controls" and add everything that is there (for testing purposes). It will probably come from Master, PCM and Headphones. Have a play with the various sliders to see which one actully does apply to your "normal" output volume.

You could also try running alsamixer (from a terminal) just to check there isn't something in there that needs setting.

---

### Post by JazzPotato on 2012-04-15
sudo apt-get install pavucontrol
Start up the program and change the default output stuff (i can't remember exactly what I did on my old pc)
Live long, and prosper.

---

### Post by djahma on 2012-05-01
Indeed, as explained[COLOR=Blue] [here]("https://bugs.launchpad.net/xfce4-volumed/+bug/901338")[/COLOR], the (current/future) merger of xfce4-volumed and xfce4-mixer is causing keyboards volume controls (xfce4-volumed actually) to control the audio card directly instead of going through PulseAudio as it should. 
Simpl[COLOR=black]y follow Ingo Ruhnke's workaround from the link above to sort the problem once and for all.

If you are a non-english xubuntu/xfce user as I am, you will probably experience some trouble in getting your card name right as xfce4-volumed doesn't work with accents such as é è î etc.

[/COLOR][COLOR=black]First, you must find the sound card you want your keyboard to control, so go into the sound control panel (I find it in my sound [/COLOR][COLOR=black]panel[/COLOR][COLOR=black] indicator) or type in a terminal [/COLOR]```
$ pavucontrol
```[COLOR=black]Under the output device tab you should see the different cards in your pc. If you move the volume control sliders you should quickly see which card xfce is using and which one you'd like to control instead. e.g. on mine, xfce is changing the volume for _Cedar HDMI Audio [Radeon HD 5400/6300 Series]_ when I wanted xfce to control _[COLOR=Indigo]Audio intégré Stéréo analogique[/COLOR]_.
[/COLOR][COLOR=black]Now in a terminal do,[/COLOR]```
$ killall xfce4-volumed
```[COLOR=black], or it will get in your way and prevent changes.
Next, you must transform the name of your card, by removing all accented letters, parentheses, brackets, spaces etc; to keep just the basic ASCII characters. So for me, the name in purple became: AudiointgrStroanalogique.
Add the words "Playback" before and "[/COLOR]PulseAudioMixer" after, to get your active card name and you can now make the change:
```
$ xfconf-query -v -c xfce4-mixer -p /active-card -s PlaybackAudiointgrStroanalogiquePulseAudioMixer
```Restart the volume daemon to experience the change:
```
$ xfce4-volumed
```

---

