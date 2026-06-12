---
title: "Volume control missing"
date: 2010-07-28
forum: General Help
---

### Post by mastodon1314 on 2010-07-28
hey 
since i've upgraded Ubuntu to 10.04 the volume control is missing 
i cant find it anywhere! it isnt in the panel,  it isnt in the options to add to the panel, it isnt in the system preferences, it isnt in the applications menu....

i have no idea what the hell happened 

please help me 

thanks

---

### Post by chopinhauer on 2010-07-28
> **mastodon1314 said:**
> 
i have no idea what the hell happened 


I is in the notification zone (where e.g. the NetworkManager applet appears), it you don't have one, add it to the panel.

---

### Post by mastodon1314 on 2010-07-28
i have the notification zone on the panel but there is no volume control on there either

---

### Post by wilee-nilee on 2010-07-28
First try in the terminal,
```
killall gnome-panel
```
This will restart the panel, if you have removed the envelope applet that is why the volume icon is gone. You can put the volume icon in startup applications in preference here is a screenshot of the add setup.
[ATTACH]164859[/ATTACH]
Log off then back on the volume applet will back and actually adjustable by hovering and using a mouse wheel.

---

### Post by bobpress on 2010-07-28
> **mastodon1314 said:**
> i have the notification zone on the panel but there is no volume control on there either

That's the Network Manager Applet, but do you also have the Indicator Applet?  The battery and email indicators should be there also.  If you don't, right click the panel and you can select Add to Panel to add it.

---

### Post by mastodon1314 on 2010-07-28
the problem isn't it being absent from the panel it is being absent from EVERYWHERE

i CAN'T find a volume/sound preference button/app ANYWHERE!!!!

---

### Post by chopinhauer on 2010-07-29
> **mastodon1314 said:**
> i have the notification zone on the panel but there is no volume control on there either

Sorry, it was moved to the Notification Applet, the one with a mail envelope on it. If it is still missing, try executing
```
/usr/lib/indicator-sound/indicator-sound-service
```
in a terminal.

---

### Post by Quackers on 2010-07-29
I have exactly the same problem. My sound works but I have no icon.
I ran the script and here is the output

mike@mike-laptop:~$ /usr/lib/indicator-sound/indicator-sound-service
** (process:10837): DEBUG: Root ID: 1
** (process:10837): DEBUG: update pa state with state 0, availability of 0, mute value of 0 and a volume percent is 0.000000
** (process:10837): DEBUG: Building new Slider Menu Item
** (process:10837): DEBUG: !!!!!!**in the rebuild sound menu - slider active = 0
** (process:10837): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 0
** (process:10837): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 0.000000
** (process:10837): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0
** (process:10837): DEBUG: connecting - waiting for the server to become available
** (process:10837): DEBUG: authorizing
** (process:10837): DEBUG: context setting name
** (process:10837): DEBUG: PA daemon is ready
** (process:10837): DEBUG: server info callback
** (process:10837): DEBUG: Just set the default sink index to 0

** (process:10837): WARNING **: Default Sink info callback failure
** (process:10837): DEBUG: About to add an item to our hash
** (process:10837): DEBUG: After adding an item to our hash
** (process:10837): DEBUG: About to test for to see if the available sink is null - s->name = alsa_output.pci-0000_00_1b.0.analog-stereo
** (process:10837): DEBUG: PA_Manager ->  determine_sink_availability: 1
** (process:10837): DEBUG: software volume = 54.125977
** (process:10837): DEBUG: update pa state with state 1, availability of 1, mute value of 0 and a volume percent is 54.125977
** (process:10837): DEBUG: in the refresh menu method
** (process:10837): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 1
** (process:10837): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 54.125977
** (process:10837): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0

(process:10837): libindicator-WARNING **: No watchers, service timing out.
** (process:10837): DEBUG: Service shutdown !
** (process:10837): DEBUG: freeing the pulse context
** (process:10837): DEBUG: I just closed communication with Pulse


Any clues? Thanks

---

### Post by alenn on 2010-07-29
> **mastodon1314 said:**
> the problem isn't it being absent from the panel it is being absent from EVERYWHERE

i CAN'T find a volume/sound preference button/app ANYWHERE!!!!

try to redownload it at software center

---

### Post by Quackers on 2010-07-29
An update!
I replaced the indicator applet and now it's back :-)

I'd already tried that and it didn't work. Nevermind it's back now, lol. Maybe I did something wrong - not impossible ;)

---

### Post by Quackers on 2010-07-29
Things are a bit weirdly spaced 

[ATTACH]164897[/ATTACH]

---

### Post by chopinhauer on 2010-07-29
> **Quackers said:**
> Things are a bit weirdly spaced 


You can always change spacing by right clicking on the applet, unlocking it, moving it and then locking it again.

---

### Post by RabbitWho on 2010-07-29
Gots the same problem; ongoing with lubutnu and.. funny.. with ubuntu. 

In lubuntu there is no way to change the sound at all the sound preferences option is absent from the menus. When I sudo opened it the computer crashed.  

In ubuntu there's a link to the sound preferences screen on the panel now, which is not ideal. I want the thingy that you click on once and have a volume control + mute box.

---

