---
title: "Uber-noob needs guidance on USB partitions!"
date: 2009-09-26
forum: General Help
---

### Post by Heavy Armor on 2009-09-26
Okay, first of all, I am NOT a programmer by any stretch of the imagination, therefor working in a Terminal is pretty awkward and confusing for me.

I have been attempting to set up an Ubuntu LiveUSB stick. I got halfway through one tutorial, finally got completely lost, and gave up on it. Now my USB stick mounts as two separate drives, and I can't get it back to normal. I've tried another tutorial that reformats the stick and removes partitions, but that method only works on one at a time, and doesn't merge these two pieces back together.

When I list them, my USB stick shows up as SDB1 and SDB2. I'm trying to get it back to just one big SDB1. I know it's a lot to ask, but could anyone guide me through it?

Thanks a bunch,
~HA

---

### Post by dcstar on 2009-09-26
> **Heavy Armor said:**
> Okay, first of all, I am NOT a programmer by any stretch of the imagination, therefor working in a Terminal is pretty awkward and confusing for me.

I have been attempting to set up an Ubuntu LiveUSB stick. I got halfway through one tutorial, finally got completely lost, and gave up on it. Now my USB stick mounts as two separate drives, and I can't get it back to normal. I've tried another tutorial that reformats the stick and removes partitions, but that method only works on one at a time, and doesn't merge these two pieces back together.

When I list them, my USB stick shows up as SDB1 and SDB2. I'm trying to get it back to just one big SDB1. I know it's a lot to ask, but could anyone guide me through it?

Thanks a bunch,
~HA

Install the **gparted** package and use the Partition Editor.

---

### Post by Heavy Armor on 2009-09-26
Wow, that was ENTIRELY too simple. Thanks! ):P

~HA

---

