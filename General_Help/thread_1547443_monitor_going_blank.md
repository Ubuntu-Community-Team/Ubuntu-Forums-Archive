---
title: "monitor going blank"
date: 2010-08-06
forum: General Help
---

### Post by Turpin on 2010-08-06
This is a problem I always have trouble with and it seems to get more difficult to conquer with each Ubuntu release. I want to disable screen blanking. I've tried "xset s off -dpms s noblank s noexpose s off" and it still blanks the screen after about ten minutes.  I should mention I installed Ubuntu lucid using the mini.iso and then installed the LXDE desktop environment and a few fast-opening apps. 
I've tried installing xscreensaver for a few minutes just so I could get into its controls and make sure everything is disabled because for all I know, that mechanism may run even though xscreensaver isn't actually installed. Then I uninstalled it and rebooted.  And again, I leave the mouse alone for I guess about ten minutes and the screen goes black until I move the mouse or hit a key.  It happens also when I'm laying in bed watching a movie in VLC player.  Very annoying.  

I used to also add something to my xorg.conf that fixed this a couple years ago, but now the xorg.conf has gone out of style it seems, so I don't know if it's necessary to figure out how to create a valid xorg.conf that won't stop Buntu in its tracks.  I'm pulling my hair out here.  Anyone have any ideas? For what t's worth, my hardware is an EEE pc701, but I have this same problem on my old Athlon self-built computer running the same Ubuntu and LXDE combo.

---

### Post by cmcanulty on 2010-08-06
I have same deal after setting to never do it still happens.

---

### Post by Turpin on 2010-08-06
Surely there must be a solution.  How else can one watch a movie?  The xset command mentioned above is what fixed it for me in karmic.  But it doesn't fix it for me in...  okay, I lied, I'm actually using maverick meerkat.  I didn't want the reflex responses I was expecting if I admitted that ("It's not even finished yet").  But I think I was having this same problem in Lucid for the day or two I was using it before going insane with ambition and taking the leap further forward to maverick.  Using xset didn't stop the screen blanking.  Otherwise, as it turns out, maverick has been making me pretty happy so far.  But I need no screen blanking.

---

### Post by Turpin on 2010-08-07
Okay, I got it to work.  I haven't narrowed down which of these worked just yet and out of time right now, but I created a .desktop file called xset.desktop with these contents, 
[Desktop Entry]
Name=xset
Exec=xset s off -dpms
# Exec=xset s off -dpms s noblank s noexpose s off
Terminal=false
Type=Application

and placed it in /home/myusername/.config/autostart

, then I created /etc/X11/xorg.conf, because it didn't exist yet, and placed these contents into it:
Section "ServerFlags"
    Option "BlankTime" "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection

After doing these things, reboot.

and don't forget to insert at least one empty line at the end.  I forget which file it's important to have a blank line at the end for, it might be sudoers or fstab or xorg.conf or a couple of those for all I know, but it doesn't hurt anyway. I insert a blank line at the end of everything because I do know that if you don't leave a blank line at the end of certain system configuration files, the system doesn't boot, last I checked back in hardy anyway. Important note for noobs.

But yeah, I left it on all night and this morning I wake up and no black screen.  My desktop is there showing me what I want to see without having to move the mouse. Personally, if I don't want to see the screen, I turn the monitor off.

---

### Post by Turpin on 2010-09-09
It was the xorg.conf that worked. You know, xorg.conf, that configuration file that we're not supposed to need any more, being phased out for, I imagine, a more user-friendly approach. 
But why must we resort to such insane measures to simply not have our screens hide themselves?  Imagine if I were new and less confident of my ability to find the answer to this very seemingly basic thing.  I would have been back to the evil OS I suppose. I guess evil wouldn't be evil if it weren't tempting, but that doesn't mean good has to be retarded, does it? 
Screen not going black.  Would be a nice feature, you think?????? Perhaps even a good default???????????
Sorry for the anger.  I've just not seen this fixed since edgy and I seem to keep running into it again every time I install a new release. It's cost me many frustrating hours and kept me apologizing for Ubuntu in front of friends. And I hate that, because I want to say to them it's ready for them, non-geeks.

---

### Post by bdaman80 on 2010-12-29
I am trying to achieve the same outcome as you are, but I am not having the same results as you.  I'm on Lucid, but have a special challenge.  I am using a base cli install, with x.org, but no window manager or desktop.  I've tried some "setterm" commands i've found online.  Tried both of your options, but it still times out.  I dont care if it times out in the regular cli interface, but once I 'startx' i want the screen always on.

Thanks in advance for any suggestions.


I just found that the 1st time after the xorg.conf trick, zi actually had to type - /usr/bin/startx  .  After that 1 time, its all good agsin

---

