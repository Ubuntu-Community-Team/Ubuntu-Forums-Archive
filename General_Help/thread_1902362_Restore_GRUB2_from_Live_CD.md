---
title: "Restore GRUB2 from Live CD?"
date: 2011-12-30
forum: General Help
---

### Post by fallenshadow on 2011-12-30
Can someone advise me on how to do this?

I managed to do it before but maybe it was luck as I can't seem to reproduce it like last time! :(

---

### Post by joshj70 on 2011-12-30
This might be what your looking for [http://ubuntunigeria.wordpress.com/2010/09/02/how-to-restore-grub2-using-an-ubuntu-live-cd-or-thumb-drive/](http://ubuntunigeria.wordpress.com/2010/09/02/how-to-restore-grub2-using-an-ubuntu-live-cd-or-thumb-drive/)

---

### Post by ratcheer on 2011-12-30
I can tell you, but it would be better to find a good tutorial.

Use "sudo fdisk -l" and /or "df -h" to make sure you know the correct partition name of your / filesystem. Use it where it says sdXX, below.

sudo mount /dev/sdXX /mnt

sudo mount --bind /dev/ /mnt/dev

sudo chroot /mnt

sudo grub-install /dev/sdX           (<== NOT XX, this is just the disk address)

sudo grub-install --recheck /dev/sdX

Ctrl-D (to exit the chroot session)

sudo umount /mnt/dev

sudo umount /mnt

reboot

Tim

---

### Post by fallenshadow on 2011-12-30
Trying to do what you just posted but...

> chroot: failed to run command `/bin/bash`: Exec format error

---

### Post by fallenshadow on 2011-12-30
Ok I have since managed to restore the grub menu but now im back to my original problem.

The Grub2 menu freezes and will not boot into anything!

---

### Post by lswb on 2011-12-30
ratcheer, how can that work unless there is already an otherwise working OS installed on /dev/sdXX, including grub executables? Can't you just open a terminal from a live CD or rescue CD environment and "sudo grub-install /dev/sdX"  ?

---

### Post by elliotn on 2011-12-30
restoration of grub from Ubuntu alternate CD is the easiest way there is

---

### Post by fallenshadow on 2011-12-30
Is there a way to run update-grub from the Live CD to update the grub on the hard drive?

I think if I could do this my problem would be solved!

---

### Post by cbowman57 on 2011-12-30
> **elliotn said:**
> restoration of grub from Ubuntu alternate CD is the easiest way there is

Easier than that is to use Rescatux.

---

### Post by ratcheer on 2011-12-30
> **lswb said:**
> ratcheer, how can that work unless there is already an otherwise working OS installed on /dev/sdXX, including grub executables? Can't you just open a terminal from a live CD or rescue CD environment and "sudo grub-install /dev/sdX"  ?

I'm not sure how to answer your question, but I have done it several times in the past. Yes, I had Ubuntu installed on the disk and grub had become hosed. I believe I got those instructions from the official Ubuntu documentation server.

Tim

---

### Post by Bobhuber on 2011-12-30
I keep seeing the chroot business for grub install from a live cd which seems a bit confusing.
I've done it a thousand times with 2 simple commands.

sudo mount /dev/sda1 /mnt                                                      # replace sda1 with your root partition number (Ubuntu Partition)
sudo grub-install --root-directory=/mnt/ /dev/sda                     # replace sda with your boot drive

Example - sda=drive 1 - sda1=partition 1 on drive 1

---

### Post by fallenshadow on 2011-12-31
I currently have rescatux running but keyboard input is not detected. I think this is because I have a usb wireless keyboard.

I might borrow a wired keyboard to see can I get anywhere with this.

---

### Post by cbowman57 on 2011-12-31
> **fallenshadow said:**
> I currently have rescatux running but keyboard input is not detected. I think this is because I have a usb wireless keyboard.

I might borrow a wired keyboard to see can I get anywhere with this.

Nothing to lose, try unplugging the usb dongle & plug it back in to see if it gets detected. Assuming you didn't already try that.

---

### Post by fallenshadow on 2012-01-01
Borrowed wired keyboard, used Rescatux to restore grub properly.

Now happily using Ubuntu on my desktop once again!

Thanks for all the help folks!

;)

---

### Post by cbowman57 on 2012-01-01
> **fallenshadow said:**
> Borrowed wired keyboard, used Rescatux to restore grub properly.

Now happily using Ubuntu on my desktop once again!

Thanks for all the help folks!

;)

Good to hear, that Rescatux is handy to have around.

---

