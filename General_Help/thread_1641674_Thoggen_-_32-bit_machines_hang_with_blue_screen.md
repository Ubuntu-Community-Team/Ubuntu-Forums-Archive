---
title: "Thoggen - 32-bit machines hang with blue screen"
date: 2010-12-09
forum: General Help
---

### Post by unckybob on 2010-12-09
Did a new install on all my machines.

I added the Medibuntu repository like it says here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

# sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

and libdvdcss2:

# sudo apt-get install libdvdcss2

Then I installed Thoggen:

# sudo apt-get install thoggen

Thoggen works fine on my 64-bit machines. But when I run Thoggen on my 32-bit machines, it hangs with a blue screen window like this:

[http://71.229.209.241/Screenshot-thoggen.png](http://71.229.209.241/Screenshot-thoggen.png)

Anyone have any ideas?

---

### Post by Rough Hawkbit on 2010-12-22
Hi,

I have the same problem on my Eee PC 901 running Ubuntu 10.10 NBR. If I run Thoggen from terminal, this is the last line:


(thoggen:544): GStreamer-CRITICAL **: gst_value_set_fraction_range: assertion `((gdouble) start->data[0].v_int) / ((gdouble) start->data[1].v_int) < ((gdouble) end->data[0].v_int) / ((gdouble) end->data[1].v_int)' failed


It then just hangs indefinitely.

Any ideas?

Thanks, Rob

---

