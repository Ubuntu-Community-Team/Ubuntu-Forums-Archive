---
title: "Annoying error-messages when booting Ubuntu"
date: 2010-08-06
forum: General Help
---

### Post by kenny-an on 2010-08-06
Hello

When booting Ubuntu after BIOS i get error-messages( differ a bit from time to time). The ones I've written down are :

  	 	 	 	 	 	  [	7.236977] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.242008] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.259357] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.474326] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x0
 [	7.474636] ata1.01: SError: { DevExch }


and also sometimes only



   	 	 	 	 	 	  [	12.124988] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x0
 [	12.124991] ata1.01: SError: { DevExch }


When in Ubuntu everything workes fine, should I have any concern what so ever about the health of my system? 



Thanks

---

### Post by linux18 on 2010-08-06
> **kenny-an said:**
> Hello

When booting Ubuntu after BIOS i get error-messages( differ a bit from time to time). The ones I've written down are :

  	 	 	 	 	 	  [	7.236977] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.242008] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.259357] sd 5:0:0:0: [sdc] Assuming drive cache: write through
 [	7.474326] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x0
 [	7.474636] ata1.01: SError: { DevExch }


and also sometimes only



   	 	 	 	 	 	  [	12.124988] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x0
 [	12.124991] ata1.01: SError: { DevExch }


When in Ubuntu everything workes fine, should I have any concern what so ever about the health of my system? 



Thanks
if your computer is booting fine then thats all very normal output. Debugging code is what linux is made of and it will be mad if it doesn't show you some debugging code at least once when you turn on the computer :)

---

