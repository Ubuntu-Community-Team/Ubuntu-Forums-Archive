---
title: "Wireless Laser Mouse Movement Is Jumpy"
date: 2010-06-18
forum: General Help
---

### Post by Manaan on 2010-06-18
I didn't put this in the hardware section because that section seems to be dedicated to critical hardware incompatibilities, and I didn't want to bother anybody there with my problem.

Anyway, here's what's going on: My wireless laser mouse (an iHome IH-M135ZR) will about 50% of the time move jerkily. As though the screen isn't refreshing fast enough to catch the movement. But that isn't the problem because in AssaultCube the game treats the mouse as moving jerkily, too. I don't think this is a CPU issue because stopping compiz doesn't help at all. I also don't think so because this is on a netbook and the mouse touch pad thing moves just fine. If this has something to do with process priority (the trackpad taking higher priority than the mouse) than I would like to know how to disable the trackpad temporarily when I use the mouse.

I know this isn't a very important problem but it's driving me crazy. I'd like to be able to play FPS games on my netbook since I don't own a proper computer and this is the one thing that's keeping me from it.

I'm a fairly new Linux user so a simple explanation of what I can do to fix it would be appreciated.

**THE SOLUTION:** I downloaded gpointing-device-settings and turning my trackpad off by disabling most of the trackpad-related options in the System>Preferences>Mouse menu.

---

### Post by bobcollard on 2010-06-18
> **Manaan said:**
> I didn't put this in the hardware section because that section seems to be dedicated to critical hardware incompatibilities, and I didn't want to bother anybody there with my problem.

Anyway, here's what's going on: My wireless laser mouse (an iHome IH-M135ZR) will about 50% of the time move jerkily. As though the screen isn't refreshing fast enough to catch the movement. But that isn't the problem because in AssaultCube the game treats the mouse as moving jerkily, too. I don't think this is a CPU issue because stopping compiz doesn't help at all. I also don't think so because this is on a netbook and the mouse touch pad thing moves just fine. If this has something to do with process priority (the trackpad taking higher priority than the mouse) than I would like to know how to disable the trackpad temporarily when I use the mouse.

I know this isn't a very important problem but it's driving me crazy. I'd like to be able to play FPS games on my netbook since I don't own a proper computer and this is the one thing that's keeping me from it.

I'm a fairly new Linux user so a simple explanation of what I can do to fix it would be appreciated.
Run the following in Terminal or download and install through Synaptic Package Manager then put it in your startup programs so you have a choice at restart or bootup.  It can also be run with alt F2 (Run Program) or Terminal.
```
sudo apt-get install gpointing-device-settings
```

---

### Post by steveneddy on 2010-06-18
Here's something I have to do occasionally on my laser mice:

Get a Q-tip and dip it in a little rubbing alcohol - leave the other end dry. Turn your mouse over and clean the little lens with a twisting motion like you were rubbing your fingers together.

Now take the dry end of the Q-tip and dry the lens in the same manner. When done blow on the leans a little to evaporate what is left of the residual alcohol.

Another thing you might look at is the surface you are using the mouse on. That may be an issue also.

Hope this helps.

---

### Post by UranUtan on 2010-06-18
I wonder if Ubuntu would know if the mouse is wired or wireless to treat the mouse differently.

Whenever I have issue with wireless mouse the causes are: battery, proximity to a wireless device like a laptop near by, interferences from a cordless phone ... or the hardware of the mouse itself. When replaced by a wired mouse, the issue disappeared.

---

### Post by Manaan on 2010-06-18
> **bobcollard said:**
> Run the following in Terminal or download and install through Synaptic Package Manager then put it in your startup programs so you have a choice at restart or bootup.  It can also be run with alt F2 (Run Program) or Terminal.
```
sudo apt-get install gpointing-device-settings
```

I tried gpointing-device-settings but it doesn't seem to immediately disable my trackpad. Maybe a reboot is required, first.

