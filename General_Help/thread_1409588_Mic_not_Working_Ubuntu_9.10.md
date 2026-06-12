---
title: "Mic not Working Ubuntu 9.10"
date: 2010-02-17
forum: General Help
---

### Post by neu5eeCh on 2010-02-17
I've seen the other threads and have tried their solutions (and have been confused by their solutions), but am still not able to make my mic work on two separate computers.

Thought I'd start fresh.

How can I get my MIC working? What's the magic pill?

---

### Post by fragos on 2010-02-18
Right click speaker/sound applet icon and select "Sound Preferences" and then the "Input" tab. Make sure volume is up and Mute is off. My solution to this issue involved trial and error. In the "Choose a device for sound input:" box you may see two items with the 1st selected. In my case both were described the same "Internal Audio Analog Stereo". Select the 2nd and the "Connector" bar select "Analog Microphone / Input 1 / Microphone 1". Now speak into your microphone and observe the "Input Level:" which should now respond to your voice. If that doesn't work try all the other settings until one dose.

---

### Post by honey toast on 2010-02-18
this is what I did to get mine working- open up your sound recorder app, then open sound preferences, and then on the input tab put the connector option to 'line-in'. Finally, up top where it says 'input volume' make sure that is not on mute and is audible at somewhere around 100. That should fix u up.

---

### Post by neu5eeCh on 2010-02-19
Thanks for both your suggestions. I may try the latter later today.

//Make sure volume is up and Mute is off. //

I tried that earlier.

//In the "Choose a device for sound  input:" box you may see two items with the 1st selected.//

I only have one. Unfortunately, I have no mic option in the latest incarnation of this control panel.

//Now speak into your microphone and observe the "Input Level:" which  should now respond to your voice. If that doesn't work try all the  other settings until one does.//

What I've got to do, as Honey Toast suggests, is to find a recorder app. With that in mind, what app did you use to pick "line in"?

---

### Post by fragos on 2010-02-19
"Line in" and "Microphone" are different jacks on most mother boards. The difference may be that "Line in" is for amplified input. In my case my TV card has an external sound jack which connects to "Line in".

---

### Post by neu5eeCh on 2010-02-20
> **fragos said:**
> "Line in" and "Microphone" are different jacks on most mother boards. The difference may be that "Line in" is for amplified input. In my case my TV card has an external sound jack which connects to "Line in".

Yes, so I have to wonder why Linux is only offering me the internal mic? Anyway... I've got to sort this out on two different computers (my wife's). I've yet to try.

---

### Post by neu5eeCh on 2010-02-23
Just an update. I still haven't been able to get my mic working - and that's driving me nuts because, otherwise, Ubuntu has been flawless on my computer. Flawless. I've tried using Audacity to finesse Ubuntu, but no luck. It's as if Ubuntu doesn't even know an input jack exists?

---

### Post by Endless_Nameless on 2010-02-23
The same problem here! I have a Vaio NS-series, which built-in microphone works wonderfully in Windows, but I can't get it to work in -this incredible thing that is- Ubuntu 9.10! I tried all the options in Sound Preferences, and even tried to install ALSA (which is installed, but does not appear as an option other than Pulse Audio).

I have three options for input: "Microphone 1", "Microphone 2" and "line-in", but none seems to work. If I can get it to work, I will post it here.

---

### Post by fragos on 2010-02-23
Devices on desktop computers are interfaced to in consistent ways. One driver works for all hardware within a particular OS. For example all SD card readers are USB. Laptops are a different story and SD readers for example may be interfaced to with a less expensive to manufacture chip set. I can't help but wonder if that might be the case for a laptop microphone. The implication is the microphone interface for your laptop may be unique and require a special driver. Just food for thought.

---

