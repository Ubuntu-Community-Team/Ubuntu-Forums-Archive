---
title: "Dual, dual core machine (H8DCE mobo) ubuntu compatibility?"
date: 2012-03-28
forum: General Help
---

### Post by wayover13 on 2012-03-28
Hi. This might seem like kind of a clueless newbie question but hey, I make no claims to omniscience. I've recently run across a machine I'm considering buying that was probably made to be a server. It's got two dual-core CPU's in it (not sure which/what clock speeds). I think this was the latest-greatest about 4 or 5 years ago. The mobo is a Super Micro H8DCE. Has 3 GB of RAM, yada, yada.

Basically, I'm just wondering how/whether Ubuntu (actually, probably Mythbuntu) will run on such a machine? I at one time, prior to the advent of dual-core systems, was looking into installing MythTV on a dual-CPU machine. I decided against that when someone told me that, unless apps are complied with dual-CPU support, you gain nothing from the extra CPU. I'm still unsure whether that's correct: isn't it the kernel that decides what app/process runs on which CPU?

Furthermore, with the proliferation of dual- and multi-core systems over the last few years, wouldn't it be true that most things must now be configured out-of-the-box to run on more than one core? If so, it seems I could expect Ubuntu/Mythbutu to run just fine on the hardware I'm asking about in this thread. But, like I said, my knowledge about these things is pretty sketchy.

Can anyone enlighten me on the issues at stake here?

TIA,
James

---

### Post by Bucky Ball on 2012-03-28
Looks like you're good to go (since Dapper):

[http://computingtech.blogspot.com.au/2008/08/enabling-multiple-cpus-smp-in-ubuntu.html](http://computingtech.blogspot.com.au/2008/08/enabling-multiple-cpus-smp-in-ubuntu.html)

You might want to have more of a dig in here:

[http://us.yhs4.search.yahoo.com/search;_ylt=A0oGdOIvpXNPbC8A1glXNyoA?p=ubuntu%20two%20separate%20processors%20smp&fr2=sb-top&fr=altavista]("http://us.yhs4.search.yahoo.com/search;_ylt=A0oGdOIvpXNPbC8A1glXNyoA?p=ubuntu%20two%20separate%20processors%20smp&fr2=sb-top&fr=altavista")

SMP included in the newer kernel seems to be the key ...

---

### Post by wayover13 on 2012-03-28
Thanks for those links--interesting information there. So it seems apps themselves need not be compiled for multi-core/multi-CPU compatibility?

James

---

### Post by wayover13 on 2012-03-29
I'll bump this thread because I'm still curious about the issues involved. Again, my assumption in the past was that the kernel is what determines what process runs on which CPU in a multi-CPU or multi-core system, so apps do not require any special configuration to take advantage of the extra CPU/core. But a fellow who seemed a bit better informed  than I technically once told me that applications need to be compiled for multi-CPU/core support in order for them to run any better on a multi-CPU/core than on a single CPU/core system. 

Can anyone provide further commentary or information on that issue? So, were I to use such a machine as was asked about in the OP, would it not matter whether I had apps specially compiled for multi-core/CPU, since the kernel would be orchestrating how the CPU's/cores get used by the applications? Or, perhaps in this day of multi-core ubiquity, apps are just compiled by default with multi-CPU/core support? Clarification will be appreciated.

Thanks,
James

---

### Post by Bucky Ball on 2012-03-29
Well ... most processors now are dual, quad, and beyond core, just in one processor. Since the days of hyper-threading a single-core was pretending to be a dual-core. 

Just wondering how long ago your friend mentioned it ... ;)

But I know that doesn't clarify much. Maybe a quick search ...

[http://us.yhs4.search.yahoo.com/yhs/search?p=multi+core+support+applications&fr=altavista&fr2=sfp&iscqry=](http://us.yhs4.search.yahoo.com/yhs/search?p=multi+core+support+applications&fr=altavista&fr2=sfp&iscqry=)

... and:

[http://us.yhs4.search.yahoo.com/search;_ylt=A0oGdNa1aXRPAFQAwAJXNyoA?p=multi%20core%20support%20applications%20ubuntu&fr2=sb-top&fr=altavista](http://us.yhs4.search.yahoo.com/search;_ylt=A0oGdNa1aXRPAFQAwAJXNyoA?p=multi%20core%20support%20applications%20ubuntu&fr2=sb-top&fr=altavista)

---

### Post by wayover13 on 2012-03-29
Thanks for the further input. I also found something interesting in wikipedia's "Multi-core processor" article (section "Software impact"): > An outdated version of an anti-virus application may create a new thread for a scan process, while its GUI thread waits for commands from the user (e.g. cancel the scan). In such cases, a multicore architecture is of little benefit for the application itself due to the single thread doing all heavy lifting and the inability to balance the work evenly across multiple cores. Programming truly multithreaded code often requires complex co-ordination of threads and can easily introduce subtle and difficult-to-find bugs due to the interweaving of processing on data shared between threads (thread-safety). Consequently, such code is much more difficult to debug than single-threaded code when it breaks. There has been a perceived lack of motivation for writing consumer-level threaded applications because of the relative rarity of consumer-level demand for maximum use of computer hardware. Although threaded applications incur little additional performance penalty on single-processor machines, the extra overhead of development has been difficult to justify due to the preponderance of single-processor machines. Also, serial tasks like decoding the entropy encoding algorithms used in video codecs are impossible to parallelize because each result generated is used to help create the next result of the entropy decoding algorithm.

Given the increasing emphasis on multicore chip design, stemming from the grave thermal and power consumption problems posed by any further significant increase in processor clock speeds, the extent to which software can be multithreaded to take advantage of these new chips is likely to be the single greatest constraint on computer performance in the future. If developers are unable to design software to fully exploit the resources provided by multiple cores, then they will ultimately reach an insurmountable performance ceiling.
From that information I infer that most end-user software is still not written to take advantage of multiple CPU's/cores in the sense that multi-threading's not implemented (and in some case, apparently, can't be). Things run better/quicker I guess because each program can have some share of the CPU power of one or other of the available cores/CPU's. But the programs are apparently still running single-threaded. Oh, and I also infer that the kernel does orchestrate this distribution of tasks to the CPU's/cores.

Further input, anyone?

Thanks,
James

---

