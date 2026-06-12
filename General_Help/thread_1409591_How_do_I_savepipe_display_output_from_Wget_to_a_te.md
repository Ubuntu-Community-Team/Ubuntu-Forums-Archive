---
title: "How do I save/pipe display output from Wget to a text file?"
date: 2010-02-17
forum: General Help
---

### Post by cilbuper on 2010-02-17
I am looking for a way to save the output/display of the wget command to a text file?  

I tried 
```
wget  http://www.website.com/filename > file.txt
```
and it didn't save the data.  

Is there a way to do this or is there another means of downloading a file and piping the output of the speed/transfer rate to a text file?

---

### Post by Barriehie on 2010-02-17
> **cilbuper said:**
> I am looking for a way to save the output/display of the wget command to a text file?  

I tried 
```
wget  http://www.website.com/filename > file.txt
```
and it didn't save the data.  

Is there a way to do this or is there another means of downloading a file and piping the output of the speed/transfer rate to a text file?

Try:
```
wget  http://www.website.com/filename 1>file.txt 2>/dev/null
```

This will pipe STDOUT, 1, to the file and STDERR, 2, into /dev/null.

HTH

---

### Post by jamesisin on 2010-02-17
Your syntax ought to work.  The syntax provided by Barriehie would also be correct.  (STDOUT or 1 is assumed when not specified.)  If you would like both STDOUT and STDERR in that file use &> filename (&>> will append rather than overwrite).

Are you certain there is any output?

---

### Post by jamesisin on 2010-02-17
I just tested your version.  There is no STDOUT.  All the screen output is STDERR.

There you go.

---

### Post by cilbuper on 2010-03-19
I'm still getting an empty file when I do the above. I have tried the following:

