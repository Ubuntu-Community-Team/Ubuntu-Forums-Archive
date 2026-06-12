---
title: "Oh god someone help, wheres my info!"
date: 2010-06-02
forum: General Help
---

### Post by ToastyMallows on 2010-06-02
Backstory:  I recently purchased a new computer. I had two hard drive in my old one, one for storage of all of my files, and one for the operating system.  As it so happens this didn't stay this way for long and soon enough i had some important files on both hard drives.

Fast forward to today; I was trying to recover the files from my operating system hard drive.  So I took it out of the computer and plugged it into my computer using a USB plug that I bought a while back.  But then I remembered, it was encrypted!  Well that's fine I have my paraphrase and my extrememly long key written on a post-it note.

Using the terminal, which I don't do that much, and a tutorial, I successfully mounted my hard drive and decrypted it.  All is well.  Now I tried to move all of my info OFF of the drive to an external hard drive mounted by my 10.04 LiveCD, lets call it MovingHDD.

I ran this command, WHILE IN CHROOT, to move my files off of the harddrive i was saving to MovingHDD

```
sudo cp -r cp /home/ross /media/MovingHDD
```

After it finished "moving", it blew up with all these errors because it couldn't find the directory it was moving to.

I ls after it is done, nothing.  Where did all of my files go!  I checked /home/ross, 0 files, /media/MovingHDD, 0 files.  BUT, my hard drive still has the same amount of freespace left as before.  So where did my files go?

Or are they gone forever?

Pleaes help!

---

### Post by bodhi.zazen on 2010-06-02
Moved to general help.

May I ask, what errors exactly did you get ?

---

### Post by ToastyMallows on 2010-06-02
I don't remember something about a "stat"?

Does that make any sense?

---

### Post by dtfinch on 2010-06-02
Is /home or /home/ross on a different partition? It'd show up as an empty folder if you only mounted the partition containing /.

---

### Post by ToastyMallows on 2010-06-02
No the whole drive is one partition.

---

### Post by ToastyMallows on 2010-06-02
does it just go somewhere in the operating system when there is an error? some other folder on the drive and I just have to find it?

---

### Post by cryptotheslow on 2010-06-02
Are you sure this is the exact command you used? As per your first post...

```
sudo cp -r cp /home/ross /media/MovingHDD
```

---

### Post by ToastyMallows on 2010-06-02
Ahhh!

Ok I restarted my live session and tried to get back on using this tutorial

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

and all my information is still there!

Now how do I move my home folder off to my MovingHDD CORRECTLY this time?

---

### Post by cryptotheslow on 2010-06-02
Well.. if you are in a liveCD environment and can see both your old home folder and the drive you want to move them too.... just use Nautilus - the normal file manager app to drag them across (hold down CTRL while you do to make sure you are only trying to copy rather than move them).

You might run into permissions issues though... if you do, delete what has already been copied and hit Alt+F2 and type in gksu nautilus to get nautilus running with sudo permission and try again.

---

### Post by ToastyMallows on 2010-06-02
I can't see my old home folder when i go into it theres two files a README that tells me to click on Access-Your-Private-Data.desktop.

The README says the click on that but it won't let me open it it says

"if you don't know where this came from, running it could be unsafe"

and then theres only a cancel button.

---

### Post by BoneKracker on 2010-06-02
'cp' doesn't "move" files; it copies them

So, regardless of what you did, your original files should still be where they started.

'mv' on the other hand, will indeed "move" files

Good thing you used 'cp'.

---

### Post by happyhamster on 2010-06-02
> **ToastyMallows said:**
> an external hard drive mounted by my 10.04 LiveCD, lets call it MovingHDD.
I'm new to chroot, so don't take my word for it, but wouldn't that be the problem? MovingHDD is mounted onto the live-session's filesystem, instead of the chrooted environment? In other words, you would have to manually mount MovingHDD from within the chroot instead. 

- Or, with MovingHDD mounted by the livecd, run: 

sudo mount -o bind /media/MovingHDD /mnt/media/MovingHDD

- before running the chroot command.

- Again, I'm new to chroot, so you'll want to be careful. Your data is still fine, and if you're in no serious haste to get to it, then there's no reason to take risks. Perhaps someone else can confirm or shoot the above down?

- Also, before trying to copy anything, make sure all folders are visible. And try copying just 1 file first to test.

- Anyway, if the chroot doesn't work out, as another approach you could try booting from the drive you're wanting to get your data from. (You'll have to select it as the first boot device, the exact way of doing that depends on your machine's BIOS. For example, on my machine I have to press the F12 key during the very first stages of the boot process. It's possible that grub won't cooperate though.)

---

### Post by ToastyMallows on 2010-06-02
> **happyhamster said:**
> I'm new to chroot, so don't take my word for it, but wouldn't that be the problem? MovingHDD is mounted onto the live-session's filesystem, instead of the chrooted environment? In other words, you would have to manually mount MovingHDD from within the chroot instead. 

- Or, with MovingHDD mounted by the livecd, run: 

sudo mount -o bind /media/MovingHDD /mnt/media/MovingHDD

- before running the chroot command.

- Again, I'm new to chroot, so you'll want to be careful. Your data is still fine, and if you're in no serious haste to get to it, then there's no reason to take risks. Perhaps someone else can confirm or shoot the above down?

- Also, before trying to copy anything, make sure all folders are visible. And try copying just 1 file first to test.

- Anyway, if the chroot doesn't work out, as another approach you could try booting from the drive you're wanting to get your data from. (You'll have to select it as the first boot device, the exact way of doing that depends on your machine's BIOS. For example, on my machine I have to press the F12 key during the very first stages of the boot process. It's possible that grub won't cooperate though.)

This sounds like something I need to do becuase chroot obviously can't see MovingHDD because as you stated its on the live CD.  I might give this a try.

I can see my /home/ross on my live cd now but everything isn't there its replaced by Access-Your-Secure-Data.desktop and READMe, which tells me to open the first file.  Which does nothing.  What do I do from here?

---

### Post by BoneKracker on 2010-06-02
Once both devices are mounted properly _somewhere_, the contents of the old home directory can be copied over (copied, not moved, for safety).  That should probably be done with:
```
sudo cp -a /<whatever> /<wherever>
```

That will recursively copy the entire directory and preserve all permissions.  Later, when the files are in the final destination, if the owner isn't right that can be easily fixed with:

```
chown -R myusername: /home/myusername
```

Sounds like LiveCD is making things harder instead of easier and it might have been easier just to boot from a simple rescue CD, mount the two devices, and copy the stuff over.  There is absolutely no need for a chroot old system just to copy files off it.

---

### Post by ToastyMallows on 2010-06-02
Thanks everyone that helped me.  I figured that I would just make a folder on the hard drive and move all of the information on there THEN after everything is moved and given premissions to, I would move it to my MovingHDD in the LiveCD.

Thanks again!

---

### Post by JoelOl75 on 2010-06-03
It would be better and safer to just move the items (Docs and pics and whatever) off your drive and onto the new one istead of trying to replace the whole home directory with the old one.  Permission problems and strange old config files usually cause more headache than just reconfigging a fresh install.

---

