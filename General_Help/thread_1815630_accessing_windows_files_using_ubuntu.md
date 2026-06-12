---
title: "accessing windows files using ubuntu"
date: 2011-07-31
forum: General Help
---

### Post by kenknott on 2011-07-31
My son's Windows Vista crashed and he wanted to access his files. We installed Ubuntu from a disc. The plan was to use ubuntu to get access to his files and then copy them onto a pen drive.
 
This installation went OK, but when we look in Computer Places we cannot see his old files.
 
When installing we opted to replace Vista with Ubuntu (rather than have it along side). Does this mean that we have wiped his old files or is there some way to access them?
 
Thanks to anyone who can help.

---

### Post by Untold on 2011-07-31
I do believe you lost everything.  When installing there is a warning under the "replace windows" that says it will wipe everything.  In the future, I would run Ubuntu live first and you would be able to find the files.  Then replace windows.

---

### Post by kenknott on 2011-07-31
As I feared!  Many thanks for confirming the bad news!!

---

### Post by bigken on 2011-07-31
you should have run ubuntu from cd and used an external device to write data too do a google search for a free data recovery software you might get the lost data back

---

### Post by gdonwallace on 2011-07-31
From what you are describing, then yes you erased the Vista install and replaced it with Ubuntu.  At this point, there is nothing that can be done to get those files back, unfortunately they have been deleted.

---

### Post by bigken on 2011-08-01
your lost is still recoverable like I said do a google search for a windows recovery software

---

### Post by coffeecat on 2011-08-01
@kenknott, the chances of recovering the lost data are small but it may be possible.

The first and most important thing is not to run Ubuntu from the hard drive. You have overwritten the Vista partition and any further use will simply increase overwriting of any data that may be there.

Next - have a look here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

You can install the application testdisk (which includes photorec) to a live Ubuntu session. With testdisk you can (theoretically) restore lost partitions. It may be possible to recover the lost Vista partition. However, all this does is to restore the lost partition table entries. The Vista NTFS filesystem will have been overwritten by the Ubuntu files to a greater or lesser degree. The chances of re-establishing a bootable Vista system are very low. It is worth trying, though. If you are able to restore the Vista partition, and even if it is unbootable, some of the files there may be readable (and copyable) from the live CD. It all depends on how much has been overwritten.

If testdisk fails, then you can try photorec, which can recover files of many types (not just photos) from lost or damaged partitions. Be aware that this is a tedious process. Photorec will serve you up with hundreds, even thousands, of files with obscure filenames - not the originals.

That link also describes some other data recovery software which you can run from an Ubuntu live CD.

---

### Post by kenknott on 2011-08-01
Many thanks for your help.
 
Silly question, maybe, but how do i find the wireless network?!  I've set up the SSID & WEP code using Edit Connections, but it doesn't seem to be looking for the connection.  
Left clicking on the icon gives Wired Network disconnected & VPN Connections.  No mention of wireless.
Right clicking:  Enable Networking is ticked.  If I go to Edit Connections it doesn't help.
 
I guess its something simple, but what?!
 
Until i can connect, I can't do the HowtoGeek process.

---

### Post by coffeecat on 2011-08-01
Since left-clicking on the network manager applet icon reveals no wireless networks it is likely that you have a driver issue which is going to be difficult to resolve in the live session. In which case you will be better off connecting with an ethernet cable.

---

### Post by kenknott on 2011-08-02
wow coffeecat, this really does work!  The HowtoGeek tutorial is brilliantly clear.  Thank you.
 
So far, using photorec, I have recovered a large number of images, many of which will need to be discarded.  
 
I've also recovered documents, but these are unreadable (i.e. symbols displayed instead of the expected text) when viewed using microsoft office.  Any idea how i might be able to make them readable?
 
Finally, the recovered files cannot be deleted!  Any idea how to unlock them, preferably in bulk?
 
Many thanks for your help.

---

### Post by coffeecat on 2011-08-02
> **kenknott said:**
> 
Finally, the recovered files cannot be deleted!  Any idea how to unlock them, preferably in bulk?

