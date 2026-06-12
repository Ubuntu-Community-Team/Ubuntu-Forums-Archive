---
title: "Ubuntu ld not workng (cannot be found)"
date: 2011-11-07
forum: General Help
---

### Post by newport_j on 2011-11-07
I am having trouble going back to my old Ubutu 11.04 setup. I tried and did not comletely install binutils_gold.
 
Then when I stopped the install and tried to compile some programs that I previously had compiled it said it could not find ld or ld was not working.
 
 
I looked in
 
/usr/bin for ld (the error directed me there)
 
and found a softlink: ld->gold
 
Well I though this is simple I must break the link.
 
I typed: 
 
unlink gold
 
 
Now ld and gold are now shown in reverse video, but this step is creating more ld problems.
 
I believe that I have three options:
 
 
1. Repair ld function - can this be done?
 
 
2. Repair my install of Ubuntu 11.04 - how is ths done? 
 
 
3. Install Ubuntu 11.04 again - I know this can be done, and of course all important files must be backed up?
 
 
In fact for all three options relevant files must be backed up.
 
Just what should I do?
 
If there any other options are available please let me know.
 
Newport_j

---

