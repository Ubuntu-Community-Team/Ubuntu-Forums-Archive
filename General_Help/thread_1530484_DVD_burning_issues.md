---
title: "DVD burning issues"
date: 2010-07-13
forum: General Help
---

### Post by johnston_evo3 on 2010-07-13
Okay since upgrading to 10.04 burning iso's to DVD has been patchy.

At first it corresponded to a new pack of discs which were duly replaced and it worked for a few burns then it stopped again.

I have tried Brasero, K3B and gnomebaker plus yet another pack of discs going from -R to +R.

Most of the time they will only work on one DVD player, not even the computer reads them.  But there have also been a number of full on coasters made too.


I then went back and did a clean install back to 9.04 which is what the computer seemed to work best on previously.  I also tried burning a Kubuntu. ubuntu 10.04 and Sabayon discs but only the 9.04 worked.

I've tried an older versions of WODIM and K3B with no luck

I have also purged all burning software and reinstalled with no luck.

I then tried using right click and selecting write to disc, this got me 4 burns although the last one looked like it wasn't burnt correctly, the markings on the disc looking faded and fuzzy if that makes sense but yet it was readable on the PS3.

Since then I have had no luck even after a re-boot. 

I find it really strange it worked in 9.04 and 9.10 but only went funny with the 10.04 upgrade up until then I don't think I ever had a bad burn, but going back to the older versions hasn't worked.


Heres last bits of two of the brasero session logs .



BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 12
	message	= "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record burn.c:2599)

--------------------------------------------------------

BraseroWodim stderr: wodim: fifo had 15218 puts and 14964 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 1937 times full, min fill was 65%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

Many thanks in advance for some input on this issue!!

---

### Post by wkulecz on 2010-07-22
I get this on CDs too :(

"An error occurred while writing to disc"

10.04, AMD64, all updates current as of this morning.

Suggestions?  This is terrible, CD/DVD burning has been rock solid on this very same hardware since 6.06, now its useless!

---

