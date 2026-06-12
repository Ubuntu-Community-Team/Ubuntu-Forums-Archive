---
title: "How do I copy Shotwell data to a new install?"
date: 2012-04-26
forum: General Help
---

### Post by x-shaney-x on 2012-04-26
I have copied ~/.shotwell and ~/.gconf/apps/shotwell to my new install but after launching, I had to reconfigure almost all settings.

To top it off, I have all my photos in dropbox for synchronising between devices.
After launching shotwell, I find all my photos are untagged again and I don't really fancy going through several thousand photos re-tagging them.

I had the box checked in shotwell to write metadata to files and in the previous install every file was tagged.

<EDIT>
After installing and running Gthumb, all the tags ARE still embedded in the files so something is going wrong in shotwell.

---

### Post by x-shaney-x on 2012-04-26
Well this gets weirder:

I made a note of some photos that are showing as untagged then looked at the file properties, which also showed no signs of tags.

I then looked at the properties of the same files in a backup I made earlier today and all the ones I checked WERE showing the tags in the backed-up files.

So I deleted all the files in dropbox and replaced them with the backups, checked the file properties on some of them and they showed tags.
I then deleted my shotwell data and started it from scratch, it picked up all the tags and I created a custom search and it listed NO photos as un-tagged.

I started showell up again 5 minutes later and again, loads and loads of missing tags, which were no longer in the file properties again.

---

### Post by eric-yorba on 2012-04-26
Sounds like it's a bit late to point this out, but there's items in the Shotwell FAQ about this very topic:
[http://redmine.yorba.org/projects/shotwell/wiki/ShotwellFAQ#How-can-I-move-my-photo-files-from-one-directory-or-hard-drive-to-another](http://redmine.yorba.org/projects/shotwell/wiki/ShotwellFAQ#How-can-I-move-my-photo-files-from-one-directory-or-hard-drive-to-another)

FYI, modern versions of Shotwell (and all Gnome-y apps) no longer use GConf.

---

### Post by x-shaney-x on 2012-04-27
Right, started from scratch then:

1.  Deleted ~/.shotwell
2.  Deleted ~/.gconf/shotwell
3.  Deleted all my photos from dropbox
4.  Restored the photos to dropbox from yesterdays backup
5.  Copied over ~/.shotwell from my previous install
6.  Launched shotwell
7.  It auto-imported all the photos, including ALL the tags
8.  Checked for un-tagged photos and nothing was listed at all
9.  Closed and re-launched shotwell
10. Most tags still there but several hundred un-tagged photos now and the tags have gone from the file properties again.

At that point I noticed most of the photos folders in dropbox are re-syncing.
It appears that for whatever reason, shotwell IS seeing the tags at first but then is removing tags from those photos, hence dropbox re-syncing to update the files without tags.

Should mention, when I talk about file properties, that is right-click > Properties > Image > Keywords in nautilus.

Also, my ~/Pictures folder is symlinked to a pictures folder in dropbox.
I have now tried taking dropbox out of the reckoning and copied the backups directly to ~/Pictures but still get the same problem.

---

### Post by x-shaney-x on 2012-04-27
It gets stranger still:

I deleted all the photos in dropbox once again, replaced them with the backups once again but this time didn't touch the .shotwell folder.

Ran shotwell and the progress bar appeared, saying it was writing metadata to files and sure enough, it has put back all the missing tags.

Can't imagine what the problem was but hopefully this is resolved now.

Just dreading what happens when I update the missus' machine which has the same dropbox photos.

---

