---
title: "Bad DVD Media? Bad Burner? Corrupt OS?"
date: 2011-03-10
forum: General Help
---

### Post by held7over on 2011-03-10
10.10 Gnome, TDK DVD+R blank media, both K3b and Nautilus Brasero

The first blank DVD I put into my burner was never seen by Ubuntu, so no icon appeared on the desktop nor did Nautilus File Manager see it. So, I assumed it was bad media and gave it a proper UFO flight, but thought it strange the system didn't at least acknowledge I had had something in the DVD burner.

I then inserted another blank DVD, Ubuntu promptly showed an icon for it and proceeded to burn successfully 2 DVD's using K3b and when they finished, I re-inserted them so I could check the contents were accessible and they were.

From that point on, the real trouble began, however Ubuntu saw the Blank DVD's I was putting in, and so did K3b (and also Nautilus Brasero). In the case of K3b it would report success in burning the DVD, but when I re-inserted the DVD the operating system would ignore it, just like it did the very first Blank DVD I had put into the drive. I tossed the DVD's until I had tossed 5 of them, then I lifted the stack of DVD's and took one from near the bottom and tried it. It burned as the others did, but I could not see it after I re-inserted it.

Also, if I put the DVD's that I had burned earlier that I could see upon re-inserting them back into the burner drive, the OS saw them right away and gave me the icon and Nautilus.

With Brasero, it also started burning, but then terminated with an error log.  Here is the applicable section of that log and I have put an <--- where the error begins:

BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr1 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr1 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2295104 ,  r=3245 ,  w=3245
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 1Bh , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD+R pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=3677634560, cap=4700372992

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
            <------------------------
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 73 03] Power calibration area error   
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibisofs stopping
BraseroLibisofs Getting out thread
BraseroLibisofs disconnecting BraseroLibisofs from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroLibburn
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2862)


That SCSI error thing makes me worry something is going wrong with DVD burner or internal communications or something like that. Can anyone tell me what the problem is here and what I should do? 

All in all, I wasted about 10 DVDs and I find it hard to believe TDK's are that bad! As I have been using them for years with the occasional Frisbee. 

Thanks :)

---

### Post by held7over on 2011-03-14
I discovered that K3b has no problems burning a CD and the system has not problems seeing the re-inserted cd and bring up nautilus to view the contents. The problem seems to be centered on either burning DVD's or the system detecting them after they have been re-inserted in the burner or any cd/dvd-rom for viewing.

Could this be some kind of power supply thing?

---

### Post by sidzen on 2011-03-14
purge brasero, use k3b only.  
After all, what do the error messages point to?

---

### Post by Bucky Ball on 2011-03-14
> **sidzen said:**
> purge brasero, use k3b only.  
After all, what do the error messages point to?

The DVD problem exists in both so this is no solution. The errors apply to Brasero because that was what was being used at the time. If it was K3B the errors would point to that.

Questions:

How old is the power supply? Is it a silver box or a reputable, reliable brand-name PSU.
How old is the optical drive (your burner)?
Are you having any problems with any other external devices?

---

### Post by sidzen on 2011-03-14
Just try it, then tell me if it doen't help.  I've had this problem before, with brasero.  
If it doen't help, then I'll yield to you,  in the meantime, let me quote --
"There is a principle which is a bar against all information, which is proof against all arguments and which cannot fail to keep a man in everlasting igonorance -- that principle is contempt prior to investigation."  -- Herbert Spencer

Investigate first, please!

---

### Post by held7over on 2011-03-14
Hi Bucky Ball!

A friend just came over with his laptop and we tried reading the DVDs that I can't get my system to see. His computer wouldn't read them either. So, the finger seems to point at my burner, except a friend emailed me today saying that it takes more power to burn a DVD than it does a CD, which is why I asked the question of whether it could be the power supply. The machine is old.

However, there has been no problem with all of its devices, except for the described problem. I was running it as a dual 250 gig system until I loaned out one of the drives a few weeks back. It now has 1 250 gig hard drive, 2 cd/dvd-roms, 1 floppy, 1 linux modem, 1 wireless card, and the memory is fully fleshed out. Externally it has a Epson Perfection 1660 Photo Scanner and a HP Photosmart B8550 Printer. I haven't seen anything glitchy about any of the system and peripherals and am using it to write these notes right now.

The computer is a Dell XPS T700r, 32 bit, 700 Mhz machine that must have been produced in late 1999 or 2000. I am the second owner picking up from a friend in 2006, so I don't know if the power supply has been replaced, but I can crack it open tomorrow.

The burner is a NEC DVD_RW ND-2500A that I purchased new in 2004. I would guess it has probably burned 500 DVD's at most over the years.

I guess I could try purchasing a Coolmax PS-228 LCD Power Supply Tester from ebay....or....maybe I could yank the Burner and shove it into another computer to see if that solves it's problems. I suppose it is also possible that some internal cabling connections in the machine aren't making good contact....lowering the available power also.  What do you think?

---

### Post by held7over on 2011-03-14
I removed the DVD Burner and put it into different Desktop Tower made in 2005. It burns DVDs and then the system sees them upon re-insertion. Also, I took the original DVD that the other system would not see, and tried them in the new system and they remained unseen by the system.

So, I guess that means the power supply in the older system is too weak under load.

I am thinking of converting the old system into a linux firewall for the server I am trying to set up. I will see if I can find a cheap power supply to drop into it.

I guess this means Problem solve-ed!  Thanks everyone for your input!

---

