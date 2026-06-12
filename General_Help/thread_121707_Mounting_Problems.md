---
title: "Mounting Problems"
date: 2006-01-25
forum: General Help
---

### Post by dk_pa on 2006-01-25
Okay, I know I asked this question already but I can't seem to find an answer anywhere so I am going to ask for some help again.

I have a ITE8212 ATA/RAID Controller on my motherboard.  I have two drives attached to it in just ATA/IDE mode.  The drives mount fine from a booted desktop but do not mount at boot.  The error that I see is "Device does not exsist."  I guessed that it's because that ITE8212 card is not loaded before the drives are trying to be mounted.  That is just my guess tho.  

Bottomline:  What can I do to fix this.  Currently every time I boot I just do "mount -a" and everything is fine.  I dont know if that could cause any kind of problems for me tho.  Is there a way to have the card loaded first (if that is the problem) or would an easy answer be to write a script to mount the drives for me (in which case can I have some help please?).  

Thanks

---

### Post by dcstar on 2006-01-25
[QUOTE=dk_pa]
.......
Bottomline:  What can I do to fix this.  Currently every time I boot I just do "mount -a" and everything is fine.  I dont know if that could cause any kind of problems for me tho.  Is there a way to have the card loaded first (if that is the problem) or would an easy answer be to write a script to mount the drives for me (in which case can I have some help please?).  

Thanks[/QUOTE]
System-Preferences-Session-Startup Programs

Put in whatever mount commands you use.

---

### Post by dk_pa on 2006-01-25
Doesn't seem to be working.

mount /dev/hde1 /media/secondary -t ext3 

Is what I put in.  Works from a terminal as sudo tho.

---

### Post by dcstar on 2006-01-25
[QUOTE=dk_pa]Doesn't seem to be working.

mount /dev/hde1 /media/secondary -t ext3 

Is what I put in.  Works from a terminal as sudo tho.[/QUOTE]
Your /etc/fstab entry may not allow users to mount this.

---

### Post by dk_pa on 2006-01-25
> Your /etc/fstab entry may not allow users to mount this.

Not quite sure I understand.  I commented out what I had in the fstab file and then put the mount /dev...etc commands (like what you see in above post) into the sessions --> startup.

I think you are saying that I would have to be sudo to do the mounting?  How would I get around that then?  Just give ownership?

---

### Post by dcstar on 2006-01-25
[QUOTE=dk_pa]Not quite sure I understand.  I commented out what I had in the fstab file and then put the mount /dev...etc commands (like what you see in above post) into the sessions --> startup.

I think you are saying that I would have to be sudo to do the mounting?  How would I get around that then?  Just give ownership?[/QUOTE]
You need to read the "man mount" pages to see what the options are to mount as a non-root user.

You should be able to leave the original fstab entry there, and just do "mount /media/secondary" to kick it off again.

---

### Post by dk_pa on 2006-01-25
Got it!  Thanks a lot!! I do always forget to read the man pages, shame on me!  Haha.  Man, super happy now.  Thanks again and for the patience =)

---

