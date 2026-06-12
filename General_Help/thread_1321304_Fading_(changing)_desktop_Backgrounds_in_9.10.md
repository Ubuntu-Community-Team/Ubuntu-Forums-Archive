---
title: "Fading (changing) desktop Backgrounds in 9.10"
date: 2009-11-09
forum: General Help
---

### Post by vizitorq on 2009-11-09
Hey guys! Just upgraded to 9.10 from 8.04! Big jump! Anyway, I decided I wanted to make this one look a lot like a mac, so I've succeeded with all the similarities I wanted except one, I want to add the fading/changing wallpaper. After doing a bit of research I found there were a couple of programs, dapper and wallpaper-tray that perform this task. I downloaded wallpaper-tray, but I didn't like the fact that it automatically grabbed images from my /home/user/Pictures directory, and I didn't like the fact that it disregarded all the directories that I added for it to choose images from... So, it basically doesn't work.

I also found that there is a way to do it with an XML file in the /usr/share/backgrounds/ directory. With 9.10, in /usr/share/backgrounds/cosmos/ there is an XML file that looks like this:
```

<background>
  <starttime>
    <year>2009</year>
    <month>11</month>
    <day>09</day>
    <hour>22</hour>
    <minute>18</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
    <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/comet.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/comet.jpg</from>
    <to>/usr/share/backgrounds/cosmos/earth-horizon.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/earth-horizon.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/earth-horizon.jpg</from>
    <to>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</from>
    <to>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</from>
    <to>/usr/share/backgrounds/cosmos/helix-nebula.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/helix-nebula.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/helix-nebula.jpg</from>
    <to>/usr/share/backgrounds/cosmos/jupiter.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/jupiter.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/jupiter.jpg</from>
    <to>/usr/share/backgrounds/cosmos/sombrero.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/sombrero.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/sombrero.jpg</from>
    <to>/usr/share/backgrounds/cosmos/whirlpool.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>/usr/share/backgrounds/cosmos/whirlpool.jpg</file>
  </static>
  <transition>
    <duration>2.0</duration>
    <from>/usr/share/backgrounds/cosmos/whirlpool.jpg</from>
    <to>/usr/share/backgrounds/cosmos/cloud.jpg</to>
  </transition>
</background>

```

I changed the start-time parameters, but nothing has happened. I wanted to know how you make this XML file actually WORK. Do I have to make it an executable or something? Can anyone help me with this?

---

### Post by vizitorq on 2009-11-09
Nevermind. Found the answer

You have to right click the desktop. Click Change desktop background. And Add the XML file as a desktop background. You must choose from the dropdown menu to display ALL FILES, not just IMAGES, then add the xml file to your backgrounds list...

[http://ubuntuforums.org/showthread.php?t=1314008](http://ubuntuforums.org/showthread.php?t=1314008)

---

