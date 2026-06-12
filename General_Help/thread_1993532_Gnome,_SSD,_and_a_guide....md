---
title: "Gnome, SSD, and a guide..."
date: 2012-06-02
forum: General Help
---

### Post by JiuJitsu500 on 2012-06-02
[FONT=Arial, sans-serif][SIZE=3]Hello all you crazy GNU/Linux fans!

After using Ubuntu almost exclusively for a few years now, and attempting to catch up on the kernel options as they come out for things like flash and solid state memory, processors, and a slew of other stuff, I have put together a guide for myself I would like to share. Instead of googling everywhere to find out how to enable TRIM, edits for various files, and all-around optimization, I have everything I've done minus the errors and screw-ups (I've re-installed 5 times getting it right), and believe this to be pretty good.

Might I note my specs, however, and note that a LOT of this is through the GUI, as I'm no expert, and it's just easier generally and does the job just fine. I also note that since Precise is an LTS, I won't be switching for a long time.

Asus ROG Customized G53SX, w/2xOCZ Vertex 3 SSD's (each 120GB, Precise on one, Windows 7 on the other), Core i7 (forgot the model, it's 2.4GHz Quad core), Nvidia GeForce GTX 560M 2GB, 24GB 1866 MHz DDR3 RAM. The rest I don't believe matters much, and yes, the RAM is excessive, I know.

So, enough about me, right? The ONLY remaining question, is that after my research, would any of the Dev's or more advanced user like to comment on anything redundant or done incorrectly????

Here we go:

First, as I had an SSD, I would liked to have enabled TRIM, which is very easy... edit the /fstab (sudo gedit /etc/fstab) and simply find the line that has your SSD's ID (UUID xxxxxx....) and just before the "error", add "noatime,discard," so it looks like "UUIDxxx..... noatime,discard,error...." - Save and exit.

Secondly, its annoying that the new ubuntu's wont show you the startup apps, so run this command:[/SIZE][/FONT]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop[/SIZE][/FONT][/COLOR] [FONT=Arial, sans-serif][SIZE=3]Then update your sources by editing and adding everything you want to in the Update manager settings.

Then, to update them and add the ability to play encrypted DVD's later, run this command and wait for it to finish:[/SIZE][/FONT]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]*sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update*[/SIZE][/FONT][/COLOR] [FONT=Arial, sans-serif][SIZE=3]Then, if you are like me, and hate unity (I gave it a fair shot over 3 releases, trust...) and prefer gnome-shell (we'll remove unity later), and to install the actual library to play those DVD's run this:[/SIZE][/FONT]
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]sudo apt-get install gnome-shell libdvdcss2[/SIZE][/FONT][/COLOR]
 [FONT=Arial, sans-serif][SIZE=3]
Now, Restart the computer into Gnome-Shell. Or if you left Unity, leave out the "gnome-shell" part in the last command, and restart anyway.

Now, I prefer to install all my replacement programs before removing the ones I don't like, don't use, or don't prefer. So here's my short list (can find them all in the software center if you click the "show technical items":

Bleachbit, GParted, Preload, sysv-rc-conf, Orphaned Package Remover, Synaptic Package Manager, GIMP, Audacity, gnome-tweak-tool, java and iced tea (java 7, as I believe the restricted extras installs 6 still), Deluge, Chromium, VLC, Skype, Restricted extras, and WINE.

Those are what I like, you may prefer better programs however.

Once all is installed, run "sudo sysv-rc-conf" and disable the things you do not need at boot. This tool is a run-level configuring machine like BUM, but I dont need a GUI for a one-time app. I disabled avahi-daemon, bluetooth, brltty, cups, dns-clean, pppd-dns, rsync, saned, and speech-dispatcher (if you have a scanner and printer, leave cups and saned on).

Since I do not use any universal access, I also edt the file: /usr/share/gnome-shell/js/ui/panel.js (open with your favorite text editor) and find the line "[COLOR=#000000]a11y':[/COLOR][COLOR=#000000]imports.ui.status.accessibility.ATIndicator and simply comment it out by adding "//" without the quotes in front of it. I also found this easier than using an extension to do something so simple.[/COLOR][/SIZE][/FONT]
 

  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]Then, I need a screensaver, since the built-in one doesnt seem to work with the shell:[/SIZE][/FONT][/COLOR]
  

 [FONT=Arial, sans-serif][SIZE=3]sudo apt-get remove gnome-screensaver[/SIZE][/FONT] [FONT=Arial, sans-serif][SIZE=3]sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra[/SIZE][/FONT] 

[FONT=Arial, sans-serif][SIZE=3]And Viola!!! A working screensaver. The lock screen still seems to be buggy and crashes, burns, and ruins everything for me, but I dont use it anyway.[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]
Now, I changed my startup apps, like removing bluetooth and additional drivers (you should only need this once, then manually after that). If you hunt for updates manually like I do, remove update manager too and the useless junk. I used to install and add GUAKE in here, but since CTRL+ALT+T works again to open a terminal (the shell used to have some dcong and gcong mistranslations, but works now), but guake is no longer necessary for me. 

