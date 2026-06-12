---
title: "IPod Classic (6th) -- songs not detected after syncing with rhythmbox"
date: 2011-08-11
forum: General Help
---

### Post by urukrama on 2011-08-11
I'm trying to add music to an iPod Classic 6th Gen. (160 GB) through Rhythmbox. The iPod shows up in Rhythmbox, and I can transfer music to it, as well as see music that is already on the device. 

However, when I eject and disconnect the iPod, it tells me there is no music on the device (including the music that was already on it), even though the space the entire library takes up is indicated in the Settings > About (though there too not recognised as either music, video, etc.), and I can see the files on the disk when I connect it to the computer.

When I connect it to Windows XP, Itunes tells me it needs to restore the iPod, and I lose all the files when the disk is reformatted. 

I tried [resetting](http://support.apple.com/kb/HT1320?viewlocale=en_US) the iPod, hoping that would recreate the database (as it does on a Creative player I own), but to no avail.

In case anyone suggests to use Gtkpod instead: I tried, but it just exits after the splash screen.

I'm helping someone move to Linux, and this is one of the main obstacles. I'm not very familiar with iPods (or Rhythmbox for that matter), and what comes up in a forum and internet search doesn't offer much assistance. I would appreciate any help I can get.

---

### Post by urukrama on 2011-08-15
Just to update and add some more info about the problem:

I tried Banshee too, which had the same results. I could upload music and play the music on the iPod from within Banshee, but when I disconnected the iPod, it told me there was no music on it. When I reconnect it, though, I can still play the music from within Banshee or Rhythmbox.

I also tried Amarok, with similar results. I can upload music to the iPod from Amarok, and play that music from within Amarok, but the iPod, when disconnected, does not recognise any of the tracks, including those uploaded from within iTunes.

I tried Floola, which did not detect the iPod to begin with.

After uploading music through Banshee or Rhythmbox, when I reconnect the iPod to Windows XP and iTunes, it tells me it cannot read the iPod and asks me to restore it to factory settings, erasing all the music. I can upload files without any difficulties using iTunes. The problem seems to be on the Linux end of things.

---

### Post by cottfcfan on 2011-08-15
Its an old post, but could this help:
[http://downloadsquad.switched.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/](http://downloadsquad.switched.com/2008/03/18/enable-support-for-7th-gen-ipods-in-ubuntu/)

---

### Post by urukrama on 2011-08-15
Thanks cottfcfan, that helped, though I also had to install libgpod-common, which wasn't pulled in as a dependency.

For those with a similar problem, here's how I fixed it (based on the instructions in the document cottfcfan linked to): 

Restore your iPod on Windows XP in iTunes. This will erase your entire iPod, so if you have music on your iPod you don't want to lose, connect it first to your Linux computer, access the iPod in your file manager and copy the files over to your computer (they should be in iPod_Control if I remember correctly).

Next, connect it to your Linux computer and before you copy any music to it, use the following command to find your iPod's Firewire Number (see the above linked page for more info):

```
sudo lsusb -v | grep -i Serial
```

You'll see several serial codes; you'll need the sixteen digit one. Copy that, and then run the following command:

```
sudo gedit /mnt/ipod/iPod_Control/Device/SysInfo
```

In my case this was an empty (nonexistent) file, though I've found some info online that indicates that file might already contain some data. In any case, add the following to that file:

```
FirewireGuid: 0xffffffffffffffff
```

Where ffffffffffffffff stands for the sixteen digit Firewire number you've gotten earlier. Save the file and close it. Don't try to copy music to your iPod before you do this, as your iPod's database won't properly build. I disconnected and reconnected the iPod at this stage, but I'm not sure that is necessary.

Then open Rhythmbox and copy your music to the iPod. Don't forget to disconnect the iPod from within Rhythmbox before you unplug it when you're done.

---

### Post by dejlig on 2011-08-24
Thanks!  Saved me from having to get a new music player...

---

