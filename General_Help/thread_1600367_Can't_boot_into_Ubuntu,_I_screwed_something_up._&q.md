---
title: "Can't boot into Ubuntu, I screwed something up. &quot;An error occurred while mounting /&quot;"
date: 2010-10-18
forum: General Help
---

### Post by Leopardson on 2010-10-18
So, I was trying to mount my windows partition in Ubuntu so I could read it.

I said "Sudo Mount /dev/sdb1". 
Then it said "Error: Blah blah blah Windows wasn't shut down properly."
So I went into Windows, and shut it down properly.
Then when I tried to boot into linux, it stops with a low-res ubuntu splash screen and a message that says:

An error occurred while mounting /
Press S to skip mounting or M for manual recovery

So, I press M.
I say "mount /".
It does nothing.

I restart in recovery mode.
It stops at:
"mount: / not mounted already, or bad option"
"mountall: could not mount /"

Or something.

What did I do and how can I fix it?
Please help. I need Ubuntu working so I can transfer a file to my windows so I can start it up so I can access the internet through my cellphone so I can e-mail my boss a file so I don't get fired tomorrow morning.

Computers hate me.

Edit:
Changed Recovery to RW, edited Fstab, restarted, bam. It's alive.

---

### Post by Leopardson on 2010-10-18
Fantastic. "You have 20 minutes of battery remaining" on my laptop. The charger's got a short in it that I can't fix because I don't have solder.

The machines are out to get me.

---

### Post by dtfinch on 2010-10-18
Did you edit your /etc/fstab earlier? Having two entries for "/" could cause it to mess up, complaining that it can't mount / when it gets to the second entry. What if you just press 'S'?

---

### Post by dtfinch on 2010-10-18
If the laptop battery is dead by now, with no power supply, I imagine your next option might be to take the hard drive out, and if it's a sata, you might be able to just plug it into a desktop like any other hard drive. (edit: just noticed you said desktop in the other thread)

---

### Post by Leopardson on 2010-10-18
If I press S, It says

"The disk drive for /tmp is not ready yet or not present"

and freezes forever. Yay!

Yes, I probably screwed up fstab. Any ideas on restoring it?

> If the laptop battery is dead by now, with no power supply, I imagine  your next option might be to take the hard drive out, and if it's a  sata, you might be able to just plug it into a desktop like any other  hard drive.Paper tape and an earring. It's temporary, but it works.

Only other computer is my laptop and it doesn't have a sata port.

Edit: I might have a fstab.bak, hold on

Edit: I've got some good news and some bad news.

The good news is that I made a fstab.bak like a person with a brain before screwing things up.
The bad news is "mv: cannot move 'fstab' to 'fstab.old' : Read-only file system

---

### Post by dtfinch on 2010-10-18
In the manual recovery, / is already taken by the initramfs. I think you'd make another folder (like /blah) and mount your real / to that folder, then edit your fstab (maybe "nano /blah/etc/fstab") and reboot.

Edit: If it actually did manage to boot to your real /, but it's read-only, you might be able to "mount -n -o remount,rw /" to make it writable again.

---

### Post by Leopardson on 2010-10-18
I definitely screwed up fstab.

I looked at them with nano, and apparently I mounted sdb1 and made it think it's NTFS when it's not.
The old fstab is fine.

But I can't replace them, because the hard drive is read only.

So close, yet so far...

> In the manual recovery, / is already taken by the initramfs. I think  you'd make another folder (like /blah) and mount your real / to that  folder, then edit your fstab (maybe "nano /blah/etc/fstab") and reboot.
No idea how to do that.

---

### Post by dtfinch on 2010-10-18
If you got as far as being able to see your fstab, you could disregard what I said about manual recovery.

So "mount -n -o remount,rw /" to remount the root as read-write didn't work?

---

### Post by Leopardson on 2010-10-18
No, but editing grub and changing "ro" to "rw" got me started up.

So, now I'm in the computer. Fstab is completely empty and Fstab.bak is MIA. WTF?

---

### Post by dtfinch on 2010-10-18
No idea how that would happen. You could get empty files with ext4 by uncleanly powering off less than a minute after saving, if the editor didn't sync afterwards, but they would still exist.

A very basic fstab would be something like "/dev/sda1 / ext4 defaults 0 1"

---

### Post by Leopardson on 2010-10-24
Fixed. I had the right idea, but did things in the wrong order.
This is how I fixed it:
1. Loaded grub, changed Ubuntu (RECOVERY) to Read and Write (In Grub, both had RO, I changed one to RW.).
2. I was able to change fstab and make it how I wanted it.
3. I booted again and it worked fine.

This is what happen when you give someone who doesn't know what they're doing an OS intended for people that know what they're doing.

---

