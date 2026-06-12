---
title: "Volume Control not working w/ Keytouch"
date: 2006-06-10
forum: General Help
---

### Post by Doytch on 2006-06-10
Hey, I have an MX3000 combo, whcih comes with a MX3000 keyboard and MX600 Laser Mouse.  

I downloaded keytouch and I configured it easily, everything worked, but when I restart, the volume control doesn't work anymore.  Before restarting, you can see the visual indicator and the volume changes, but after restart, there's no indicator, and the volume doesn't change.  

This was all using the Amixer plugin, so I tried using the KMix plugin, which didn't help, probably because I don't know how to get KMix to act as the mixer.  

I'd really like the volume keys to control the master sound(the one you can control using the button on the taskbar).  If anyone has any ideas regarding that, it would be great.

Thanks, Mark D.

EDIT: After looking some more, I've realised I want the volume keys to control the GNOME ALSA Mixer.  If that helps any.

---

### Post by Doytch on 2006-06-10
OK, for anyone who had this problem, this is how I solved it.

1) I got aumix-gtk from Synaptic.  You might need to display all the repositories, since this one appears to be in the Universe.

2) Next, I opened up Keytouch, and for the 'Volume Up' command, I told it to run the program "aumix -v +5", without the quotes.  For 'Volume Down', it should run "aumix -v -5".

Now, the only bad thing is that it doesn't pop up a little display when you change volume.

For a duct-tape solution regarding mute, use the program "aumix -v 0".  It's pretty crude, since it doesn't act like a toggle, it just quickly sets the volume to 0.

If anyone has any better ideas, that'd be awesome :)

---

