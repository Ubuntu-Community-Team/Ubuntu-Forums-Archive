---
title: "My Ubuntu Computer Runs slower than Windows"
date: 2010-10-01
forum: General Help
---

### Post by iamthesgt on 2010-10-01
I have a 2-year old DELL XPS M1330. I used to have Windows Vista on it, but over time, I believe it became clogged with too many programs and so I wiped the hard drive and installed ubuntu 10.04 LTS about 2 weeks ago. However, ubuntu many times seems to run slower than vista did. I have 4 GB of RAM, an Intel Core 2 Duo T8100 (2.1 GHz, 3MB Cache, 800MHz FSB), 320GB HDD, 128MB nVIDIA GeForce 8400M. Ubuntu recognizes me as having dual processors at 2.1 GHz and 3.4GB RAM, but when I'm watching a simple video, whether online or locally on the computer, my CPU usage invariably jumps to 100% and it lags. Sometimes, even simple word processing makes it slow significantly. Please help.

---

### Post by davidmohammed on 2010-10-01
welcome to the forums,

  your problem sounds like that you may need the nvidia graphics driver to be activated.  From you System menu - navigate to Administration - Hardware drivers.

Activate the recommended nvidia driver.  Hope this helps.

---

### Post by Marzata on 2010-10-01
You might look at: [http://ubuntuforums.org/showthread.php?t=1585751](http://ubuntuforums.org/showthread.php?t=1585751)

---

### Post by TBABill on 2010-10-01
If you get or have the nVidia driver going and still seem sluggish, make sure you are running both Adobe Flash and Sun Java. You can check via Synaptic. Just search flash, then search java. If you have open source versions of either, remove them and install the adobe or sun versions. That'll speed things up a small amount as well.

---

### Post by iamthesgt on 2010-10-02
Thanks guys. I installed the nVIDIA driver and it seems to be working now. I thought I had already done that, but I guess not. Anyway, it works now.

---

