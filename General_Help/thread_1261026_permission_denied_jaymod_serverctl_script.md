---
title: "permission denied jaymod serverctl script"
date: 2009-09-08
forum: General Help
---

### Post by shred_eng on 2009-09-08
hi, i have been trying to use the jaymod serverctl script on a enemy territory server (non-graphical) i'm sure i've put  the right paths into the serverctl script which starts with   #!/bin/sh

but no matter what permissions i set for my - enemy-territory, etmain, and jaymod folder,  - path:  /home/myname/enemy-territory,

the console is filled with /enemy-territory     permission denied
                                   /enemy-territory/etmain    permission denied 
                                   /enemy-territory/jaymod/
                                   /enemy-territory/jaymod/qagame.so   permission denied
and the same for other configs in these folders

any advice how to sort out the permission problem?  :confused:

thanks
 the server runs fine without using serverctl script, but i just wanted to get it working (as you do)

---

### Post by shred_eng on 2009-09-08
this is the thing that is baffling me, it is a commented out description from the serverctl script bundled with jaymod  : serverctl is THIS script make sure it has execute permissions.

how do i give it execute permissions, which i interperet as meaning it needs permission to enter the folders and have access to the files in them, but surely its just a script, and as all the folders and files are currently set at 0777 it should work...or no? the script itself is 0775    and everything,  enemyterritory folders and script is in     /home/shred_eng/

any ideas?...plz

shred_eng

---

### Post by shred_eng on 2009-09-11
bump!  

hi, had to bump this cos im getting desperate. just tell me any possible ways to give directories and files in my /home/shred_eng/  execute permissions, in case ive overlooked something. any help appreciated :biggrin:

thanx,

---

