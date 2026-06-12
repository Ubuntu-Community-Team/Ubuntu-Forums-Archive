---
title: "Assign Drive Letter to Windows Share"
date: 2011-02-03
forum: General Help
---

### Post by justindublin on 2011-02-03
Hey Guys,

Searched 4 hours on this, trawled through 100s of post but its now 2am here (Ireland) so I'm giving up and posting my question.

I've a Windows and a Ubuntu Machine on the same network.
I've a shared folder on my Windows machine.
I need to permanently map it to drive letter in Ubuntu, just like a hard disk.

Think of mapping a network drive in windows, I need to do the exact same thing.

Is there a way? I've honestly gone through about 500 posts explaining different ways and I go none working. Is there a GUI for this?

I know there is something called mounting, but I need it to be a drive letter for my program to understand.

Hope you can help, 
Cheers, 
JD

---

### Post by JKyleOKC on 2011-02-03
Linux does not use drive letters at all, so what you want to do can only be done in Windows.

You could possibly create a mount point named "/Z" and mount the partition there, but it would have the leading "/" and not have the trailing ":" that a Windows-oriented program expects, so that still would not do what you ask for.

Incidentally, Linux uses slightly different terms; the "drive" is the entire disk unit, and it's divided into "partitions" which contain files. Windows actually does the same thing but hides the term "partition" from you and uses the word "drive" instead. If you have one HDD and in Windows create two "drives" on it named C: and D:, you've actually got two partitions on that drive. When Linux sees it, it will call the drive "/dev/sda" if it's the first drive discovered during boot, and the C drive will be known as partition /dev/sda1 while D will become /dev/sda2.

---

### Post by justindublin on 2011-02-03
Ah ok, wine is just making it look like I've drives so.

Is there a way to map a windows shared folder to just a folder name in XUbuntu?

That's what most of the guides I seen seemed to be doing, but many were outdated.

Baring in mind also that's I'm new to Xubuntu

Thanks so far!

---

### Post by lykwydchykyn on 2011-02-03
Of course.  The terminology you're after is "mounting a samba share".  Samba is the Linux/Unix implementation of Microsoft's networking protocols.

There are GUI tools in Gnome for this, though I'm on KDE so I don't know off hand how it's done that way.

But there are any number of ways to mount a samba share.  At the command line, it's like this:

```

smbmount //server/sharename /path/to/mountpoint

```

Where "mountpoint" is where you want to attach the share.

You can also specify samba shares in your /etc/fstab file so they mount automatically at boot.

Someone more GNOME-y can probably recommend some GUI way to do this if that's your preference.

EDIT: saw you're on XFCE not GNOME; well, same difference, as far as my advice is concerned.

---

### Post by 1clue on 2011-02-03
If your server is sharing using cifs then use the newer protocol.

Is it absolutely necessary to have the drive letter?

I've discovered a neat trick for some legacy software that expects the drive letter but then uses a standard API from there:
[LIST=1]
[*]Mount using the mount command mentioned before.
[*]Change to your working directory from where the software will be run.
[*]ln -s /path/to/your/mount X:\\Attachments
[/LIST]

This makes a local directory named X:\Attachments, which was the name my legacy software expected.  Oddly enough it was smart enough to handle directory manipulation once it got that far, but there was no way it would handle a UN*X root path.

Good luck and have fun.

---

