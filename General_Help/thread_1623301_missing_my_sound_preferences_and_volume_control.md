---
title: "missing my sound preferences and volume control"
date: 2010-11-16
forum: General Help
---

### Post by vchickenskinv on 2010-11-16
the sound preferences menu, the one that's achieved by system>preferences>sound is completely gone, and so is the volume control that amarok/rhythmnbox connect too, that has that shortcut link to the sound preferences?

any ideas or any information i should gather that'll help you guys help me?

Sorry for what is probably a noobish question, third day of using linux ever.
EDIT:I'm on 10.10

---

### Post by Frogs Hair on 2010-11-16
System> Preferences> Main Menu ,scroll down to Preferences , select and make sure the box for sound is checked. To add the icon to the panel , right click the panel select add to panel and add the indicator applet.

If sound is missing from the Main Menu you will have to wait for help with that issue.

---

### Post by jmszr on 2010-11-16
vchickenskinv,

Go to System > Preferences > Main Menu > Scroll down to "Preferences" > "Volume Control" and checkmark that. In addition checkmark "Multimedia Systems Selector" (if it isn't already selected). The "MSS" will give you the functionality of the old Systems > Preferences > Sound > Devices.

Edit: You can drag and drop either/both icon(s) to the panel (and lock) if you wish.

---

### Post by vchickenskinv on 2010-11-16
All of that is missing, but thanks for the suggestions.
i still have an idicator applet or whatever up, i have my bluetooth/wifi showing up, but where the volume control would normally be isn't there.

i think this is an issue with pulseaudio, any idea how to reinstall?

---

### Post by Ancanus on 2010-11-16
Before you get into that, try 

```

sudo aptitude install gnome-volume-control
```

---

### Post by jmszr on 2010-11-16
Nmfn

---

### Post by vchickenskinv on 2010-11-16
> **Ancanus said:**
> Before you get into that, try 

```

sudo aptitude install gnome-volume-control
```
getting an aptitude command not found error.


I'm worrying most about my sound preferences being gone.

---

### Post by Ancanus on 2010-11-16
Hm.

How about

```

sudo apt-get install gnome-volume-control
```

---

### Post by vchickenskinv on 2010-11-17
> **Ancanus said:**
> Hm.

How about

```

sudo apt-get install gnome-volume-control
```
sudo apt-get install gnome-volume-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-volume-control

---

### Post by jmszr on 2010-11-17
vchickebskinv,

I think this should at least restore the volume control to the indicator applet:

```
sudo apt-get install indicator-sound
```

Hope that helps.

P.S.: What version of Ubuntu are you running?

---

### Post by vchickenskinv on 2010-11-17
> **jmszr said:**
> vchickebskinv,

I think this should at least restore the volume control to the indicator applet:

```
sudo apt-get install indicator-sound
```Hope that helps.

P.S.: What version of Ubuntu are you running?

10.10, i updated my original post to reflect this.
I talked to my roommate, who was the one that convinced me to install ubuntu, I told him I had problems with skype about two days back, and yesterday, he says he'd go fix it, so as I slept, I let him do his thing.

The volume control is now back on the indicator applet, but mute is greyed out, and the  sound preferences are now linking me to alsa?

and the issue i had with skype, it's not pulseradio anymore, it's a ton of options for my soundcard, which is why I think I need to reinstall skype.

if any more information is needed from me, or anyone else has anymore advice, it would help surely.

---

### Post by jmszr on 2010-11-17
vchickenskinv,

Have you discussed with your roommate exactly what he did when he "fixed" Skype? Does Skype work properly now?

If not, why don't you go ahead and reinstall Skype and then we'll see what affect that has on your issue.

---

### Post by vchickenskinv on 2010-11-17
> **jmszr said:**
> vchickenskinv,

Have you discussed with your roommate exactly what he did when he "fixed" Skype? Does Skype work properly now?

If not, why don't you go ahead and reinstall Skype and then we'll see what affect that has on your issue.
turns out he tried to uninstall pulse radio?

went through my history, he used this guide Im pretty sure
[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

I'm confused as to what to do to revert this back

and my bad, I didn't mean reinstall skype, i meant reinstall pulseradio

---

### Post by Jeff250 on 2010-11-17
I believe I may be able to assist, since that's my blog. ;) I'm sorry to hear about your roommate messing with your setup.  I was actually quite surprised to see my site linked here, since I've never linked to it from the forums.  I guess that's Google for you.

Since I can't say exactly what your roommate did, especially since it sounds like he left things in an inconsistent state, it's difficult to say what to do to undo it.  Here's my recommendation to try to undo everything that he may have done:

First run these commands to restore the PulseAudio command and gstreamer libraries:

```
sudo rm /usr/bin/pulseaudio
sudo dpkg-divert --rename --remove /usr/bin/pulseaudio
sudo dpkg-divert --rename --remove /usr/lib/gstreamer-0.10/libgstpulse.so
```

Open /etc/apt/sources.list in a text editor as root (sudo gedit /etc/apt/sources.list).  If they exist, remove anything resembling these two lines from the file:
```
deb http://ppa.launchpad.net/dtl131/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/dtl131/ppa/ubuntu maverick main
```

Then type in a terminal:
```
sudo apt-get update
```
And
```
sudo apt-get install --reinstall pulseaudio/maverick
```
```
sudo apt-get install gnome-settings-daemon/maverick gnome-applets-data/maverick gnome-applets/maverick libcanberra0/maverick libcanberra-gtk0/maverick libcanberra-gtk-module/maverick libcanberra-gstreamer/maverick gnome-session-canberra/maverick libgnome-media0/maverick gnome-media/maverick gnome-media-common/maverick libsdl1.2debian-pulseaudio/maverick
```

Reboot.  Then run
```
gstreamer-properties
```
and set everything in the audio tab to PulseAudio.

Hopefully this works.  After this, you may have to do things like manually add your old volume control back to the tray.  If this works, I'll update the blog post to provide more robust undo instructions.

---

### Post by vchickenskinv on 2010-11-17
I'm loving this community, everyone is quite helpful.

Jeff, I get to the last of your steps

i see default output/input and i set both to pulse sound, I then click test.

I get PULSEAUDIO sound server failed to connect, connection refused.

Where to here

oh, just realized that rhythmn box and movie player aren't giving me any audio, is that from pulseaudio being messed up?

---

### Post by Jeff250 on 2010-11-17
Yes.  Did you make sure to reboot?  It sounds like the PulseAudio server still isn't running.  Let's try to see what state things are in.

What does the following output when you paste it into a terminal?
```
ls -l /usr/bin/pulseaudio /usr/bin/pulseaudio.ubuntu /usr/lib/gstreamer-0.10/libgstpulse.so /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu
```
And this?
```
ps -e | grep pulse
```
And does this output any error messages or fix anything after you type both these?
```
pulseaudio -k
pulseaudio -D
```

---

### Post by vchickenskinv on 2010-11-17
> **Jeff250 said:**
> Yes.  Did you make sure to reboot?  It sounds like the PulseAudio server still isn't running.  Let's try to see what state things are in.

What does the following output when you paste it into a terminal?
```
ls -l /usr/bin/pulseaudio /usr/bin/pulseaudio.ubuntu /usr/lib/gstreamer-0.10/libgstpulse.so /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu
```And this?
```
ps -e | grep pulse
```And does this output any error messages or fix anything after you type both these?
```
pulseaudio -k
pulseaudio -D
```


for the first command, I get this.
ls -l /usr/bin/pulseaudio /usr/bin/pulseaudio.ubuntu /usr/lib/gstreamer-0.10/libgstpulse.so /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu
ls: cannot access /usr/bin/pulseaudio.ubuntu: No such file or directory
ls: cannot access /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu: No such file or directory
-rwxr-xr-x 1 root root 66840 2010-10-14 00:47 /usr/bin/pulseaudio
-rw-r--r-- 1 root root 88376 2010-09-24 18:17 /usr/lib/gstreamer-0.10/libgstpulse.so


Nothing happens with the second command.

karl@shitthouse:~$ pulseaudio -k
E: main.c: Failed to kill daemon: No such process

with the last command, the original pulseaudio preferences open up, but my soundcard is missing, and I can't figure out how to pick it, I only get "dummy output"

only piece of hardware there is my webcams microphone input.

we're getting somewhere, thank you so much for helping.

---

### Post by Jeff250 on 2010-11-18
From your 'ls -l' output, it looks like your files were correctly restored.  I think that getting "Dummy Output" happens if PulseAudio can't get an exclusive lock on your sound device.  If this wasn't already the case, try closing all programs (including Firefox, since Flash or something might be running in the background) and then rerun the last two pulseaudio commands.  Although even if this worked, it would be a kludge to manually get pulseaudio starting.  The real problem is that pulseaudio doesn't seem to be automatically starting when you boot--if it were, then it would also easily be able to get the lock on your sound device.

I wonder if your roommate didn't try following other advice for disabling PulseAudio before mine.  What does it say when you type:
```
sudo /etc/init.d/pulseaudio restart
```
And:
```
ls -l /etc/init.d/pulseaudio
```
And:
```
find /etc -iname '*pulseaudio*' 2>/dev/null
```
?

Just to double-check and since you didn't explicitly answer the last time I asked, have you rebooted since making the changes that I had in my first response?

---

### Post by vchickenskinv on 2010-11-19
> **Jeff250 said:**
> From your 'ls -l' output, it looks like your files were correctly restored.  I think that getting "Dummy Output" happens if PulseAudio can't get an exclusive lock on your sound device.  If this wasn't already the case, try closing all programs (including Firefox, since Flash or something might be running in the background) and then rerun the last two pulseaudio commands.  Although even if this worked, it would be a kludge to manually get pulseaudio starting.  The real problem is that pulseaudio doesn't seem to be automatically starting when you boot--if it were, then it would also easily be able to get the lock on your sound device.

I wonder if your roommate didn't try following other advice for disabling PulseAudio before mine.  What does it say when you type:
```
sudo /etc/init.d/pulseaudio restart
```And:
```
ls -l /etc/init.d/pulseaudio
```And:
```
find /etc -iname '*pulseaudio*' 2>/dev/null
```?

Just to double-check and since you didn't explicitly answer the last time I asked, have you rebooted since making the changes that I had in my first response?


for the first command i get
PulseAudio configured for per-user sessions
second command-
-rwxr-xr-x 1 root root 2228 2010-10-14 00:39 /etc/init.d/pulseaudio

the last command, i got this
 find /etc -iname '*pulseaudio*' 2>/dev/null
/etc/init.d/pulseaudio
/etc/xdg/autostart/pulseaudio.desktop
/etc/xdg/autostart/pulseaudio-kde.desktop
/etc/rc4.d/S50pulseaudio
/etc/rc1.d/K15pulseaudio
/etc/rc2.d/S50pulseaudio
/etc/default/pulseaudio
/etc/rc5.d/S50pulseaudio
/etc/dbus-1/system.d/pulseaudio-system.conf
/etc/rc3.d/S50pulseaudio



and yes, I did reboot.

pulseaudio DOES work, but i have to start it with pulseaudio -D, everytime.

sound preferences still doesn't exist in my system menu, but i can access it via the volume icon.

thanks for your help, but is there a way to get it to automatically start?

---

### Post by Jeff250 on 2010-11-20
Your terminal output looks fine, but my last post was actually leading you on a wild goose chase.  By default, it appears that PulseAudio doesn't start any system-wide daemon via an init script, but instead it's set up to start a per-user-session daemon when you log in.  The question I should have asked you is:

Go to System -> Preferences -> Startup Applications.  Do you see an entry for PulseAudio?  If it is greyed out, then your roommate disabled it, so check the box next to it to re-enable it.  If PulseAudio isn't listed at all, then your roommate removed it.  Add it back by clicking "Add" and put in PulseAudio for the name (you can name it whatever you want actually) and
```
start-pulseaudio-x11
```
for the command.  Disabling PulseAudio this way isn't the way my guide does it, but I think your roommate may have tried something else before mine, so checking this is worth a shot.

---

### Post by vchickenskinv on 2010-11-21
> **Jeff250 said:**
> Your terminal output looks fine, but my last post was actually leading you on a wild goose chase.  By default, it appears that PulseAudio doesn't start any system-wide daemon via an init script, but instead it's set up to start a per-user-session daemon when you log in.  The question I should have asked you is:

Go to System -> Preferences -> Startup Applications.  Do you see an entry for PulseAudio?  If it is greyed out, then your roommate disabled it, so check the box next to it to re-enable it.  If PulseAudio isn't listed at all, then your roommate removed it.  Add it back by clicking "Add" and put in PulseAudio for the name (you can name it whatever you want actually) and
```
start-pulseaudio-x11
```for the command.  Disabling PulseAudio this way isn't the way my guide does it, but I think your roommate may have tried something else before mine, so checking this is worth a shot.

Pulse audio seems to be in my start up applications, bu t i still have to use the whole pulseaudio -D line.

---

### Post by Jeff250 on 2010-11-22
What happens when you manually run start-pulseaudio-x11 from the terminal instead of pulseaudio -D?  Does that work?  Or any error messages?

One thought is that you could try adding pulseaudio -D to your startup applications (or if start-pulseaudio-x11 works from the terminal, you might try adding a second entry for that).  If this works, it wouldn't be a very satisfying solution, since it would just work around the real problem without really allowing us to understand what it is.  I suppose you might want to first check to make sure that the PulseAudio entry in Startup Applications is actually set to run start-pulseaudio-x11, if you haven't already checked this.

---

### Post by neycheva87 on 2011-06-19
Hello. I have some problems with the sound... I am using Ubuntu 11.04. I followed your blog to remove the Pulseaudio and after that to restore the system tray icon. The problem is that now I have a sound but don't know how to have back the tray icon. Any suggestions? And Also I have a lot of choises in skype for the input sound 
> **Jeff250 said:**
> I believe I may be able to assist, since that's my blog. ;) I'm sorry to hear about your roommate messing with your setup.  I was actually quite surprised to see my site linked here, since I've never linked to it from the forums.  I guess that's Google for you.

Since I can't say exactly what your roommate did, especially since it sounds like he left things in an inconsistent state, it's difficult to say what to do to undo it.  Here's my recommendation to try to undo everything that he may have done:

First run these commands to restore the PulseAudio command and gstreamer libraries:

```
sudo rm /usr/bin/pulseaudio
sudo dpkg-divert --rename --remove /usr/bin/pulseaudio
sudo dpkg-divert --rename --remove /usr/lib/gstreamer-0.10/libgstpulse.so
```Open /etc/apt/sources.list in a text editor as root (sudo gedit /etc/apt/sources.list).  If they exist, remove anything resembling these two lines from the file:
```
deb http://ppa.launchpad.net/dtl131/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/dtl131/ppa/ubuntu maverick main
```Then type in a terminal:
```
sudo apt-get update
```And
```
sudo apt-get install --reinstall pulseaudio/maverick
``````
sudo apt-get install gnome-settings-daemon/maverick gnome-applets-data/maverick gnome-applets/maverick libcanberra0/maverick libcanberra-gtk0/maverick libcanberra-gtk-module/maverick libcanberra-gstreamer/maverick gnome-session-canberra/maverick libgnome-media0/maverick gnome-media/maverick gnome-media-common/maverick libsdl1.2debian-pulseaudio/maverick
```Reboot.  Then run
```
gstreamer-properties
```and set everything in the audio tab to PulseAudio.

Hopefully this works.  After this, you may have to do things like manually add your old volume control back to the tray.  If this works, I'll update the blog post to provide more robust undo instructions.

---

### Post by timgood on 2011-06-19
I have a similar problem - but in my case it's just Skype that seems to be using Alsa instead of PulseAudio. Previously, I could not select anything other than pulseaudio from Skype's audio preferences, but now I get everything as per the attached screenshot. Something (or some update?) seems to have changed my settings.

I have uninstalled and re-installed pulseaudio as per the instructions above. Pulse Audio is running and set to start at startup. Rhythmbox and other sound applications use pulse, but Skype refuses to work when pavucontrol is active. Help would be appreciated. I also notice that PulseAudio Sound System KDE Routing Policy is set to run on start up. Could this have any effect?

---

### Post by PeterOakland on 2011-11-24
Jeff, I used your blog entry to fix a problem I was having with Skype and pulseaudio -- it would not come up reliably, and most often sounded like it had a huge stuttering frog in its throat.  Now, with alsa, it's fine.
I have been able to restore a vol. ctrl icon/applet to the bar.  However, when I go to Preferences, there's no longer an entry for Sound.  Is there something I need to do about that, or can I just leave well enough alone?
Thanks.  Greatly appreciate the help I got so far from your blog.

---

