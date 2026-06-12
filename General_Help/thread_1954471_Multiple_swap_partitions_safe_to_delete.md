---
title: "Multiple swap partitions safe to delete?"
date: 2012-04-08
forum: General Help
---

### Post by try1211 on 2012-04-08
Hello. I've already read Ubuntu's SwapFAQ [here]("https://help.ubuntu.com/community/SwapFaq") but it doesn't say anything about deleting swap partitions, so just to be clear, and to avoid any possible headaches, I have to ask: Is it safe to delete all but one of these swap partitions and extend my main ext4 partition?

Screenshot illustrating the issue:
[IMG]http://i1237.photobucket.com/albums/ff470/tryaiden/UbuntuOneiric/gparted-swappartitions.png[/IMG]

The NTFS partition is just a shared media partition NOT a windows system partition. 
I don't know how I ended up with so many swap.

---

### Post by Elfy on 2012-04-08
Yep.

Delete sda5/6/7/8

None are in use.

> I don't know how I ended up with so many swap.IF you keep do the autopartition bit of the install procedure it would create swaps - though it would also create / as well.

Not sure why you have so many - but I'd hazard a guess that it's something like that.

You will end up with ~30Gb unused at the end of the drive.

If you wish to add that to / then you'll have to do that from a live environment.

To be honest you might be better - deleting all the swap - resizing / and then make a new swap in the livecd/usb
Then while still there edit fstab and edit the swap line.

---

### Post by try1211 on 2012-04-08
Thanks for a prompt reply!

> IF you keep do the autopartition bit of the install procedure it would create swaps

I guess that makes sense because I had 11.10 installed on this partition, then I decided I'd try out 12.04beta and I did a clean install over 11.10 by choosing to "Replace 11.10 with precise."

After that I decided it was just too buggy for me to use yet so I installed 11.10 again over it...

But thanks for answering my question!

---

