---
title: "kernel compilation in ram (memory)"
date: 2012-01-31
forum: General Help
---

### Post by masuch on 2012-01-31
Hi,

I have a problem to compile kernel in RAM faster than on harddisk. I have still got the same compilation time consumption similar to on hard disk.

commands:
swapoff -a
mkdir -p /tmp/ramdisk
sudo mount -t tmpfs -o size=4G tmpfs /tmp/ramdisk
tar xvf linux-3.2.2.tar.xz -C /tmp/ramdisk/
cd /tmp/ramdisk/
make clean
make mrproper
make defconfig
export CONCURRENCY_LEVEL=`grep -c '^processor' /proc/cpuinfo`
time make


---time on ramdisk and harddisk:
real	6m4.874s
user	5m6.919s
sys	0m36.714s

real	6m7.436s
user	5m6.135s
sys	0m37.198s

---time on ramdisk and harddisk with -j20 parameter:
1m18s

Could please anybody help me what am I doing wrong ? Why is not ramdisk much faster than harddisk ?

Thank you for any clue.
Martin

---

### Post by Bobhuber on 2012-01-31
The primary reason to compile in ram is to save write cycles on an  SSD. Your still compiling the program in memory either way. It doesn't make much sense anyway if you have to keep the source and move it after your done. BTW I OC also and would have to see some charts to believe those specs.

---

### Post by masuch on 2012-02-01
Hi,

Thanks for answer. I understand that compiling is done in both cases in memory. But I/O operations within compilation process should have make bigger differences than I measured. There is usually only couple of secconds difference which is caused by whatever OS is doing. I have been expecteting more than 30 secconds difference because there are thousands I/O operations that should have had influence on final compilation time. I/O operations on hard disk or ram should be different. That's what I thought should happened ?
(I do not have SSD hd)



OC: I do not know how to make charts in linux for OC or what do you mean exactly by that ? I am linux newbee. I just made couple of test by 
turbostat - I do not know if I can trust to this old software but results coresponded with BIOS settings - which I am changing quite often.:
  # one of the results from ./turbostat:
      # core CPU   %c0   GHz  TSC   %c1    %c3    %c6    %c7   %pc2   %pc3   %pc6   %pc7 
      #           22.72 5.09 3.40  29.17   0.18  47.94   0.00   0.00   0.00   0.00   0.00
      #    0   0  57.01 5.10 3.40  22.78   0.16  20.05   0.00   0.00   0.00   0.00   0.00
      #    0   4  34.26 5.10 3.40  45.53   0.16  20.05   0.00   0.00   0.00   0.00   0.00
      #    1   1  24.84 5.09 3.40  19.72   0.37  55.07   0.00   0.00   0.00   0.00   0.00
      #    1   5   5.95 5.05 3.40  38.61   0.37  55.07   0.00   0.00   0.00   0.00   0.00
      #    2   2  30.24 5.10 3.40  17.71   0.16  51.89   0.00   0.00   0.00   0.00   0.00
      #    2   6  13.80 5.10 3.40  34.15   0.16  51.89   0.00   0.00   0.00   0.00   0.00
      #    3   3  15.57 5.08 3.40  19.67   0.02  64.74   0.00   0.00   0.00   0.00   0.00
      #    3   7   0.10 5.10 3.40  35.14   0.02  64.74   0.00   0.00   0.00   0.00   0.00



(OR stress test:
stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s --verbose )

---------------
But honistly I do not see linux to be using this speed usually like it is normal in windows (The difference between 3.4 and 5.1 GHz in games is visible).
I played crysis 2 in wine but I do not know how to force linux to use more than 3.4GHz (in my case) CPU ?

----------------
If you know how to say to linux use 5.1GHz frequency all the time when I
start some software please share the information :-)

I did noticed that do this is not enough:
sudo cpufreq-set -g performance

---

### Post by sxyaqwedc on 2013-01-04
When you run multiple threads then I/O waits are not that important because other threads that do have some data to process can fully utilize the CPU...

---

