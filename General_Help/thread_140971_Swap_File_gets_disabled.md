---
title: "Swap File gets disabled"
date: 2006-03-07
forum: General Help
---

### Post by fermulator on 2006-03-07
Hey all;

My swap file keeps getting disabled everytime ubuntu starts up!

ANy ideas?

Where could it be configured to do this?

At first startup;

top reveals:
**Swap: 0k total, 0k used, 0k free, ###k cached**

Everytime the system boots I have to enter the following commands:
```

mkswap /dev/hda2
swapon /dev/hda2
```

After doing that, top reveals:
**Swap: ###k total, ##k used, ###k free, ##k cached**

Any ideas how I can stop the system from disabling the swap on startup?

Of course I could keep entering these commands everytime it starts up, or create a script to do so...but it'd be nice to actually find the culprit who disables the swap.

Thanks!

---

### Post by Ocxic on 2006-03-07
check your /etc/fstab for a swap entry. if not add this line. you may cut & past if you wish, as your line should look just like this.

```

/dev/hda2       none            swap    sw              0       0

```

---

### Post by fermulator on 2006-03-07
WOW!

Haha, thanks

After looking in the fstab..it was empty!

But there was a backup, so I copied it over to the existing fstab.

That should do the trick!

Thanks a lot.

---

### Post by Ocxic on 2006-03-07
Your fstab was empty?!?!?!?!? it should never be empty!!!!!

---