This will be a permissions or ownership issue. Where did you save the recovered files to? What sort of filesystem? On a Linux partition or one formatted with a Microsoft filesystem - NTFS or FAT32? If on a Linux filesystem this will be easily dealt with. If on a Microsoft filesystem, I'm slightly mystified at the moment as to how this could happen. 

If you are comfortable with using a Linux terminal, cd into a folder with some of the recovered files and post the output of:

```
ls -l
```

That will show ownership and permissions. If you're not clear what that means, post back and we'll see what we can do.

Also - you now have many photos with unhelpful filenames. You may or may not be aware that if the EXIF data is intact you'll be able to rename the files from EXIF fields to make them more meaningful. You can do this in either Windows or Ubuntu. Post back if you need more information.

> **kenknott said:**
> I've also recovered documents, but these are unreadable (i.e. symbols displayed instead of the expected text) when viewed using microsoft office. Any idea how i might be able to make them readable?

I'm wondering if these are not really word documents but have been given the filename extension .doc erroneously by photorec. We need to read the file header to see what they really are. At the moment I've forgotten how to do that, but I know where to find the information. I'll post back in a few hours when I've found it.

---

### Post by coffeecat on 2011-08-02
> **coffeecat said:**
> I'm wondering if these are not really word documents but have been given the filename extension .doc erroneously by photorec. We need to read the file header to see what they really are. At the moment I've forgotten how to do that, but I know where to find the information. I'll post back in a few hours when I've found it.

Tut - my memory! :| The Linux terminal command to read the file header to see what file type it is, is - wait for it - "file".

If you need help with that, or any of the other points, do post back and we'll take it from there.

---

### Post by kenknott on 2011-08-02
Well I'm getting out of my depth, but I'm not done yet!
 
What I'm doing at the moment is gradually transferring the many many files onto DVDs.
 
The jpg files can be seen ok using our other Vista laptop.  I reckon that if I put the files in size order, I'll only need to look at the larger ones.
 
The doc files aren't readable as yet, but at least i'll have those on dvd so that i can try to sort them later.
 
Thanks for your help.

---

### Post by kenknott on 2011-08-02
Nearly given up!  I have (literally!) millions of images now which is totally unmanageable!  I can't delete the smaller ones because i don't have permisssions to do so.  They are saved in ubuntu files.
 
The documents are more important so I might try a bit harder with these!  They are currently on a couple of dvd's but won't open with microsoft office.  Any suggestions gratefully received.
 
Thanks.

---

### Post by coffeecat on 2011-08-02
> **kenknott said:**
> Any suggestions gratefully received.
 

Please re-read my previous two posts. Without answers to some of those questions, it is difficult to help. By "Ubuntu files" do you mean on an Ubuntu partition? Are you using an Ubuntu live CD or a permanent Ubuntu installation? Where are the files saved to? An external drive or internal? How was it formatted?

By "other Vista laptop", do you mean you can't delete them in Windows??! What operating system are you using?

If the files are on a Linux fileystem it's possible that they are owned by root. If so, if you open a root nautilus with:

```
gksu nautilus
```

... navigate to where the files are stored and use shift-delete (for immediate deletion) that may deal with it. But I would prefer to see exactly what's happening first.

With regard to the alleged .doc files, as I said before the terminal "file" command will tell us whether they really are Word files or not, but again I need some information before I can tell you how to use that command.

---

### Post by kenknott on 2011-08-03
[QUOTE=coffeecat;11112488]Please re-read my previous two posts. Without answers to some of those questions, it is difficult to help. By "Ubuntu files" do you mean on an Ubuntu partition? Are you using an Ubuntu live CD or a permanent Ubuntu installation? Where are the files saved to? An external drive or internal? How was it formatted?
 
By "other Vista laptop", do you mean you can't delete them in Windows??! What operating system are you using?
 
If the files are on a Linux fileystem it's possible that they are owned by root. If so, if you open a root nautilus with:
 
```
gksu nautilus
```
 
... navigate to where the files are stored and use shift-delete (for immediate deletion) that may deal with it. But I would prefer to see exactly what's happening first.
 
 
 
