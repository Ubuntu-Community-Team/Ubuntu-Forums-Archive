---
title: "synclient settings"
date: 2010-03-27
forum: General Help
---

### Post by kazakore on 2010-03-27
OK so I have had some issues getting my touchpad working as I like it. Using circular scroll as the edge scroll setting wont work. Scroll zone as standard is far too big, as previously mentioned.

I have since found I can set all settings via command line using synclient. For some reason my computer never remembers the zone setting for circular scrolling, always resting to the centre, and as mentioned the area of the pad for this is far too big.

I can correct both of these with these two lines in a Terminal

synclient CircScrollTrigger=3
synclient RightEdge=5950


What file should i add these to to be applied at startup? I have a .xinitrc in my Home to ensure Nvidia settings are loaded but wonder if this is too early?

---

### Post by kazakore on 2010-03-27
Nobody?

Is .xinitrc in my Home folder a reasonable place to add these commands or is it too easrly in the boot sequence?

---

### Post by kazakore on 2010-03-29
Well I added an entry in Startup Application called Touchpad Settings with "synclient CircScrollTrigger=3 ; synclient RightEdge=5950" as the command and this seems to have done the job.

Thanks for your help (do you think the sarcasm comes across on this post?)

---

### Post by John Baptist on 2010-05-05
Your sarcasm is clear.

I am dealing with the same issue. However, simply running synclient on startup does not work. In particular, the settings are "forgotten" if I suspend, hibernate, or switch to a virtual console (with ctrl-alt-f1). Clearly there needs to be a solution that lets one implement custom input device settings persistently, but I don't know what it is. 

I've also experimented with putting files in /usr/lib/X11/xorg.conf.d but the settings there are apparently ignored.

If anyone has any insight into this matter, I would be grateful.

---

### Post by FokkerCharlie on 2010-08-02
Did you get anywhere with this, John?  I am scratching my head over the same issue.

Cheers
Charlie

---

### Post by nils_a on 2010-08-21
Hi.
I stumbled across this post. 
You set theese things using hal.
I am unsure about the general setting names but I think they match the synclient settings.
so try editing /etc/hal/fdi/policy/99-x11-synaptics.fdi
to look like this: 
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <!-- this line is needed for this to work -->
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      <merge key="input.x11_options.CircScrollTrigger" type="string">3</merge>
      <merge key="input.x11_options.RightEdge" type="string">5950</merge>
    </match>
  </device>
</deviceinfo>

```

the file-location may also not be correct for ubuntu. But this should give you the right pointer...

Nils

---

### Post by FokkerCharlie on 2010-08-24
Nice one, Nils, that fixed it.

For reference, my file now looks like:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <!-- this line is needed for this to work -->
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">4</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">5</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">1</merge>
        <merge key="input.x11_options.TapButton3" type="string">1</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
	<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">20</merge>

    </match>
  </device>

</deviceinfo>
```

---

### Post by FokkerCharlie on 2010-08-25
Hmmm.

Unfortunately, it stops working after suspend/resume.  How odd.

Any ideas?

Charlie

---

### Post by mrant on 2011-01-25
I have recently upgraded to Maverick (10.10) and have been struggling with this same problem.

I have two-finger scrolling working great through the Mouse configuration, however, I would like to have two-finger AND vertical edge scrolling enabled at the same time. The Mouse config only provides one option or the other, not both at the same time.

Through research and experimentation, I was able to accomplish this by using synclient, however, the settings do not stick after reboot, suspend/resume, or switching to a virtual console. Adding the synclient command to startup also does not solve the issue.

Oddly, my /etc/hal/fdi/policy/ folder is empty, except for a thirdparty folder with a file related to ntfs-3g. I have also read that these settings should be set through xorg.conf.d config files, but my /usr/share/X11/xorg.conf.d/ folder also does not contain any config files related to synaptics.

I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=1603657](http://ubuntuforums.org/showthread.php?t=1603657)
and created the file 50-synaptics.conf and populated it with the following config:
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
	Option "VertEdgeScroll" "1"
EndSection

```
But this has no effect whatsover. (I also tried changing the "1" to "on").
I even tried these settings in xorg.conf (I'm pretty sure that is not right) but no luck.

Any ideas? I feel like I've tried everything that SHOULD work.

Funny thing about this is I remember in a past version of Ubuntu (8.04 maybe?) where the Mouse config supported simultaneous scroll mechanisms. Such is forward progress I suppose.

--MrAnt--

---

### Post by SundeepG on 2011-03-03
Hey, I've had success by modifying **/etc/hal/fdi/policy/preferences.fdi**. Navigate to the policy folder and type "gksu gedit preference.fdi" in the terminal to edit the file. You can then modify the touchpad (for synaptics) by using synclient settings (see synclient manpage for commands). My file now looks like:

<!-- -*- SGML -*- -->
&#8722;
<!--
 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
&#8722;
<deviceinfo version="0.2">
&#8722;
<!--
 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
&#8722;
<!--

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
	<match key="info.capabilities" contains="input.touchpad">
		<match key="info.product" contains="Synaptics TouchPad">
			<merge key="input.x11_driver" type="string">gsynaptics</merge>
			<merge key="input.x11_options.RTCornerButton" type="string">3</merge>
		<merge key="input.x11_options.TapButton2" type="string">3</merge>
		</match>
	</match>
  </device>
-->
</deviceinfo>

However, I accidentally modified another file which is overwriting some of these settings. I will post more when I find a solution. Let me know if this works for anyone else.

---

