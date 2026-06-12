---
title: "Firefox unknown error"
date: 2009-11-29
forum: General Help
---

### Post by dadrc on 2009-11-29
This one is a little difficult to describe, so please bear with me.

I updated from Jaunty to Karmic without any problems, at least that's what I thought.
But ever since then, when opening a torrent from firefox (which should fire up transmission), I get the following error and nothing else happens:

> /tmp/<name>.torrent could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.Here's a list of things I already tried:

[LIST]
[*]Tried a lot of different torrent, so it's not related to that specific torrent
[*]Checked /tmp for the torrent, it's there and works if loaded into transmission manually, even though Firefox' Download Manager claims the download failed
[*]Deleted the mimeType.rdf as recommended in the Mozillazine KB [here]("http://kb.mozillazine.org/Unable_to_save_or_download_files")
[*]Edited the filetype association to use /usr/bin/transmission, which works if used outside of Firefox
[*]Started Firefox with a new profile
[*]Launched Firefox with another user
[*]Reinstalled Firefox and came across the reason why I posted this here instead of the Firefox forums:
[/LIST]
At first, I did not install firefox-gnome-support, which lead to a change: Instead of that error, the download works (launching transmission doesn't, but that's probably due to no gnome support ;)) When reinstalling firefox-gnome-support, everything is back to the state described above. I am running out of ideas on how to fix this, anyone got any hints or even a solution?

---

### Post by john newbuntu on 2009-11-29
Go to edit->preferences. In the main tab and the section where it asks where to save files to, make sure you can write to that folder/directory.  In my case, it is the Downloads folder where I can freely write and read from.  If not go to a terminal and do
```
chmod -R 755 Downloads
```
Retry the download.

---

### Post by dadrc on 2009-11-29
Thanks for the answer. The thing is, normal downloads work fine, but when directly opening a torrent, Firefox doesn't use the usual download directory (being ~/Downloads) but saves the file in /tmp to open it from there and delete it afterwards. Sorry if that wasn't obvious from the first post.

---

### Post by john newbuntu on 2009-11-29
Sorry then.  About the only thing I can suggest is is make sure that your versions of transmission, firefox and Ubuntu are up-to-date.
It works ok for me though. Transmission version 1.75, firefox v3.5.5, ubuntu 9.10 kernel 2.6.31-15-generic. Please use update manager to update all these.

---

### Post by dadrc on 2009-11-30
Mozilla Firefox 3.5.5
Transmission 1.75
2.6.31-15-generic #50-Ubuntu

Might have been helpful to include that in the first post, stupid me. Anyway, since I regularly run updates, I don't think any outdated package causes this.

What makes things even more weird: Directly opening pdf files from Firefox works perfectly, evince opens, no error there. So I guess there's something wrong with the firefox-gnome-support settings. Any way to check and/or alter them?

---

### Post by roblubbers on 2009-12-02
I have the same error

---

### Post by dadrc on 2009-12-02
Good to know I'm not the only one. Anyone got an idea what causes this?

---

### Post by ChurdCFG on 2009-12-04
I'm having the same issue here - I'm not sure if this is why, but I notice that Firefox is saving the files in the /tmp folder with read-only for the owner and that's it. Perhaps the permissions are too strict for whatever reason?

EDIT: D'oh!  Nevermind, I figured out that my default "Open With" bittorrent program didn't actually exist (I had to change it to use my bittorrent client, then all is well)

---

### Post by dadrc on 2009-12-05
Firefox uses 400 here, too. But opening the torrent with those exact rights manually works, so I don't think that's the cause.

And while a non-existing torrent client is definitly a good reason for it not to work, it's not the reason for my problem, since /usr/bin/transmission works just fine.

---

### Post by Cato2 on 2010-03-28
I believe there is a solution for this, or at least one worth trying out as it's quite easy for most people.  I had this when clicking on PDFs in Firefox 3.5.8 but the same fix should work for .torrent files as described here.  It may happen more frequently with Kubuntu, Xubuntu or other variants of Ubuntu.

I based this on [http://ubuntuforums.org/showthread.php?t=793388](http://ubuntuforums.org/showthread.php?t=793388) which refers to a bug with the Ubuntu version of Firefox, but I had the same problem with the Mozilla.com version.

If you are using the Ubuntu version of firefox (if you're not sure, this is what you are using), just do ```
sudo apt-get install firefox-gnome-support
``` - this installs a single library, libnkgnomevfs.so, which seems to fix this.  Restart Firefox to test.  I haven't tested this but it's a simpler version of what I did.

If you have installed the Mozilla.com version of Firefox, i.e. downloaded as a .tar.gz file and installed in its own directory, say /opt/firefox, here's what to do.  Tested on Ubuntu 8.04.

The exact .deb name will vary depending on your Ubuntu version - I'm on Ubuntu 8.04 so just use the .deb starting firefox-3.* that matches your Firefox version and distro.  Note that I used the firefox-3.0 .deb with Firefox 3.5.8, so it should work with any 3.x version of Firefox.

This procedure pulls in only one GNOME related library, so it's probably a better solution if you are using KDE (Kubuntu), XFCE (Xubuntu), etc.

```
sudo -i                # become root
apt-get install wajig        # great APT tool

# Get the .deb
wajig download firefox-gnome-support

# Copy it to a safer place
cd /var/cache/apt/archives
mkdir -p /root/debs/firefox-deps
cp firefox-3.0-gnome-support_3.0.18+build1+nobinonly-0ubuntu0.8.04.1_i386.deb /root/debs/firefox-deps

# Unpack the .deb (ar archive, with tarball inside)
cd /root/debs/firefox-deps
ar x firefox-3.0-gnome-support_3.0.18+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
tar xzvf data.tar.gz

# Put the library where it can be seen by Firefox
mkdir /usr/local/lib
cp ./usr/lib/firefox-3.0.18/components/libnkgnomevfs.so /usr/local/lib

# Test
export LD_LIBRARY_PATH=/usr/local/lib: 
firefox 

```
Hope this helps.  This has been annoying me for a while so I thought I'd document the fix.

---