### Post by Endless_Nameless on 2010-02-24
It worked!:D Unfortanetly by "magic" ...:(

I tried one method, but I think you can try this one first:

**1st method:** (I don't know if it really works)
```
sudo apt-get remove pulseaudio
sudo apt-get install pulseaudio
```If this does not work, you can try the method that I did use.

**2nd method:**
```
sudo apt-get remove pulseaudio
```Than I followed the steps in _*[ALSA v1.0.21 Upgrade Script]("http://ubuntuforums.org/attachment.php?attachmentid=128874&d=1253177665")*_. Which not only did not work for my micro, but you will not have the sound control GUI, and my sound did not work as well. So I did:
```
sudo apt-get remove alsa-oss aconnectgui alsa-firmware-drivers
sudo apt-get install pulse audio
```I don't know very well the connections between alsa and others programs, so I didn't tried something like "remove alsa*". Maybe the update of alsa that I did changed some file that is also used by pulseaudio, which made it work. As I said, try the "1st method first", and let me know how it worked. I hope this explanation is not so confuse (english is not my first language), so any doubt about my text you can ask me!

---

### Post by neu5eeCh on 2010-02-24
Endless, just checked in and saw your post. I will try this out and get back to you and all.

---

### Post by neu5eeCh on 2010-02-28
> **Endless_Nameless said:**
> It worked!:D Unfortanetly by "magic" ...:(

I tried one method, but I think you can try this one first:

**1st method:** (I don't know if it really works)
```
sudo apt-get remove pulseaudio
sudo apt-get install pulseaudio
```If this does not work, you can try the method that I did use.

(and etc...)

Alas, none of your suggestions worked. But thank you... I also checked out "The Official Ubuntu Book: Fourth Edition", and while they acknowledged that Microphones don't seem to work in Ubuntu, their solution was useless (make sure the mute is off and mic sliders are up). Duh.

Frustrating.

I guess I'm going to have to keep googling and googling until I stumble over a  solution.

---

### Post by donut123 on 2010-03-03
The Microphone does work in Ubuntu...i have had it working....not in Ultimate ...I have a problem...last year when i had Ubuntu...it worked fine...now I dont know.....it should work.

---

### Post by HunterAnderson on 2010-03-04
hey. im having the some problem to. i know before i switched to ubuntu my line in worked but not anymore. ive tryed to change different settings but its like it has yet to recognise it. i have two internal mics and they work fine but as for the line in i cant say the same. any suggestions???

---

### Post by fragos on 2010-03-04
What's connected to Line-in?

---

### Post by HunterAnderson on 2010-03-05
it was a mic but i tried to run from the headphones jack to linein just to make sure the mic i had that wasnt broke but no results then either

---

### Post by fragos on 2010-03-05
The jack is the same but I believe the electrical characteristics are aren't the same for line-in and headphones. That's not really my area of expertise.

---

### Post by neu5eeCh on 2010-03-05
> **HunterAnderson said:**
> hey. im having the some problem to. i know before i switched to ubuntu my line in worked but not anymore. ive tryed to change different settings but its like it has yet to recognise it. i have two internal mics and they work fine but as for the line in i cant say the same. any suggestions???

Good luck.

I still look for solutions, but they're all so haphazard as to be rhymeless and reasonless (from my perspective). I've noticed a lot of users say: I did "X", "X" worked, and I have no idea why "X" worked.

Try everything. Do a rain dance. It might work.

Anyway.... I'm going to file a bug report sometime today. You should do the same.

---

### Post by HunterAnderson on 2010-03-05
im not exactly sure about the electrical thing either. id think you would get some signal but i could be wrong. ill keep trying stuff to see if i can get it to work. if i cant get it going i will probably file a bug report to see if it can get fixed. if it happened to the few of us there are probably more people having the problem or will. then again it could just be compatibility but never the less.
till then however the lousy integrated mics will have to suffice for my english project. thanks for the suggestions. even if they don't fix it you can learn alot just trying them out(im still learning ubuntu).:)

---

### Post by Smith.. on 2010-04-11
Hey after doing all that stuff. Why not try this out. Goto:

System>Administration>Users and Groups

Give yourself access to these groups here: 

pulse
pulse-access 
audio
voice

Man after reading a LOT about this deal and nothing working. I remembered that seeing in other posts they talked about giving yourself access to pulse and pulse-access. Then by accident I figured why not right. Lets try voice and see if that's the trick. Low and behold my mic not only works. But I'm here posting the good news. The "community" has helped me out. If this works for you awesome. Next time your having issues with something no one else can figure out. Give people the low down on what you did to fix it. So we're all good. Anyways hope this helps you out. It did for me. 

Peace

I forgot to mention you'll need to restart your x server for these changes to take effect. All that means is you log out then back in again.

---