> wget  [http://www.website.com/filename](http://www.website.com/filename) 1>file.txt 2>/dev/null

Am I supposed to put the "1" in front of the ">file.txt" and the "2" in front of the ">/dev/null"  ?  I have tried it with and without the 1 & 2.  

I have tried any possible combination with no luck.  I have tried it on my Ubuntu 9.10 install as well as my web host server that I pay for.  

I just don't understand this. Also why do I send the STDERR to the blackhole (/dev/null)?

---

### Post by HappyHoward on 2010-03-19
According to the man page of wget you should use:

wget -O file.txt [http://www.website.com/filename](http://www.website.com/filename)
or
wget -O - [http://www.website.com/filename](http://www.website.com/filename) > file.txt

---

### Post by cilbuper on 2010-03-19
I think I have not made my goals or intentions clear.  I need to capture the data on the screen after Wget is completed, the IP address, transfer rates etc and place them into a log file.  

I know I once did this for a very large website as I downloaded the entire 30GB+ of HTML files and I was able to save what was being displayed on the screen into a text file.  

So, if that makes it a little clearer, how do I save what is being displayed on the screen into a text file?

---

### Post by HappyHoward on 2010-03-19
Ah ok I see. 

wget [http://website.com/file](http://website.com/file) 2> file.txt

This will redirect stderror to the file file.txt, which I think is what you want.

Edit: Looking at your previous posts it seems you have already tried this... In that case I don't know why it doesn't work.

---

### Post by cilbuper on 2010-03-19
> **HappyHoward said:**
> Ah ok I see. 

wget [http://website.com/file](http://website.com/file) 2> file.txt

This will redirect stderror to the file file.txt, which I think is what you want.

Edit: Looking at your previous posts it seems you have already tried this... In that case I don't know why it doesn't work.

I am very appreciative for the help you have given me on this issue. Thank you very much!

Well, this actually does give me a result which is really detailed and can be very useful and I never knew I could save these results.  What does the "2" mean?  I think the 2 is what made it work.  

Here are the results I get when I use the above command, but it is saved in the text file (it is edited to protect privacy):
> --2010-03-19 06:50:06--  [http://www.website.com/file](http://www.website.com/file)
Resolving [www.website.com](www.website.com)... 74.111.111.111
Connecting to [www.website.com|74.111.111.111|:80](www.website.com|74.111.111.111|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5115824 (4.9M) [text/plain]
Saving to: `file'

     0K .......... .......... .......... .......... ..........  1%  181K 27s
    50K .......... .......... .......... .......... ..........  2%  601K 18s
   100K .......... .......... .......... .......... ..........  3%  684K 14s
   150K .......... .......... .......... .......... ..........  4%  885K 12s
   200K .......... .......... .......... .......... ..........  5% 1.05M 10s
   250K .......... .......... .......... .......... ..........  6% 1.05M 9s
   300K .......... .......... .......... .......... ..........  7% 1.02M 8s
   350K .......... .......... .......... .......... ..........  8% 1.04M 8s
   400K .......... .......... .......... .......... ..........  9% 1.04M 7s
   450K .......... .......... .......... .......... .......... 10% 1.05M 7s
   500K .......... .......... .......... .......... .......... 11% 1.02M 7s
   550K .......... .......... .......... .......... .......... 12% 1.04M 6s
   600K .......... .......... .......... .......... .......... 13% 1.04M 6s
   650K .......... .......... .......... .......... .......... 14% 1.05M 6s
   700K .......... .......... .......... .......... .......... 15% 1.01M 6s
   750K .......... .......... .......... .......... .......... 16% 1.05M 6s
   800K .......... .......... .......... .......... .......... 17% 1.04M 5s
   850K .......... .......... .......... .......... .......... 18% 1.03M 5s
   900K .......... .......... .......... .......... .......... 19% 1.03M 5s
   950K .......... .......... .......... .......... .......... 20% 1.04M 5s
  1000K .......... .......... .......... .......... .......... 21% 1.04M 5s
  1050K .......... .......... .......... .......... .......... 22% 1.05M 5s
  1100K .......... .......... .......... .......... .......... 23% 1.02M 5s
  1150K .......... .......... .......... .......... .......... 24% 1.05M 5s
  1200K .......... .......... .......... .......... .......... 25% 1.04M 4s
  1250K .......... .......... .......... .......... .......... 26% 1.06M 4s
  1300K .......... .......... .......... .......... .......... 27% 39.7K 8s
  1350K .......... .......... .......... .......... .......... 28%  231K 8s
  1400K .......... .......... .......... .......... .......... 29%  594K 8s
  1450K .......... .......... .......... .......... .......... 30%  364K 8s
  1500K .......... .......... .......... .......... .......... 31%  678K 7s
  1550K .......... .......... .......... .......... .......... 32%  727K 7s
  1600K .......... .......... .......... .......... .......... 33%  193M 7s
  1650K .......... .......... .......... .......... .......... 34%  200M 7s
  1700K .......... .......... .......... .......... .......... 35%  193M 6s
  1750K .......... .......... .......... .......... .......... 36%  198M 6s
  1800K .......... .......... .......... .......... .......... 37%  242K 6s
  1850K .......... .......... .......... .......... .......... 38%  346K 6s
  1900K .......... .......... .......... .......... .......... 39%  595K 6s
  1950K .......... .......... .......... .......... .......... 40%  728K 6s
  2000K .......... .......... .......... .......... .......... 41% 1.02M 6s
  2050K .......... .......... .......... .......... .......... 42% 1.02M 5s
  2100K .......... .......... .......... .......... .......... 43% 1.04M 5s
  2150K .......... .......... .......... .......... .......... 44% 1.05M 5s
  2200K .......... .......... .......... .......... .......... 45% 1.04M 5s
  2250K .......... .......... .......... .......... .......... 46% 1.02M 5s
  2300K .......... .......... .......... .......... .......... 47% 1.04M 5s
  2350K .......... .......... .......... .......... .......... 48% 1.04M 5s
  2400K .......... .......... .......... .......... .......... 49% 1.02M 4s
  2450K .......... .......... .......... .......... .......... 50% 1.05M 4s
  2500K .......... .......... .......... .......... .......... 51% 1.04M 4s
  2550K .......... .......... .......... .......... .......... 52% 1.04M 4s
  2600K .......... .......... .......... .......... .......... 53% 1.02M 4s
  2650K .......... .......... .......... .......... .......... 54% 1.04M 4s
  2700K .......... .......... .......... .......... .......... 55% 1.05M 4s
  2750K .......... .......... .......... .......... .......... 56% 1.05M 4s
  2800K .......... .......... .......... .......... .......... 57% 1.02M 4s
  2850K .......... .......... .......... .......... .......... 58% 1.04M 3s
  2900K .......... .......... .......... .......... .......... 59% 1.05M 3s
  2950K .......... .......... .......... .......... .......... 60% 1.05M 3s
  3000K .......... .......... .......... .......... .......... 61% 1.01M 3s
  3050K .......... .......... .......... .......... .......... 62% 1.05M 3s
  3100K .......... .......... .......... .......... .......... 63% 1.05M 3s
  3150K .......... .......... .......... .......... .......... 64% 1.04M 3s
  3200K .......... .......... .......... .......... .......... 65% 1.02M 3s
  3250K .......... .......... .......... .......... .......... 66% 1.05M 3s
  3300K .......... .......... .......... .......... .......... 67% 1.05M 3s
  3350K .......... .......... .......... .......... .......... 68% 1.04M 2s
  3400K .......... .......... .......... .......... .......... 69% 1.02M 2s
  3450K .......... .......... .......... .......... .......... 70% 1.05M 2s
  3500K .......... .......... .......... .......... .......... 71% 1.04M 2s
  3550K .......... .......... .......... .......... .......... 72% 1.02M 2s
  3600K .......... .......... .......... .......... .......... 73% 1.05M 2s
  3650K .......... .......... .......... .......... .......... 74% 1.04M 2s
  3700K .......... .......... .......... .......... .......... 75% 1.05M 2s
  3750K .......... .......... .......... .......... .......... 76% 1.02M 2s
  3800K .......... .......... .......... .......... .......... 77% 1.05M 2s
  3850K .......... .......... .......... .......... .......... 78% 1.05M 2s
  3900K .......... .......... .......... .......... .......... 79% 1.05M 2s
  3950K .......... .......... .......... .......... .......... 80% 1.02M 1s
  4000K .......... .......... .......... .......... .......... 81% 1.04M 1s
  4050K .......... .......... .......... .......... .......... 82% 1.05M 1s
  4100K .......... .......... .......... .......... .......... 83% 1.05M 1s
  4150K .......... .......... .......... .......... .......... 84% 1024K 1s
  4200K .......... .......... .......... .......... .......... 85% 1.07M 1s
  4250K .......... .......... .......... .......... .......... 86% 1.03M 1s
  4300K .......... .......... .......... .......... .......... 87% 1.06M 1s
  4350K .......... .......... .......... .......... .......... 88% 1.02M 1s
  4400K .......... .......... .......... .......... .......... 89% 1.04M 1s
  4450K .......... .......... .......... .......... .......... 90% 1.06M 1s
  4500K .......... .......... .......... .......... .......... 91% 1.02M 1s
  4550K .......... .......... .......... .......... .......... 92% 1.04M 1s
  4600K .......... .......... .......... .......... .......... 93% 1.05M 0s
  4650K .......... .......... .......... .......... .......... 94% 1.05M 0s
  4700K .......... .......... .......... .......... .......... 95% 1.01M 0s
  4750K .......... .......... .......... .......... .......... 96% 1.06M 0s
  4800K .......... .......... .......... .......... .......... 97% 1.05M 0s
  4850K .......... .......... .......... .......... .......... 98% 1.04M 0s
  4900K .......... .......... .......... .......... .......... 99% 1.01M 0s
  4950K .......... .......... .......... .......... .....     100% 1.07M=6.7s

2010-03-19 06:50:12 (747 KB/s) - `file' saved [5115824/5115824]



I would also like to be able to get the shortened version of what is displayed in the following picture, basically the bottom two rows are the most important but I have been able to capture everything after the command begins.

[IMG]http://www.integritycomputingsolutions.com/images/wget_screenshot.jpg[/IMG]

---

### Post by HappyHoward on 2010-03-19
The 2> means redirect stderror
1> or just > means redirect stdout

How did you get wget to output in the short format? I get my output in the same form you did in your first example. If you know how to get wget to output in that short form you should be able to save just the last 4 rows (including blank rows) using:

wget [http://website.com/file](http://website.com/file) |& tail -n 4 > file.txt

---

### Post by cilbuper on 2010-03-19
> **HappyHoward said:**
> The 2> means redirect stderror
1> or just > means redirect stdout

How did you get wget to output in the short format? I get my output in the same form you did in your first example. If you know how to get wget to output in that short form you should be able to save just the last 4 rows (including blank rows) using:

wget [http://website.com/file](http://website.com/file) |& tail -n 4 > file.txt


THAT IS PERFECT!!!  I really appreciate your help doing this!  Thanks again!

---

