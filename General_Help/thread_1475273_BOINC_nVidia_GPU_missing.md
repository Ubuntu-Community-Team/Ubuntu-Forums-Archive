---
title: "BOINC nVidia GPU missing"
date: 2010-05-06
forum: General Help
---

### Post by dslayer202 on 2010-05-06
Hello all.

I've been using BOINC Manager to run Einstein@Home for about a week now on Ubuntu 10.04
Before I started using it I installed the Cuda 3.0 toolkit driver downloaded off of nVidia's website. BOINC ran flawlessly until today. I don't know what changed, but now the status of my tasks is 
"GPU Missing, Ready to Run(1.00 CPUs + 1.00 NVIDIA GPUs)

My card is a Geforce 9800m GTS

---

### Post by johnrh on 2010-06-11
dslayer202, I seem to have exactly the same problem! Suprised no-one can answer it yet.

When this happens here's what I get under messages:

No usable GPUs found
Einstein@Home	Application uses missing NVIDIA GPU
Einstein@Home	Missing coprocessor for task p2030_54186_40048_0030_G46.35+02.38.C_6.dm_512_0
Einstein@Home	Missing coprocessor for task p2030_54186_43900_0063_G62.71+01.65.C_3.dm_8_1

Actually this doesn't happen with every boot, sometimes it detects ok, but when this happens the kind of Einstein tasks above won't run. Other kinds run fine.

Checking the 'Use GPU.....' box 'on/off' in Preferences doesn't seem to make any difference.

My graphics card is GeForce GT9400 GT (cuda enabled), using the latest Ubuntu drivers and BOINC, Ubuntu 10.04.

Annoying, these intermittent bugs!

PS: I see there's a new BOINC version 6.10.56, anyone tried that?

---

### Post by oldos2er on 2010-06-11
> **johnrh said:**
> PS: I see there's a new BOINC version 6.10.56, anyone tried that?

I'm using 6.10.56, CUDA's been working for me (I run World Community Grid and Seti@home). 

"NVIDIA GPU 0: GeForce 9500 GT (driver version unknown, CUDA version 3000...."

I'm using Nvidia drivers v195.36.24

---

### Post by johnrh on 2010-06-13
Thanks, oldos2er, interesting comment.

My guess is that 6.10.56 is the solution, but was rather put off installing their .sh file by reading some disadvantages listed on their website.

Hopefully the ubuntu developers will soon give us 6.10.56.

---

### Post by RoyStrachan on 2010-06-16
> **johnrh said:**
> Thanks, oldos2er, interesting comment.

My guess is that 6.10.56 is the solution, but was rather put off installing their .sh file by reading some disadvantages listed on their website.

Hopefully the ubuntu developers will soon give us 6.10.56.

Sometimes the GPU needs a second chance try -
sudo /etc/init.d/boinc-client restart   

and see if that gets things going.

---

### Post by miha72 on 2010-07-10
What happends if you try to restart the boinc with thw init.d script. 
I personaly have a problem with the slow init of the driver and boinc does not "see" the card as it starts.
Manual restart fixes it.

Miha

---

### Post by quantumbb on 2011-02-23
I'm currently having the same problem with DNETC@home. I'm using a GT 240 nvidia card. This problem started about 10 days ago when I upgraded some packages. It was working prior to the upgrade. This has happened before with upgraded packages or kernels, but later updates fixed the problem. On a different system, I'm using a 9800GTX card with no problems.

---

### Post by inebriant on 2012-04-11
> **RoyStrachan said:**
> Sometimes the GPU needs a second chance try -
sudo /etc/init.d/boinc-client restart   

and see if that gets things going.

This worked for me. Thanks.

---

### Post by oldos2er on 2012-04-11
Closed, necromancy.

---

