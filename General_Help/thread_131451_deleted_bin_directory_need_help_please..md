---
title: "deleted /bin directory need help please."
date: 2006-02-16
forum: General Help
---

### Post by pippin on 2006-02-16
i accidentally  and very stupidly deleted my  /bin directory using "rm" command in gnome-terminal.am now unable to access gnome-terminal (application gnome-terminal has quite unexpectedly) or my cdrom drive to get at my backup cd. i'm quite new to all this and was hoping wouldn't have to  do a entire reinstall. any help much appreciated. o yea wasnt sure if this was the right forum to post in.:confused:

---

### Post by psusi on 2006-02-16
Yes, you will need to reinstall or restore from backup.

---

### Post by wrtrdood on 2006-02-16
You might be able to copy the directory back from a live CD to at least get to the point where you could restore from the backup.

---

### Post by pippin on 2006-02-16
cheers for your replies----

"you might be able to copy the directory back from a live CD to at least get to the point where you could restore from the backup."

 could you you explain how i could do the above as i really don,t want to lose everything on HD. thanks:)

---

### Post by wrtrdood on 2006-02-16
Boot from the livecd, mount the hard drive root partition on a temporary mount point (e.g. /mnt), copy /bin to the hard disk /bin directory.  Something like this:

After livecd is booted:

sudo mkdir /mnt/temp

sudo mount /dev/hda1 /mnt/temp

ls /mnt/temp  [ just to be sure it's the root partition - may not be hda1]

sudo cp -r /bin /mnt/temp

reboot and restore...

---

### Post by pippin on 2006-02-16
thanks a lot,  wrtrdood   i'll give that a go.:-D

---

### Post by psusi on 2006-02-16
Or just restore the backup using the livecd.

---

### Post by pippin on 2006-02-16
hi again 
  i followed your instructions but after "sudo cp -r /bin /mnt/temp"
   it gave me the following error:  
 "cannot create symbolic link "/mnt/temp/bin/lspci" :operation not permitted"  etc. i'm not sure what this means .


also  i don't know how to follow psusi's advise as my laptop only has one cdrom.  cheers once again

---

### Post by wrtrdood on 2006-02-16
Such is the problem with killing the /bin directory.  You'll probably run into a few programs that are actually stored elsewhere but have what is known as a symbolic link in the /bin directory.  This is one of them.  What that means is that it has a conflict with copying that file because it's not the actual file.  You can see this with the *ls -l* command on the source file:

ls -l /bin/lspci

should show you something like:  /bin/lspci -> /usr/bin/lspci

Which simply means that the program is actually in /usr/bin.

This one's not critical since this command is used to display the devices on the PCI bus. 

I agree that restoring the backup directly is possible but with a livecd boot it can get a bit more complicated I was trying to avoid that.  Instead, my suggestion was to get enough of the /bin data back to at least boot normally.

---

### Post by pippin on 2006-02-16
can't thank you enough
i should have used hda3 and not hda1, i just didn't check it properly the first time. anyway redid it and it worked a treat.:D 
so thanks once again you saved me from a  heap of pain and anguish:mrgreen:

---

### Post by wrtrdood on 2006-02-17
You're quite welcome.  Beats having to do a complete reinstall which happened to one of my users one time.  Trouble is, he did an rm -r as root at the root level.  Fun.  That was a Unix box whose restore media was a pile of floppies -- sheesh.  I finally had it back up by the end of the day...

---

