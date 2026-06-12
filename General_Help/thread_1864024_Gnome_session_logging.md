---
title: "Gnome session logging"
date: 2011-10-18
forum: General Help
---

### Post by littlesatan on 2011-10-18
Hey guys.
I need to find some way to write a log of gnome session starting.

The problem is in my touchpad (alps, not synaptic): while I stay on Oneiric welcome screen, my touchpad works fine. When I login in my fresh new testing profile, touchpad works fine.
But when I login in my main profile (from Natty (from Karmic)),  the touchpad dying during loggin in.

It's listed in xinput, but have "[FONT=Courier New]Device Enabled: 0[/FONT]".
When I try "**xinput set-int-prop *id* "Device Enabled" 8 1**", the state of "[FONT=Courier New]Device Enabled[/FONT]" doesn't change.
After that:
[B]sudo modprobe -r psmouse
sudo modprobe psmouse[/B]

touchpad works just about 2sec, then died again.

I have no idea how that's possible, so is there any way to see what happens during gnome session loads?

---

### Post by blueridgedog on 2011-10-18
I would compare the files in ~/.gconf/desktop/gnome/peripherals/touchpad/ between the two home directories to see if there is any difference.

You will have to use gconf-editor to edit/change any values.

---

### Post by littlesatan on 2011-10-18
First of all, great idea, thanks.

Yes, the files are different. I copy %conf content  from new profile to "broken", 

beside that, only in "broken" profile I found that directories: AlpsPS@47@2@32@ALPS@32@GlidePoint
ImPS@47@2@32@Generic@32@Wheel@32@Mouse
Logitech@32@USB@32@Receiver
PS@47@2@32@Mouse

I move all of these dirs to ./disabled/

After logout/login - nothing changed, touchpad died during login.

---

### Post by blueridgedog on 2011-10-18
I don't think you can copy the files.  I think you have to use gconf-editor to change the entries in the corresponding locations.  The issue is clearly profile based.

---

### Post by littlesatan on 2011-10-18
I do not just copy the files, I copy lines from one file to another. There is only boolean parameters.
```

<?xml version="1.0"?>
<gconf>
    <entry name="touchpad_enabled" mtime="1318966990" type="bool" value="true"/>
    <entry name="tap_to_click" mtime="1318966991" type="bool" value="true"/>
    <entry name="scroll_method" mtime="1318952279" type="string">
        <stringvalue>two-finger-scrolling</stringvalue>
    </entry>
    <entry name="horiz_scroll_enabled" mtime="1318966992" type="bool" value="true"/>
    <entry name="disable_while_typing" mtime="1318966993" type="bool" value="true"/>
</gconf>

```As you advised, I recheck the fields through gconf-editor. And that was good advice, bacouse there was warning "this key has no schema". After recheking warning disappear.

But problem don't fixed.

Then I move entire "touchpad/" to ./disabled/. Folder "Touchpad" disappear from gconf-editor's tree.
After that I go to system preferences > "mouse and touchpad" and check all the options on "touchpad" tab. Folder "touchpad" returned to the place (in gconf-editor).
But touchpad still don't working.

---

### Post by blueridgedog on 2011-10-18
Are you opposed to deleting you gnome profile and starting over?  I am stumped otherwise.

---

### Post by littlesatan on 2011-10-19
I tried to rename .gconf to .gconf~ but that's doesn't solve the problem. Is there some other places for config files?

---

### Post by blueridgedog on 2011-10-20
Try renaming the directories .gconf, .gconfd and .gnome2.

---

### Post by littlesatan on 2011-10-20
Well, I tried, but with no luck.

---

### Post by crdlb on 2011-10-20
On 11.10, the settings are stored in dconf. You can run dconf-editor and go to org.gnome.settings-daemon.peripherals.touchpad

---

### Post by littlesatan on 2011-10-20
OMG, I check "touchpad-enabled" via dconf-editor and viola - touchpad is finally enabled.
Thank you guys for all the advices.

But where the settings are stored? Not in the system registry, I hope?

---

### Post by crdlb on 2011-10-20
> **littlesatan said:**
> 
But where the settings are stored? Not in the system registry, I hope?

~/.config/dconf/user, which is in fact a [binary database]("https://live.gnome.org/dconf#Design"), but there's nothing wrong with that.

---

### Post by blueridgedog on 2011-10-21
So the gnome configuration editor and the directory xml files are all legacy?

---

### Post by crdlb on 2011-10-21
> **blueridgedog said:**
> So the gnome configuration editor and the directory xml files are all legacy?

Yes, gconf is being replaced by GSettings and dconf. (GSettings is a generic API in GLib, and dconf is the backend)

---

### Post by blueridgedog on 2011-10-24
So we will need to carry forward all of the gconf and xml tools for years as to work with non-conforming applications?

---

