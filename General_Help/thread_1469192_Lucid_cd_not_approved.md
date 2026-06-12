---
title: "Lucid cd not approved"
date: 2010-05-02
forum: General Help
---

### Post by shinjan on 2010-05-02
I had ordered for a Ubuntu 10.04 CD on 27th. It's still not approved...can any of you say why....
I have received 3cds from ubuntu previously by ordering. It takes about 1-2 days to get the approval....why is it so late this time?

---

### Post by nomnex on 2010-05-02
it was a bug in the grub at the release date, that prevented the detection of another OS (dual-booting), they had to re-spin the .iso & dvd.
be patient.

---

### Post by shinjan on 2010-05-02
One of my friends has downloaded lucid and installed in his machine...he says lucid hangs every 2 minutes in his machine...does it have anything to do with this bug?i think no, but still I'm asking.

---

### Post by nomnex on 2010-05-02
unlikely

---

### Post by shinjan on 2010-05-02
Then what is the problem in his case? Ubuntu is developing more and more serious problems as new versions are being released. Instead of fixing the bugs and improving on the previous version, new problems are cropping up. This will discourage newcomers to ubuntu from using it....
Out of the box functionalities and features are very much welcome but the developers can't afford to compromise on the fundamental amenities.

here is another serious problem:-
[http://ubuntuforums.org/showthread.php?p=9197470#post9197470](http://ubuntuforums.org/showthread.php?p=9197470#post9197470)

---

### Post by nomnex on 2010-05-02
nobody listens but feel free to change distro. no string attached.

bugs are always present on a new OS (Win, Mac, Linux) and on the bright side canonical is committed to fix them. That's why you are suffering a little delay.

They are hardware compatibility bugs (e.g. intel chipset 855) but that's upstream, canonical has little to do about it.

I have donated 10 USD for the free CD as mens of support this year, have you? Either you can support the project, either you can ask for a refund.

---

### Post by shinjan on 2010-05-02
>  but that's upstream, canonical has little to do about it.

what do you mean by 'upstream'? i didn't get you...

---

### Post by nomnex on 2010-05-02
[https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

you should do a bit of reading on the forum or browse the net. Ubuntu uses the Linux kernel and adapts it to its need. The kernel is the same for all the distros (RHL, Suze, Debian, etc.).

When you experienced a bug related to a hardware component, that's not Ubuntu specific. It is over Ubuntu--or upstream--at the kernel level.

it also applies to distribution software. When the software you are using has a bug, it is also over Ubuntu--or upstream--at the software developer level.

When you report a bug on Launchapd, the bug will be triaged and ported upstream to the attention of the developers (not to Ubuntu). Dev. are doing the job of fixing bugs (when they decide to do so), they are usually independent of Ubuntu.

Ubuntu fix bugs related to its distributions only, e.g. package software compatibility, or installation bugs. I am not sure if I explain well, but to summarize: Ubuntu uses a kernel and software packages it adapts to its distribution.

---

### Post by shinjan on 2010-05-03
I understand what you are trying to say. I appreciate your knowledge in this matter.
 HAL has been removed from lucid. Can it be a reason for so many hardware problems in lucid?

---

### Post by nomnex on 2010-05-03
shinjan, I don't know what you refer to by "so many hardware problems"?
Yes, DeviceKit [1][2] has replaced HAL
[1] [http://freedesktop.org/wiki/Software/DeviceKit](http://freedesktop.org/wiki/Software/DeviceKit)
[2] [http://lists.freedesktop.org/archives/hal/2008-May/011560.html](http://lists.freedesktop.org/archives/hal/2008-May/011560.html)

Lucide will probably need a couple of months to iron out some of its bugs. It is not different from the previous releases.

---

