---
title: "Docking station -&gt; Syncmaster 2343"
date: 2009-11-11
forum: General Help
---

### Post by Nomadic Logic on 2009-11-11
Good morning, all.

I've recently installed 9.10 on my Dell D820.  Everything runs fine on the laptop, but when I try to dock, I run into issues.

Docking to a basic Dell docking station with a DVI out to a Samsung Syncmaster 2343 (23") is not working.  I end up having to switch to a command line tty, and am never able to get the GUI up and running.

I have the latest nVidia software installed via the Ubuntu repositories.

Any help for this Linux newbie is appreciated.

---

### Post by Giblet5 on 2009-11-11
Your DVI cable isn't passing DDCC or EDID info to the laptop's GPU.

While docked, if you have no display at all, hit Fn+F5 to switch back to the laptop's display. Click on System -> Preferences -> Display and you'll get a dialog asking whether you want to use the vendor's display tool. Answer Yes.

This is the nvidia-settings tool.

Click on "X Server Display Configuration"

There will be a drop-down widget labeled "Model:". Click the drop-down and select the SyncMaster.

Click on the "Resolution:" drop down and select a safe resolution. Click "Apply".

The display should switch to the SyncMaster at the requested resolution.

Did it?

If so, do this:

Exit the nvidia-settings tool.

Bring up a terminal window and enter ```
sudo nvidia-settings
```

Repeat all of the above settings steps.

Now click the "Save to X Configuration File" button.

Exit nvidia-settings.

Undock the laptop. The display should shift to the laptop.

Dock the laptop. The display should shift to the SyncMaster.

Now you owe me coffee in accordance with the prophecy.

---

### Post by Nomadic Logic on 2009-11-11
I think I have a bit of a wrinkle to throw in.

The D820 doesn't have DVI out.  Only the docking station does.

I dock the laptop with the lid closed and run only off the Syncmaster when in the office.

---

### Post by Giblet5 on 2009-11-11
That shouldn't matter.

Does the dock prevent you from opening the laptop? If not follow the directions.

"To find if a thing is possible, try it."
-Napoleon Bonaparte's IT guy

---

### Post by Nomadic Logic on 2009-11-11
It does.  The docking station doubles as a monitor stand.

Current situation:

- Able to run dual monitor if undocked.  Laptop + VGA to Syncmaster

- Unable to pull up anything but command line tty when docked.

> **Giblet5 said:**
> That shouldn't matter.

Does the dock prevent you from opening the laptop? If not follow the directions.

"To find if a thing is possible, try it."
-Napoleon Bonaparte's IT guy

---

### Post by Giblet5 on 2009-11-11
> **Nomadic Logic said:**
> It does.  The docking station doubles as a monitor stand.

Current situation:

- Able to run dual monitor if undocked.  Laptop + VGA to Syncmaster

- Unable to pull up anything but command line tty when docked.


Did you try hitting Fn+F5 (on the laptop's keyboard) while it's docked?

Fn+F5, on every laptop I have seen since 1992, will switch the laptop's graphics display between docking mode and internal display mode.

Your laptop's F5 key even has a picture of a display on it to remind you what it does.

---

### Post by Nomadic Logic on 2009-11-11
I would, but like I said:  the docking station prevents me from opening the lid when docked.  The docking station doubles as a monitor stand.

---

### Post by Giblet5 on 2009-11-11
Oh. I misunderstood that "It does." comment.

So, it works if you connect the monitor to the laptop's vga connector. Let's go with that.

Does the SyncMaster automatically switch inputs? Mine doesn't. I have to push the "Input" button until the monitor displays "DVI-D".

Does the dock have a vga connector on the back? Mine has both VGA and dual-DVI. If it has VGA, have you tried using that?

Try following the instructions I posted about saving the X configuration from within nvidia-settings. Just don't use "Auto" for the Resolution because that's what already doesn't work.

Then try docking.

The idea is to give your X display a configuration that it can use when it can't detect the monitor type, and Xorg is not detecting the monitor type from the docked configuration.

---

### Post by Nomadic Logic on 2009-11-11
> **Giblet5 said:**
> Does the SyncMaster automatically switch inputs? Mine doesn't. I have to push the "Input" button until the monitor displays "DVI-D".
Yes, it switches between analog and digital automatically.  When I dock right now, it toggles back and forth 2 or 3 times and gives up.

> **Giblet5 said:**
> Does the dock have a vga connector on the back? Mine has both VGA and dual-DVI. If it has VGA, have you tried using that?
I have actually tried going VGA->VGA from dock to monitor.  Same result.

> **Giblet5 said:**
> Try following the instructions I posted about saving the X configuration from within nvidia-settings. Just don't use "Auto" for the Resolution because that's what already doesn't work.
Giving that a go now.

---

### Post by Nomadic Logic on 2009-11-11
Ok, when I click the save to X configuration file button, I get "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

---

### Post by Nomadic Logic on 2009-11-11
Success!

Your instructions above, coupled with the instructions on how to resolve the failure to parse xorg.conf have remedied my problem.

Who knows what's going to happen when I undock, as I disabled the laptop screen in order for this to work, but that's okay for now, I guess.

Thanks for the help!

---