However, you must add the XScreensaver, so click "add" and name it whatever you want, and describe it how you want, but the command is "xscreensaver -nosplash" without the quotes.[/SIZE][/FONT]

[FONT=Arial, sans-serif][SIZE=3]Now restart again. Why? I don't know, but I needed to here for some reason. After the restart I think it's a good idea to run additional drivers, and add everything you need.[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]

NOW, the grub edits, as I have an i7, I find this to be best. Open up in your favorite editor the /etc/default/grub and find te following lines:[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]"quiet splash" after some other command, and the line GRUB_CMDLINE_LINUX=""[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]

Change "quiet splash" to "quiet spalsh[/SIZE][/FONT][COLOR=#000000][FONT=Arial, sans-serif][SIZE=3] pcie_aspm=force i915.i915_enable_rc6=1 profile" (NOTE: you do not need the "pcie... rc6=1" if you do not have an i7 I don't think, so don't add it unless I'm wrong)[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]Inside the quotes after LINUX in the other line, add "elevator=noop"[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]The "noop" seems to be best and give best boot time performance, especially on an SSD[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]the you HAVE to run this: "sudo update-grub" or nothing you just did will matter.

Now, add a repository real quick (I did this because the GNOME team comes out with updates faster than Ubuntu gets them to you).[/SIZE][/FONT][/COLOR]  [COLOR=#222222][FONT=Arial, sans-serif][SIZE=3]"sudo [/SIZE][/FONT][/COLOR]*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]add[/SIZE][/FONT][/COLOR]*[COLOR=#222222][FONT=Arial, sans-serif][SIZE=3]-apt-repository [/SIZE][/FONT][/COLOR]*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]ppa[/SIZE][/FONT][/COLOR]*[COLOR=#222222][FONT=Arial, sans-serif][SIZE=3]:[/SIZE][/FONT][/COLOR]*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]gnome3[/SIZE][/FONT][/COLOR]*[COLOR=#222222][FONT=Arial, sans-serif][SIZE=3]-team/[/SIZE][/FONT][/COLOR]*[COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]gnome3"[/SIZE][/FONT][/COLOR]*
 [FONT=Arial, sans-serif][SIZE=3]
Now go ahead and go into update manager and make sure this repo is checked, and either click "check" in the manager or run "sudo apt-get update && sudo apt-get upgrade" and let that finish.[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]Now, actually update everything by clicking "install updates" or if you used the terminal command just now, its already updated.[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]Restart as it should say, as the Kernel is likely updated now, and everything else.[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]

The next part is CIRITICAL. You added "profile" to the GRUB. What this does is tell the system to look only for the necessary drivers for your specific computer. It finds everything you need to boot right, and you don't need it to look for everything else, or look for anything except what you need. So, go back into that file (/etc/default/grub) and take out the word "profile" after quiet splash, but leave everything else. Then, again, and this is critical, AFTER removing "profile, save and exit, then run "sudo update-grub"[/SIZE][/FONT]  [FONT=Arial, sans-serif][SIZE=3]Now, if ou are advanced enough, purge through synaptic everything you do not want or need. (i.e everything AMD or radeon if you have nvidia and intel, or vice-versa, etc... do some googling here).[/SIZE][/FONT] 

Alternitavely, anything you downloaded to replace something else, you can remove the replaced app from the software center.
[FONT=Arial, sans-serif][SIZE=3]
Then lastly, remove unity if you like (just make sure you are in the shell or XFCE or any other environmet:[/SIZE][/FONT]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=3]sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications unity-common indicator-sound indicator-power indicator-appmenu libindicator7 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-2.0-0 nux-tools[/SIZE][/FONT][/COLOR] 

You have to re-install deluge if you have it, maybe some other apps too. They depend on one of these to run right, so -re-install those apps afterward to keep unity gone.
[FONT=Arial, sans-serif][SIZE=3]
NOTE: some of these packages my have a different name since you updated, this command is kind of old. It aslo does not remove EVRYTHING unity, as some libs are needed for other apps, like usb-creator. Either way, this removes unity.[/SIZE][/FONT] 

Lastly, use the Orphaned Remover to remove leftover config files or packages you dont want. Run bleachbit too and clean up a little.
[FONT=Arial, sans-serif][SIZE=3]
It's also a true story that you can simply install the GNOME-Shell remix, but I didnt have that option, and found this to be better overall anyway. I might be wrong, but to me this worked better. I have to say though, I am THOROUGHLY impressed with this version of Xubuntu, to to avoid most of the mess, just install that. But, I have LOTS of power, so I opted for the heavier Ubuntu with Gnome-Shell. I also do not like Kubuntu either, or KDE in general as a note, but if you do, you can avoid some hassle going that route too.[/SIZE][/FONT]  

I did a LOT more than this too, but most of that was to customize, not harder to find crap I've had to look around for. Like Kernel options and such. Abother thing though, in 11.04 I remember parralellizing ureadahead, and correcting the I/O scheduler so everything knows the SSD is NOT a rotational drive... but I do not remember how. It's some scripts to edit or make, but I forget.

[FONT=Arial, sans-serif][SIZE=3]So, What do you guys think?[/SIZE][/FONT]

---

