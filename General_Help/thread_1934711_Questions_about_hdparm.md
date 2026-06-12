---
title: "Questions about hdparm"
date: 2012-03-02
forum: General Help
---

### Post by josephellengar on 2012-03-02
Hello.

I am doing a project for my OS class and am testing the impact of I/O scheduling on solid state drives. I am considering using hdparm for the benchmarking, but had a concern: does hdparm specifically test the performance of the drive or does it test the performance in the context of the given OS? That is, if I change the scheduler, will the results from hdparm change, or will it stay the same because I am using the same physical drive? I haven't yet gotten approval for the project and haven't purchased the hardware I will need, which is why I am asking this question rather than testing it myself. Anyway, am I looking at the correct utility for my needs?

Thanks!

---

### Post by Khayyam on 2012-03-03
Joseph ...

hdparm is not really suitable for benchmarking, when you run, say, 'hdparm -t' it is not actually performing any meaningful (filesystem level) timeing, just buffer reads. Such information is useful, but it doesn't translate well into 'real' reads/writes (which are operating not only via the buffer, but the filesystem). If your looking for something more meaningful (in a real world sense) then you might want to look at [bonnie++](http://www.coker.com.au/bonnie++/).

As for your question re "hdparm and OS", no, its directly interfacing the drive.

HTH ... khay

---