[COLOR=blue]Out of my depth, but here goes:[/COLOR]
 
[COLOR=blue]The jpg files are saved in Ubuntu partition on the hard drive. For each file the properties show Owner: root Group: root. The menus are greyed out.[/COLOR]
 
[COLOR=blue]I don't know how to open a root nautilus.[/COLOR]
 
[COLOR=blue]Shift-delete did nothing.[/COLOR]
 
[COLOR=blue]Am I beyond help?[/COLOR]

---

### Post by coffeecat on 2011-08-03
> **kenknott said:**
> 
[COLOR=blue]Out of my depth, but here goes:[/COLOR]
 
[COLOR=blue]The jpg files are saved in Ubuntu partition on the hard drive. For each file the properties show Owner: root Group: root. The menus are greyed out.[/COLOR]
 
[COLOR=blue]I don't know how to open a root nautilus.[/COLOR]
 
[COLOR=blue]Shift-delete did nothing.[/COLOR]
 
[COLOR=blue]Am I beyond help?[/COLOR]

Not at all. You've given the information that was needed. The files are owned by root (the superuser) - that is why they are not deletable by an ordinary user, whatever key combination you use. You need either to delete from the terminal or with a root nautilus, but either way you need to open a terminal first.

In Ubuntu - open a terminal, and type this code:

```
gksu nautilus /
```

You will be prompted for your password. After which a Nautilus (file browser - equivalent to Windows Explorer) will open. This browser has full root privileges which means it is capable of doing things not possible with a nautilus file browser that you open normally. Take care. As I don't know where the files have been saved to, I've given you the code to open the root nautilus in the base of the filesystem. You'll have to navigate to where the files are. If you need help with that, post back. If they're in your home folder, open the folder called home, and then the one inside that named with your account name.

Now delete any files you need to delete with shift+delete - that is, press delete with the shift key held down. If you use the delete key only, they are simply sent to root's trash and are not physically removed from the drive. Since you have many thousands to delete, I guess you will need to use shift+delete. This is the same key combination that is used in Windows - it deletes files permanently and bypasses the recycle bin.

You don't ask about the alleged Word files. If they are still in your Ubuntu partition, you can examine them with the terminal command "file" to see what they really are. We can come back to that if you want.

By the way, there's something I am unhappy about. You installed Ubuntu, overwriting Vista, after which you needed to rescue lost files in the space hitherto occupied by Vista. I posted:

[quote="coffeecat"]The first and most important thing is not to run Ubuntu from the hard drive.

<snip>

You can install the application testdisk (which includes photorec) to a live Ubuntu session.[/quote]

The idea was that you would run photorec from the Ubuntu live CD and save the rescued files to an external hard drive - hence my repeated asking for what you saved the files to. However, it sounds as though you have saved the rescued files to the same partition as you were rescuing them from. I hope I have misunderstood you. The howtogeek link I posted says:

> Note: Do not recover files to the hard drive you’re recovering from.

If you still have files to rescue from the hard drive, and you are still using Ubuntu on that hard drive, stop now.

---

### Post by kenknott on 2011-08-03
How do i open a terminal?!

---

### Post by kenknott on 2011-08-03
it's ok, i've opened a terminal all by myself!

---

### Post by coffeecat on 2011-08-03
> **kenknott said:**
> How do i open a terminal?!

> **kenknott said:**
> it's ok, i've opened a terminal all by myself!

For the record, the reason I didn't describe how to open a terminal is because you don't say which version of Ubuntu you are running and hence I don't know whether you are running the classic gnome desktop or the Unity desktop. The instructions are different for each. And also, because you must have opened a terminal to have run photorec.

But you've found it - which is good! :)

---

### Post by kenknott on 2011-08-03
Many thanks.  I have now managed to get the shift-delete to work!  However there are so many images my son will have to decide how much time he wants to spend trawling through them!
 
The saving onto the hard drive was not deliberate!  I got confused in the photorec process and thought I was saving them to ubuntu live!!!
 
I have the "doc" files on dvd and will examine these in the way you describe later.
 
Thank you very much indeed for all your help.  I have enjoyed the mental exercise!

---

