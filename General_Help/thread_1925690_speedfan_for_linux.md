---
title: "speedfan for linux"
date: 2012-02-15
forum: General Help
---

### Post by hg088 on 2012-02-15
hi

is there an app that allows me to monitor and control the cpu, gpu and ohter fans speeds like speedfan does in windows

---

### Post by Ms. Daisy on 2012-02-15
Ubuntu Software Center has the following apps. I haven't tried them so I can't comment on their effectiveness.

**XSensor** uses a GUI to display hardware health like temp, voltage & fan speed.  Looks like you might need to also install lm-sensors adn run sensors-detect to make it work.

**Psensor **also uses a GUI to display temp, speed of fans & sensor of a remote computer.

---

### Post by Bobhuber on 2012-02-15
> **hg088 said:**
> hi

is there an app that allows me to monitor and control the cpu, gpu and ohter fans speeds like speedfan does in windows
Lmsensors for the monitoring and Screenlets has a program called Meter that allows you to setup custom display.

---

### Post by 3rdalbum on 2012-02-15
You can monitor fan speeds with the 'sensors' command (in the lm-sensors package). I don't think there is any manual fan control facilities in Linux. I find it a bit pointless - you have a computer that can make a billion decisions every second, designed to make your life easier, yet you're not trusting it with the mundane task of controlling its own fan speed?

Your BIOS should be able to do a fine job of controlling its CPU fan speed, as long as you have that option enabled in your BIOS settings.

---

### Post by aasdfasdfg on 2012-02-15
After installing the lm-sensors package, you'll want to install indicator-sensors as well. It is available from a ppa [here]("https://launchpad.net/~alexmurray/+archive/indicator-sensors")

---

### Post by Bobhuber on 2012-02-15
> **3rdalbum said:**
> You can monitor fan speeds with the 'sensors' command (in the lm-sensors package). I don't think there is any manual fan control facilities in Linux. I find it a bit pointless - you have a computer that can make a billion decisions every second, designed to make your life easier, yet you're not trusting it with the mundane task of controlling its own fan speed?

Your BIOS should be able to do a fine job of controlling its CPU fan speed, as long as you have that option enabled in your BIOS settings.
fancontrol is a linux program for fan speed based on temperature .For those folks with an older bios and fixed fan speeds that dont want to listen to all the noise unless needed  .

---

### Post by hg088 on 2012-02-16
thanks guys, great suggestions

apparently my problem now is that sensors-detect wont find the drivers for my main rig's mbo, but thats another story

thnaks again

---

### Post by Mark Phelps on 2012-02-16
Just to add one caution -- too many folks come here complaining about the "noise!" their fans make, and are only interested in slowing the fans down, to make less noise.

What they entirely fail to understand, is that the fans in modern PCs are variable speed, and their speed is driven the the need to keep the processors down below a certain temperature threshhold.

Forcing a fan to run slower runs the serious risk of burning out the processor it is trying to cool down.

An alternative, and better, solution is NOT to force the fan to run slower, but instead, to force the processor to run slower.  That will generate less heat, and the fans will automatically run slower as a result.

So, if you DO find a way to slow down the fans, it's really a BAD idea to do that.

---

### Post by Ms. Daisy on 2012-02-16
> **mark phelps said:**
> just to add one caution -- too many folks come here complaining about the "noise!" their fans make, and are only interested in slowing the fans down, to make less noise.
 
What they entirely fail to understand, is that the fans in modern pcs are variable speed, and their speed is driven the the need to keep the processors down below a certain temperature threshhold.
 
Forcing a fan to run slower runs the serious risk of burning out the processor it is trying to cool down.
 
An alternative, and better, solution is not to force the fan to run slower, but instead, to force the processor to run slower. That will generate less heat, and the fans will automatically run slower as a result.
 
So, if you do find a way to slow down the fans, it's really a bad idea to do that.
 
+1

---

### Post by Bobhuber on 2012-02-16
> **Mark Phelps said:**
> Just to add one caution -- too many folks come here complaining about the "noise!" their fans make, and are only interested in slowing the fans down, to make less noise.

What they entirely fail to understand, is that the fans in modern PCs are variable speed, and their speed is driven the the need to keep the processors down below a certain temperature threshhold.

Forcing a fan to run slower runs the serious risk of burning out the processor it is trying to cool down.

An alternative, and better, solution is NOT to force the fan to run slower, but instead, to force the processor to run slower.  That will generate less heat, and the fans will automatically run slower as a result.

So, if you DO find a way to slow down the fans, it's really a BAD idea to do that.
Different strokes for different folks but that statement is totally wrong on a modern system. On an older system with fixed bios maybe.
If someone wants to monitor fan speeds and temp they have a reason and it's not necessarily a BAD idea to control fan speeds. I like speed - cool - and quiet and have all three on an moderately overclocked setup. I also monitor cpu temp and fan speeds to achieve this which is what the original post was all about. 
My Bios allows base settings for CPU fan speeds (32%-100%) as most of the newer boards do and will automatically increase the fan speed as needed . So unless I want to set the base speed at 100% (4500 rpm) and listen to a freight train all the time I most certainly need and want a way to monitor and control these speeds and temps.

---

### Post by QIII on 2012-02-16
Your last paragraph is internally inconsistent and contradictory, bob.

Set minimum fan speed in BIOS, set BIOS to control fan speed based on temperature, set BIOS to throttle CPU cores when not under load.  Your fans will not run at full gallop all the time.  Most boards have system fan headers and the BIOS can be set to change fan speed on them as well.

Most modern boards allow all of that and they do it in milliseconds - so when you ho to get a Mountain Dew out of the fridge and your CPU load spikes, you don't come back to a flaming machine.

---

### Post by Bobhuber on 2012-02-16
> **QIII said:**
> Your last paragraph is internally inconsistent and contradictory, bob.

Set minimum fan speed in BIOS, set BIOS to control fan speed based on temperature, set BIOS to throttle CPU cores when not under load.  Your fans will not run at full gallop all the time.  Most boards have system fan headers and the BIOS can be set to change fan speed on them as well.

Most modern boards allow all of that and they do it in milliseconds - so when you ho to get a Mountain Dew out of the fridge and your CPU load spikes, you don't come back to a flaming machine.
  That is what I thought I said. BASE speed being the minimum fan speed (a place to start).The BIOS controls (increases and decreases) fan speed as needed based on temperature. And yes if I set the CPU fan speed to 100% it will run full gallup as you say no matter what the temperature.
P.S. I also hate Mountain Dew LOL

---

### Post by QIII on 2012-02-16
Since the OP was about software control of fans and your last sentence seemed to say you wanted same, I may have misread your intent.

User intervention in a process that a modern motherboard offers is, in my opinion, a dangerous game.

I do use bay mounted fan controllers on a couple of machines, but their intent is to force 100% fan speeds when I run things like Folding or Rosetta unattended.

---

### Post by Corvair on 2012-03-13
Thank you Ms Daisy.Installing XSensor solved my problem. Very nice display and easy to open the display

---

