---
title: "removed a raid drive, can no longer find /home"
date: 2012-02-02
forum: General Help
---

### Post by Repus on 2012-02-02
The Problem
[LIST]
[*]on boot system can no longer find /home
[*]putting the drive back isnt an option
[*]the other half of the raid 1 still has all the data of /home
[/LIST]

Background
[LIST]
[*]I moved 3 hdds to a new system.
[*]2 of them are raid-1 and mount /home
[*]1 of them is the rest of the file-system
[*]I moved the drives, everything worked (I should have stopped there and went to bed but no...)
[*]verified data on each of the raid drives
[*]shut down system
[*]removed one of the raid drives
[/LIST]

restated problem
[LIST]
[*]on boot system, can no longer find /home
[*]putting the drive back isnt an option
[*]the other half of the raid 1 still has all the data of /home
[/LIST]
My weak defense... I was tired. It was late. Im fairly certain Ive done this before and I didnt have any problems so I can only assume I skipped a step.

Any help is appreciated

Thanks

---

### Post by Repus on 2012-02-03
No luck? Unfortunate. 

Does anyone know how to take a drive that was previously half of a 2 drive raid-1 setup and make it function singly? From that point I should be able to remount it as /home.

Thanks

---

### Post by Repus on 2012-02-03
Fixed my problem. Yay Google and about 10 hours of my life.

If anyone is interested, 
[LIST]
[*]I had to degrade the raid array. This should have happened automatically but didn't for some reason
[*]Verify/check the array
[*]Mount the degraded array
[*]Backup remaining disk
[*]Maintain data and destroy array pointers
[*]Reboot while burning incense and wearing a silly hat
[/LIST]

Everything worked!

---

