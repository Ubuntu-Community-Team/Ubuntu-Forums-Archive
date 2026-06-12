---
title: "nvidia issue in ubuntu 12.04.1 LTS"
date: 2012-09-29
forum: General Help
---

### Post by pm15 on 2012-09-29
hi ubuntuers im new to ubuntu not linux but i face only 1 problem in 12.04.1 LTS wich is nvidia 525m geforce im my dell xps15z laptop !  is ther any way to solve the nvidia card issue ?  before ubuntu i was using bumblebee but its sucks realy and i wait your advanced thanks

---

### Post by BicyclerBoy on 2012-09-29
nVidia made it pretty clear, on release, that optimus was windows tech only.

You have to keep using bumblebee or just the iGPU.

There is hope on the horizon tho'
About 1 month ago nVidia announced it was working on optimus linux support.
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

I would hazard a guess that in 1 year optimus will work without bumblebee.
You probably need a later kernel than std ubuntu distro.

---

### Post by pm15 on 2012-09-29
> **BicyclerBoy said:**
> nVidia made it pretty clear, on release, that optimus was windows tech only.

You have to keep using bumblebee or just the iGPU.

There is hope on the horizon tho'
About 1 month ago nVidia announced it was working on optimus linux support.
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

I would hazard a guess that in 1 year optimus will work without bumblebee.
You probably need a later kernel than std ubuntu distro.

  thanks for your answer but how i can install bumblebee in the new ubuntu ? and is ther any wrong if i skip the nvidia drive ?

---

### Post by BicyclerBoy on 2012-09-29
I have not had the need for bumblebee.
I think the best way is ppa package archive..
[https://launchpad.net/~bumblebee/+archive/stable?field.series_filter=precise](https://launchpad.net/~bumblebee/+archive/stable?field.series_filter=precise)

You must **not** install the nVidia driver whne using Bumblebee. Bumblebee must do that.

If your iCPU/GPU is fast enough then don't use Bumblebee/nVidia.
You might be able to switch nVidia off in BIOS.

The linux support for the iGPUs HD2000/3000/4000/haswell/valley-view is improving every week but it takes time for this to get down to 12.04 LTS.

---

### Post by pm15 on 2012-09-30
> **BicyclerBoy said:**
> I have not had the need for bumblebee.
I think the best way is ppa package archive..
[https://launchpad.net/~bumblebee/+archive/stable?field.series_filter=precise](https://launchpad.net/~bumblebee/+archive/stable?field.series_filter=precise)

You must **not** install the nVidia driver whne using Bumblebee. Bumblebee must do that.

If your iCPU/GPU is fast enough then don't use Bumblebee/nVidia.
You might be able to switch nVidia off in BIOS.

The linux support for the iGPUs HD2000/3000/4000/haswell/valley-view is improving every week but it takes time for this to get down to 12.04 LTS.

  do you have a nvidia 525m geforce ?  and how you solve the problem ?  im lost now

---

### Post by BicyclerBoy on 2012-10-01
I'm sorry to have confused you..

You have to use bumblebee with optimus graphics (with almost all optimus h/w).

You have to let bumblebee install/load the graphics driver.. 

If you do **not** use bumblebee:
- wait 1-2 years for new nVidia optimus driver to get into ubuntu.
- just do nothing. use the intel iCPU/GPU

---

