---
title: "Transmission has started getting Permission Denied errors when saving new torrents"
date: 2010-01-16
forum: General Help
---

### Post by jamesisin on 2010-01-16
Transmission has started giving me errors when I download a new torrent file.  It has stopped being able to create the new file (ie touch) to begin the download.

Error: Permission denied (/path/to/specific/file/in/new.torrent)

Old torrents are still running to the same drive location.  No permissions have changed.

What's going on?

---

### Post by jamesisin on 2010-01-16
Ok, I have some more information to report.

My torrents download into a drive we'll call TD (for torrent downloads) which is mounted in /media:

/media/TD

I have Transmissions set to save in that location (via its preferences).  I can manually set the location for any of these new torrents and I get the same error message.  I have tried /media/[different hdd] and ~/Music.

The interesting thing about the error is the location in the path.  The path in the error shows /media/[name of torrent folder] which is clearly wrong.  Also if I open the properties of the torrent on the Information tab under Location: I see /media.  Also wrong.

I have also tried unmounting and remounting the drives, changing the location, restarting Transmission, and rebooting.  All to no avail.

What is Transmission doing?

---

### Post by jamesisin on 2010-01-16
I had a vision...

I changed location but told Tm that the files were already there and this actually changed the location.  Once that was taken care of starting the torrent running again did not get the error.

Strictly speaking, the files were not already there as they did not yet exist, but it solves the problem so it's good enough for me.

Hope that helps someone else.

---

### Post by happysam on 2010-01-18
Had the same problem after recent update: current version Transmission 1.75 (9117)


the torrents properties had all new torrents listed as being located in /media.

fixed as above by setting individual torrents' location and telling it that the files were already there.


thanks for the tip!!!!!!!

---

### Post by jamesisin on 2010-01-18
Yeah, I'm wondering if there might not be a bug in the Move Files option.

I'm running 1.76 (9395).

---

### Post by mojorising5150 on 2010-02-04
Oddly enough,,,, make sure you not only open the torrent from your browser to bring up transmission, but also download the torrent through transmission as well when you're selecting your files.... K.I.S.S

---

### Post by jamesisin on 2010-02-04
> **mojorising5150 said:**
> Oddly enough,,,, make sure you not only open the torrent from your browser to bring up transmission, but also download the torrent through transmission as well when you're selecting your files.... K.I.S.S

Not sure I'm following you.

---

### Post by ron999 on 2010-02-04
@ jamesisin
Hi
Transmission has been updated to v1.83.
There's a how-to for upgrading here:-[http://ubuntuforums.org/showthread.php?t=1391718]("http://ubuntuforums.org/showthread.php?t=1391718")

---

### Post by jamesisin on 2010-02-04
> **ron999 said:**
> Transmission has been updated to v1.83.
There's a how-to for upgrading

Thanks.  I prefer using repositories.  I am currently using this one:

[http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu)

---

### Post by cremate on 2010-02-04
I'm still getting the "Error: Permission Denied" problem, even with the repo install.  I also got a "Error: Minimum announce = 60" on a seperate tracker.  Not really sure whats going on here?!

---

### Post by ron999 on 2010-02-04
> **jamesisin said:**
> Thanks.  I prefer using repositories.  I am currently using this one:

[http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu)

Yes, I understand.
Intrepid is still at v1.76 in that repo. Hardy, Jaunty and Karmic are at v1.83.
:)

---

### Post by jamesisin on 2010-02-05
Not as of my latest updates.

---

### Post by ron999 on 2010-02-05
Very funny.
The repo's been updated on February 5th 2010, since my previous post, for Ubuntu 8.10.

---

### Post by Rodnox on 2010-03-22
The Thread is marked as [SOLVED] ... well .. I;ve updated the client and still get the errors.  Whats the story?

---

### Post by radioxid on 2010-04-24
I also get this error, in 1.75, and solved it, for now. For me it was a privileges matter as chown-ing it made it, and so forth not a bug.

---

### Post by jamesisin on 2010-04-24
> **Rodnox said:**
> The Thread is marked as [SOLVED] ... well .. I;ve updated the client and still get the errors.  Whats the story?

Which version of Transmission are you running?

---

### Post by arun abraham on 2010-05-29
change the download directory into any of the home directory folders or download directory itself...by configuring       preference--->torrents tab.Delete existing torrent and start after adding once again

---

### Post by tonio.ferritto on 2011-03-08
> **arun abraham said:**
> change the download directory into any of the home directory folders or download directory itself...by configuring       preference--->torrents tab.Delete existing torrent and start after adding once again

Had the same Problem here. But instead of deleting torrents and start over i simply made a symlink to the location the client was complaining access denied. That solved the problem...

(ln -s /media/real_dir /media/transmission_complained_dir)

---

### Post by tonewheelkev on 2011-05-18
All of a sudden...have the same problem, and can't make head nor tail of solutions suggested so far in THIS thread...


Please help

---

### Post by khopek on 2011-06-01
> **tonewheelkev said:**
> All of a sudden...have the same problem, and can't make head nor tail of solutions suggested so far in THIS thread...


Please help

1. Right click on a torrent in Transmission that is giving you the permission denied error.

2. Choose 'Set Location' from the right click menu 

3. Choose (or in my case it was already correct) the location where your torrents are supposed to be saved from the dropdown menu

4. Check the 'Local data is already there' radio button.

---

### Post by cheekymonky2010 on 2011-06-08
try saving it to your desired location through "other" in the transmission options window.

---

### Post by kjamal on 2012-07-19
Had the same problem on mac and solved it. 
Observations: 
torrent files downloaded to: torrents downloaded to download directory on Mac
Torrent downloads: on external drive
Triggering event: when connection to external drive is interrupted and must be re-established manually.
Solution: 
1.ensure external drive is connected and visible in finder with its familiar icon
2.carry disk repair and verify using disk utility - just a precaution and optional
3.start up transmission > preferences>transfers  and reselect default file location and save incomplete file in to the external drive. In fact, re-select all references to the previously disconnected drive. 

Hypothesis: looks like transmission may be storing the file references in a different format. When the drive is reconnected, MAC probably uses a different identifier for the drive which doesn't correspond to the one stored by transmission. 

have tested it several times and able to duplicate situation and apply resolution every time.

Cheers,
K

---

### Post by nothingspecial on 2012-07-19
Thanks for the info but this thread is old.

Closed.

---

