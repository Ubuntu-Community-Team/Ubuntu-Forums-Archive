---
title: "Something went strangely wrong here"
date: 2011-05-07
forum: General Help
---

### Post by lynchster93 on 2011-05-07
A while back I was going through the Ubuntu Software Center, and I went to the "Already Installed" category to uninstall un-needed programs. I don't have a list of programs I erased, but from what I remember it was only the Media Players. (This was before I decided to start using my laptop for music).

Now for some reason a little orange caution triangle with a "!" in the middle keeps appearing on the top panel, I click on it and it brings up the Update Manager. It says at the top, "System is up-to-date" then "The last successful update was 38 days ago".

As for the audio/video part of the situation, I can't even re-download VLC or ANY media player for that matter, it keeps saying "Requires installation of untrusted packages" then "The action would require the installation of packages from not authenticated sources." In the list area it list the so called packages that are needed, which are as listed "libaudio2 libmng1 libqt4-dbus libqt4-xml libqtcore4 libqtgui4 libsdl-image1.2 libtar libva-x11-1 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 vlc vlc-plugin-notify".

So, whats the deal here? I'm confused as to what to do, can I do a "master reset" or something? Solutions would be greatly appreciated!

---

### Post by Joe of loath on 2011-05-07
What's the output of:

sudo apt-get update

sudp apt-get upgrade

---

