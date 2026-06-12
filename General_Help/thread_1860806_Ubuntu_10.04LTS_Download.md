---
title: "Ubuntu 10.04LTS Download"
date: 2011-10-15
forum: General Help
---

### Post by XBMC old School on 2011-10-15
Is the download-able ubuntu image on the ubuntu.com page always compiled with the latest stable kernel? So if i download ubuntu 10.04 lts, will the kernel be 3.0.4?

---

### Post by asasoft on 2011-10-15
Lucid Kernel is 2.6.32, but you can compile or download newer kernels.

---

### Post by mister_playboy on 2011-10-15
> **asasoft said:**
> Lucid Kernel is 2.6.32, but you can compile or download newer kernels.

I don't recommend this.  The whole point of running the LTS is to have a stable system.  Mixing in stuff from the newer releases will cause problems.

If you want the newest stuff, run 11.10.

---

### Post by ajgreeny on 2011-10-15
Hwever, if you enable the "proposed" repos in the updates tab of Software Sources, you can install 2.6.35-30 kernel which is certainly very stable on my machine.

I did also try the 2.6.38 and the 2.6.37 kernels from the kernel ppa repos.  I thought they were OK at the start, but quickly ran into problems with USB transfer rates with those kernels so removed them.  USB is important to me as I backup to an external USB drive and speeds of only a few KB/sec, instead of up to 20MB/sec were just not acceptable.  No problem with the 2.6.35-30 kernel, however, so that is well worth using in my opinion.

---

### Post by XBMC old School on 2011-10-15
Ya i'm not to sure i like the new unity format and so on. But i did want the new 3.0 kernel w/ the BFS and BFQ patches. i have had issues trying to compile the newer kernels.

I am looking to reformat. I experimented a lot with this install and looking to clean it out.

So it's better to stick with the accompanying Kernel for that distro release?

---

### Post by AlphaLexman on 2011-10-15
I am on 10.04.3 LTS running kernel 2.6.32 and am very happy with the stability.
My Android phone also uses the same kernel version, proving it's reliability.

---

### Post by XBMC old School on 2011-10-15
my stability is fine. It is just that i'm a lean, speed junky. I thought the 3.0 kernel release had a speed upgrade. I already loaded on the BFS&BFQ patch to the 1000Mhz Low-latency Desktop.

---

### Post by varunendra on 2011-10-17
> **XBMC old School said:**
> my stability is fine. It is just that i'm a lean, speed junky. I thought the 3.0 kernel release had a speed upgrade. I already loaded on the BFS&BFQ patch to the 1000Mhz Low-latency Desktop.
IMHO, a kernel should be considered as *'definitely better than others'* only when it is included in the latest LTS. Else it is either outdated or experimental.


**PS:**
*XBMC old School (IP MAN?),*
Nice avatar by the way, do we need to stay alert and get our bones insured ASAP? ;)

---

### Post by dcstar on 2011-10-17
> **XBMC old School said:**
> Is the download-able ubuntu image on the ubuntu.com page always compiled with the latest stable kernel? So if i download ubuntu 10.04 lts, will the kernel be 3.0.4?

No. Ubuntu releases only have the package versions of the time of the original release. Security updates are only made available during the support period of the release, not newer versions.

The latest kernel for 10.04 systems is 2.6.32-35 (from the "Proposed" repository).

---

