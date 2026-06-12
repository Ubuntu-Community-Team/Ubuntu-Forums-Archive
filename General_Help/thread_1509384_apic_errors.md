---
title: "apic errors"
date: 2010-06-14
forum: General Help
---

### Post by ub007 on 2010-06-14
Hi,

I keep getting these msgs on console:

APIC error on CPU0: 00(40)
APIC error on CPU0: 00(40)
APIC error on CPU0: 08(08 )
APIC error on CPU0: 08(08 )

how do i interpret these error bits?
in doc , i find
/* Here is what the APIC error bits mean:
	   0: Send CS error
	   1: Receive CS error
	   2: Send accept error
	   3: Receive accept error
	   4: Reserved
	   5: Send illegal vector
	   6: Received illegal vector
	   7: Illegal register address
	*/

but i got no clue what the code 00(40) means with respect to above error bits in apic.c

can anyone help plz?

---

