---
title: "Need a good way to test drive performance (read/write - speed/access time)"
date: 2010-12-03
forum: General Help
---

### Post by TheOnlyMrK on 2010-12-03
I got a new flash drive that's supposedly the fastest available with 16GB quad-channel memory and I'd like to test it to make sure it lives up to it's "27MBps Read 25MBps Write". I know the Ubuntu Disk Utility can benchmark drives but for a full read/write test it requires the drive to not even have a MBR on it, which for flash based media that keeps the same speed across the entire drive that is not necessary. So I was wondering are their any programs or console commands that could test the read and write speed of this drive?

EDIT: Flash Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820220505](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220505)

---

### Post by uRock on 2010-12-04
Go in your menu to System> Administration> Disk Utility and you can use that to benchmark the drive.

You probably aren't going to get those USB speeds unless your system has USB 3.0 ports.

---

### Post by TheOnlyMrK on 2010-12-04
> **uRock said:**
> Go in your menu to System> Administration> Disk Utility and you can use that to benchmark the drive.

You probably aren't going to get those USB speeds unless your system has USB 3.0 ports.

Well I already tested the read using the Ubuntu Disk Utility and it averaged 34MBps, but I need something to test the write speed too and even though the Ubuntu Disk Utility says it supports write testing, in my opinion it does not if it doesn't provide an option to test an already partitioned drive, so I need a different tool to test the write speed.

---

### Post by TheOnlyMrK on 2010-12-04
Here's the screenshot;

---

### Post by TheOnlyMrK on 2010-12-04
Guess the best way to test speed is still the same old copy a file to/from the drive. Oh well.

---

