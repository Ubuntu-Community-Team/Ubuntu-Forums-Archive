---
title: "How to restore PulseAudio auto-start?"
date: 2010-03-30
forum: General Help
---

### Post by Objekt on 2010-03-30
I broke PulseAudio accidentally, when I was trying to fix something else.  

I'm not sure what I did, but PulseAudio no longer starts automatically when I log in.  That means I get no sound.  I can start the PulseAudio daemon manually by running:
```
pulseaudio -D
```

at the command line, but I also have to go into sound preferences and select the correct hardware (Audigy 2 ZS card) instead of my motherboard's sound device (which is not connected to my speakers) to get sound back.

How do I make all that happen automagically?

---

### Post by Objekt on 2010-04-02
This is incredibly frustrating!  There are TONS of tutorials telling you how to remove pulseaudio, but not ONE explaining how to make it start automatically upon login.  

Doesn't anyone know how to make Pulseaudio start automatically, as it does in a default Ubuntu 9.10 install?

---

### Post by Chesamo on 2010-04-02
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) ?

---

### Post by kostkon on 2010-04-02
Add it in System &#8594; Preferences &#8594; Startup Applications.

---

### Post by Objekt on 2010-04-04
> **kostkon said:**
> Add it in System &#8594; Preferences &#8594; Startup Applications.

It's already there and selected, but it doesn't start.

I'm not sure what I did, but after some additional messing around, automatic Pulseaudio startup seems to be restored.

I still don't know why my regular old Ubuntu install tries to act like Ubuntu Studio.  As part of my troubleshooting, I created another user (misterdefault).  When I logged in as misterdefault, I got the Ubuntu Studio look and login sound and menu arrangement.  Weird.

---

### Post by lidex on 2010-04-04
> **Objekt said:**
> 
I still don't know why my regular old Ubuntu install tries to act like Ubuntu Studio.  As part of my troubleshooting, I created another user (misterdefault).  When I logged in as misterdefault, I got the Ubuntu Studio look and login sound and menu arrangement.  Weird.

It's called user error :biggrin:

---

### Post by Objekt on 2010-04-04
Nope, the pulseaudio daemon is still not starting up.  I don't know why it did just that one time.  If I reboot, I have to run the daemon manually upon login.

---

### Post by lidex on 2010-04-06
Try this:
```
sudo apt-get install --reinstall pulseaudio pulseaudio-module-x11
```

Logout/in

---

### Post by Objekt on 2010-04-06
Thanks.  I'll try that when I get home today.  

Sometimes I wish Ubuntu had a "panic button" that would automagically set all major apps (Pulseaudio, graphics, networking, maybe a few others) to their defaults.  I hate it when I mess with something, in an attempt to fix one problem, but accidentally break another thing.

---

### Post by lidex on 2010-04-06
From what I could ascertain, the "/etc/int.d/pulseaudio" shell script should start the daemon. Check in "System>Administration>BootUp-Manager" to make sure the service is activated. My lucid install also has an entry in "System>Preferences>Startup Applications" -- see attachment.

---

### Post by Objekt on 2010-04-07
I opened the config file (/etc/init.d/pulseaudio) and quickly realized I had no idea what to do.  Any hints?  There's some verbiage in the file about various options, but none of it seemed to address my problem.

---

### Post by lidex on 2010-04-07
Are you configured as in post #10?

---

### Post by Objekt on 2010-04-07
Yes.  I also followed the instructions in post #8.  Pulseaudio just DOES NOT START automatically.

---

### Post by lidex on 2010-04-07
I'm still leaning towards user error :D
*Kidding*

I'm at a loss. If pulse is correctly configured, then maybe whatever is supposed to call the startup script is the problem?

---

### Post by Objekt on 2010-04-08
I guess I can add an item on "Startup Applications" to run the Pulseaudio daemon.  I thought that was what the existing entry did, but it obviously doesn't work.

I also thought about running a Live CD session & just copying the settings from its config file (/etc/init.d/Pulseaudio).

---

### Post by Objekt on 2010-04-08
> **Chesamo said:**
> [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) ?

This also didn't work.  Apparently it is not applicable to current versions of Ubuntu, since it was written in 2005.

update:
OK, adding an item to "Startup Applications" worked.  Mostly.  I still don't get any sound at the initial login screen, but once I get to my user desktop, sound is there as it should be.

---

### Post by vipin.balakrishnan on 2010-05-09
Hi Objekt,

 I'm using Ubuntu 8.04 LTS. 

**Under System ->Preferences-> Sound**. Goto Sounds tab , Check the option enable software sound mixing(ESD). This enable pulseaudio to autostart.

---

### Post by Vienen on 2011-07-19
> **lidex said:**
> Try this:
```
sudo apt-get install --reinstall pulseaudio pulseaudio-module-x11
```Logout/in

Thanks, worked for me.

I had similar problem. I also removed pulseaudio accidentally and the taskbar icon could not control my sound volume and grayed out, but i could still hear sounds. The above code solved it.

---

