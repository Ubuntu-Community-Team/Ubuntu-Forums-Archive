---
title: "Ubuntu 10.04 wacky activity, fixed by booting to different 'version'"
date: 2010-09-07
forum: General Help
---

### Post by jrusidoff on 2010-09-07
Okay, Linux-ers...this had me wracking my brain for days now.  I finally have a work-around, but have lots of questions.  I will try to be as brief as possible!

Last week sometime, my 10.04 did one of its normal Ubuntu updates.  Sometime after that, I  noticed that I couldn't shut the computer down (it's an old HP laptop).  I could kill it from the terminal, but every time I tried to shut down using the button-app on the panel it would just act like I was changing users.  I went to the forums and got a bazillion ideas;  NONE of them worked.  Just do a search for yourself and you'll see how many 'solutions' are out there.

Oh well...I thought I guess I can live with this.  BUT..then I try to plug in my ipod, it says can't mount volume, not authorized.  Ditto for my USB memory stick.  Back to the forums and other help thingies on the web, find the resultant ba-jillions of solutions (edit permissions, install mount manager, blah blah)none of which worked.

One of the ideas was to boot into recovery mode and do all kinds of scary stuff, but none of these worked.  I did notice, however, that there were two distinct versions (are they called 'versions'?) of 10.04 to boot from.  (I installed 10.04 clean from a disk I made).  The first version I was using was:

Ubuntu with Linux, 2.6.32-24 and the recovery mode of this.

The next one, which I have to assume was a bit older was:

Ubuntu with Linux, 2.6.32-21.

I thought, what the hell, it's screwed anyway, and picked the second one.  Guess what?  ALL MY PROBLEMS WERE GONE!  I can shut down correctly, and I can plug into any USB oriface with whatever and it works correctly.  I see-sawed back and forth 4 or 5 times; -24 ...bad  -21...good!  Consistently.

So, my questions:

1.  How can I make sure that my computer boots to the ONE THAT WORKS (the second one) by default?

2.  If I can do this, what happens when the helpful, friendly update comes along and screws it up again?  Will that happen?

and 3:  WTF?  Why would this happen in the first place?  I am honestly telling you all the problems came up with only the automatic Ubuntu updates;  I did not install anything new or hack into any part of the kernel or chant any voodo incantations.

Any of you who are more expert than I am (which wouldn't be hard...) have any ideas?

Thanks,

JimmyR

---

### Post by JKyleOKC on 2010-09-07
To make sure that it boots to the one that works, do these steps:
```
gksudo gedit /etc/default/grub

# change the line GRUB_DEFAULT=0 to read GRUB_DEFAULT=2
# save the file

gksudo update-grub
```
That should fix it. The next automatic update that puts in a new kernel, however, will move the non-working one down to position 2 and you'll need to do this again to change the default to 4. Grub counts the entries from the top beginning with 0.

When gksudo asks for your password, it wants your login password. The second call to it won't ask again; it leaves you authorized for several minutes just to allow for situations like this one.

As for why it happens, sometimes a kernel update includes a change that affects different hardware differently; it's impossible to test the changes against all the different kinds of machines out there so the change goes undetected until someone reports it. The next update might, or might not, fix things; I'd try it out to see what happens and if the newer one works, change the default back to "0" because updates in Ubuntu almost always involve fixes to improve system security.

---

### Post by jrusidoff on 2010-09-07
Thanks Jim, so that number is a kernel update then?

Why would it screw things up so badly?  

Will I just have to keep on notifying it to choose #2, then 4, then 6, then...well, you get the idea!

JimmyR

---

### Post by JKyleOKC on 2010-09-07
Not necessarily; I edited to respond to your final question also. You can also simply remove the not-good kernel versions, using Synaptic, but then the automatic updating would probably try to put them back for you.

---

