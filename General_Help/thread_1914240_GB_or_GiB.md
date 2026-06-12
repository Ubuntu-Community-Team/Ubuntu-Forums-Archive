---
title: "GB or GiB"
date: 2012-01-23
forum: General Help
---

### Post by ld114 on 2012-01-23
Now here's a thing. I am using Ubuntu 11.10 installed on a single partition on a 250 GB HDD. If I look at Disk Usage Analyser it tells me the total filesystem capacity is 244 GB, but if I look at System Monitor it tells me the total is 227.3 GiB. I am wondering why there are two measurement methodologies, and is Ubuntu in the process of moving from one to the other, or just not being clear about which one to use?

---

### Post by uRock on 2012-01-23
Both stand for gigabyte.

---

### Post by ld114 on 2012-01-24
Well that's just it - I don't think they do both stand for gigabyte. It seems that GiB is Gibibyte (binary-based) and GB is Gigabyte (decimal-based). My question is why does System Monitor use one method, and Disk Analyser another. Should there be a standard approach in Ubuntu. Thanks.

---

### Post by dcstar on 2012-01-24
> **ld114 said:**
> Well that's just it - **I don't think they do both stand for gigabyte**. It seems that GiB is Gibibyte (binary-based) and GB is Gigabyte (decimal-based). My question is why does System Monitor use one method, and Disk Analyser another. Should there be a standard approach in Ubuntu. Thanks.

They don't - the previous post is rubbish.

Linux uses a mixture of traditional and newer metrics, people are not going to change the behaviour of things that may have been around 20+ years (like many command line tools) just because something new comes out - it would severely break things.

Various apps are maintained by a multitude of different people, you are welcome to put in a bug report using the relevant procedure if you think something needs changing and those maintainers will consider it.

---

### Post by hartz on 2012-01-24
> **ld114 said:**
> Now here's a thing. I am using Ubuntu 11.10 installed on a single partition on a 250 GB HDD. If I look at Disk Usage Analyser it tells me the total filesystem capacity is 244 GB, but if I look at System Monitor it tells me the total is 227.3 GiB. I am wondering why there are two measurement methodologies, and is Ubuntu in the process of moving from one to the other, or just not being clear about which one to use?

244 GB = 227 GiB

You can try it yourself: 227.3 x 1024 x 1024 x 1024 = 244 GB

Engineers, including those who build bridges, space craft, hard drives and network adapters uses 1000 units in a Kilo, 1,000,000 in a Mega, etc.  Note that hard drives and network interfaces are serial read/write devices at the lowest level.

Those who build computer components that read and write in parrallel try to optimize the number of possible combinations of one and zero that they can send over an interface. Transmission paths on system cards are expensive, so it is all about return on investment.  So when 16 "wires" provides an extra 24 possible permutations of 1 and 0 (relative to 1000), they will include those.  In any case it aligns nicely with the math of base-2 number conversions, some of which even made it into numerous low-level (machine code) instructions.

Parrallel devices includes RAM and some system busses.

Operating systems and programs generally try and present these as true as possible.  

But sometimes things aren't so simple:  A program gets allocated memory in KiB, MiB, etc.  When the program stores that data to disk, the drive allocates KiB, MiB sized blocks.  But the raw media is a serial stream of 1s and 0s, built and marketed by metric-minded people.

Unfortunately people expect GB (hard drive) to be the same as GB (eg ram) ...

To alleviate some of the confusion, GiB is used to indicate 1024 MiB.  But the confusion isn't "1024" sized Gigs, we are optimistic little piggies.  We want all of our Gigs to be 1024... (unless specified as something like "metric Gigs".

Marketing plays a role too:  If one hard drive manufacturer started selling their 250 GB drives as 227 GiB drives, and the competition sells 250 GB drives ... guess who will get the sales?  People don't care that they are the same, they only read the big fat number.

I can start selling 4000 MB drives today to compete with the 3 TB drives.  I still have a few of those lying around somewhere.  Nobody reads the unit specifier in any case.

---

### Post by Habitual on 2012-01-24
hartz:

+1

---

### Post by ld114 on 2012-01-24
Thanks Hartz for a clear exposition of the two methodologies. The point about marketing and numbers is well made too. I think I now have clear understanding. So it looks like System Monitor is done by computer people, and Disk Usage Analyser by disk drive engineers!

And thanks dcstar for suggesting raising a bug report. For Ubuntu to promote a consistent approach that also suits a wide set of users, I think this should be to request that the Preferences for each App should allow the user to select whether to measure in GB or GiB. This should then promote both a better understanding of what each option is (and the fact that they are not the same), and allow users to choose the option they prefer.

---

### Post by ld114 on 2012-01-24
Actually on second thoughts, I think this is one for the Ubuntu Brainstorm.

---

### Post by dcstar on 2012-01-25
> **ld114 said:**
> Actually on second thoughts, I think this is one for the Ubuntu Brainstorm.

Maybe, maybe not. You have to remember that Ubuntu uses packages from "Upstream" sources and there is little point "reinventing the wheel" for things that may well be of benefit to all others that use the same packages.

If you put in a bug report to the maintainers of the particular package then any subsequent changes will be available to more than just Ubuntu users. As an example this change to the System Monitor came about because some users followed the process and now it will be available to all future Gnome users:

[https://bugzilla.gnome.org/show_bug.cgi?id=619979](https://bugzilla.gnome.org/show_bug.cgi?id=619979)

---

### Post by ld114 on 2012-01-25
Thanks for the last post. You have a very good point, so I will revert to submitting a bug report and see what happens. Regards.

---