I don't think this is a hardware problem because I just rebooted and my mouse seems better afterwards. Also, I just changed the battery, the mouse is within about 10 inches of the usb device that came with it, and I just bought it so the lens should be pretty clean. Also, I'm using a normal mousepad. There isn't any dust on it, either.

Actually, after my latest reboot (this was done before reading any of your responses) the mouse seems to be completely normal. However this has happened in the past and the mouse has eventually started lagging again.

---

### Post by bobcollard on 2010-06-18
> **Manaan said:**
> I tried gpointing-device-settings but it doesn't seem to immediately disable my trackpad. Maybe a reboot is required, first.

I don't think this is a hardware problem because I just rebooted and my mouse seems better afterwards. Also, I just changed the battery, the mouse is within about 10 inches of the usb device that came with it, and I just bought it so the lens should be pretty clean. Also, I'm using a normal mousepad. There isn't any dust on it, either.

Actually, after my latest reboot (this was done before reading any of your responses) the mouse seems to be completely normal. However this has happened in the past and the mouse has eventually started lagging again.
You did run the applet, right?  Not just install it?  You have to run it each time you boot or restart.

---

### Post by Manaan on 2010-06-18
Yes, I ran the applet and selected "Touchpad Off". It's weird because I just tried it again, and it stopped the touchpad for a while but started working again after about one minute.

---

### Post by waynefoutz on 2010-06-18
paste this in the terminal and then launch your game, see if it makes a difference..



```
export SDL_VIDEO_X11_DGAMOUSE=0

```

---

### Post by Manaan on 2010-06-18
> **waynefoutz said:**
> paste this in the terminal and then launch your game, see if it makes a difference..



```
export SDL_VIDEO_X11_DGAMOUSE=0

```

While I can't definitively say that this worked due to the unpredictable nature of this problem. I can say that I was able to run the game with no mouse jittering to speak of. There is still a tiny bit but it's almost inconsequential. So, what do I do to make this permanent, put it in autorun?

**EDIT:** Actually, nevermind. I just compared it to the original with ```
export SDL_VIDEO_X11_DGAMOUSE=1
``` and it seems to be about the same. Sorry for the false positive.

---

### Post by waynefoutz on 2010-06-19
> **Manaan said:**
> While I can't definitively say that this worked due to the unpredictable nature of this problem. I can say that I was able to run the game with no mouse jittering to speak of. There is still a tiny bit but it's almost inconsequential. So, what do I do to make this permanent, put it in autorun?

**EDIT:** Actually, nevermind. I just compared it to the original with ```
export SDL_VIDEO_X11_DGAMOUSE=1
``` and it seems to be about the same. Sorry for the false positive.

Sorry it didn't help. It fixed my mouse problems. To make it permanent, I added the following lines to my /etc/X11/xorg.conf file:

```
Section "Module"

         SubSection  "extmod"
           Option    "omit xfree86-dga"   # don't initialise the DGA extension
         EndSubSection

	Load		"glx"
EndSection
```


I'm running an older build of Ubuntu, modern versions don't even have that file anymore, but I suppose it would use it if you made one. Someone please correct me if i'm wrong on that.

---

### Post by bobcollard on 2010-06-19
> **Manaan said:**
> Yes, I ran the applet and selected "Touchpad Off". It's weird because I just tried it again, and it stopped the touchpad for a while but started working again after about one minute.
You have to turn off the two marked boxes under Mouse/Touchpad in System.

---

### Post by Manaan on 2010-06-21
> **bobcollard said:**
> You have to turn off the two marked boxes under Mouse/Touchpad in System.

Thanks, that worked. And I think it solved the mouse lag problem, too.

---

### Post by bobcollard on 2010-06-21
> **Manaan said:**
> Thanks, that worked. And I think it solved the mouse lag problem, too.
Great. Please edit your first post in the Title and add [Solved] to it, so others may learn from your experience.

---

### Post by DHSdrone on 2010-09-30
How would I map the keys to do things like forward, and back in browser, or change desktops by shifting the wheel left or right? Running lucid.
Thanks

---

