---
title: "Constant Password requirements? No Cube?"
date: 2010-02-17
forum: General Help
---

### Post by JediCow on 2010-02-17
So I have been using ubuntu on my laptop for a while and finally decided to switch to it on my desktop. There are some things silly going on with the desktop that are bothering me.

I was wondering if there is anyway to turn off the system that requires to me to type in my password every time I boot in to connect to my wireless as well as remove the need to use a password to access my second hard drive after each boot as well.

Finally it seems like the cube is not working. It spreads out but will not stay like a solid cube. I have compiz installed and an nvidia 8600gts so from my understanding there shouldn't be any problem.


My pc specs if this helps at all
Ubuntu 9.10 x64
MSI p35 Platinum
Intel q6600 2.4ghz
Antec Earthwatts 500w
EVGA 8600gts 256mb
4gb OCZ Platinum Rev2 ram
Creative X-fi Xtreme Gamer Fatal1ty Pro
320gb HD (main with Ubuntu on it)
1tb HD used for music and movies
D-link DWA-556 Xtreme N pci-Ex1

---

### Post by Jackzor on 2010-02-17
With the password issue, explain better what you mean. Does the promt have anything to do with a keyring? Or is it just forcing you to logon to your router everytime you boot up?

And for the dektop cude hows about you take a screen shot so we can better see whats going on here.

---

### Post by Cabs21 on 2010-02-17
sounds like you didnt set up compiz properly to get the cube effect.  Also you could try restarting windows manager through compiz.  When my effects are not working I do that and it starts working fine again.

---

### Post by JediCow on 2010-02-17
I will try to reset it. As for the password, for when I first login it says the Network Manager Applet (I think that's what it was called.) wants access to the default keyring. Is there anyway to set it at default so it always has access. 

As for the HD password it says authentication is required to mount the device. Is there a way to have it auto authenticated so I don't have to do it every time after a boot?

---

### Post by snowpine on 2010-02-17
> **JediCow said:**
> As for the HD password it says authentication is required to mount the device. Is there a way to have it auto authenticated so I don't have to do it every time after a boot?

You can add the drive to your /etc/fstab so it is automatically mounted at boot time. Rather than edit fstab by hand, you can use a GUI application such as pysdm (it's available in the Ubuntu repositories).

---

### Post by JediCow on 2010-02-17
Premo, so that is one down and two to go. Well there are more but that will be another thread. As for a screenshot look at it below. The cube does not expand it just shows each desktop side by side:(. I want the full cube.

---

### Post by j.bell730 on 2010-02-17
I think I see what the problem is...
**Step 1**
[COLOR="Red"]*If you have already done this, ignore this step and proceed to step 2.*[/COLOR]
You'll need to install ccsm, so type:
```
sudo apt-get install compizconfig-settings-manager
```

**Step 2**
Go to a terminal and type in:
```
ccsm
```

**Step 3**
Go to **General Options**.

**Step 4**
Click the **Desktop Size** tab.

**Step 5**
Make sure your settings look like the ones pictured in the uploaded screenshot.

---

### Post by Cabs21 on 2010-02-17
> **j.bell730 said:**
> I think I see what the problem is...
**Step 1**
[COLOR=Red]*If you have already done this, ignore this step and proceed to step 2.*[/COLOR]
You'll need to install ccsm, so type:
```
sudo apt-get install compizconfig-settings-manager
```**Step 2**
Go to a terminal and type in:
```
ccsm
```**Step 3**
Go to **General Options**.

**Step 4**
Click the **Desktop Size** tab.

**Step 5**
Make sure your settings look like the ones pictured in the uploaded screenshot.

+1

You dont have a cube you have 6 sided desktop in the picture posted.  It can be set to like 30 and then it looks like a circle instead of a cube.

---

### Post by JediCow on 2010-02-17
I already had it set at 4 and tried 5. No luck.....damn. Is it possible I have selected the wrong driver?

---

### Post by Cabs21 on 2010-02-17
again if a change you make does not show up instantly reload the windows manager through compiz and if that doesnt fix it you could try a reboot.

---

### Post by JediCow on 2010-02-17
Unfortunately no luck. Ahhh well.

---

