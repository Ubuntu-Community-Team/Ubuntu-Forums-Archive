---
title: "Logging rsync files"
date: 2011-04-30
forum: General Help
---

### Post by kg87 on 2011-04-30
I wonder if someone has a solution for this

currently im rysncing a remote server, and writing out the results to a text file using 

```
rsync -rtuvO --progress /media/Backup/ /media/GPCF/TEMP/ > /home/george/Desktop/Logs/"$NOW\-$TIME.0day"
```

which results in

```
SomeFile.mp3

       32768   0%   21.43kB/s    0:14:14  
       65536   0%   41.40kB/s    0:07:21  
      294912   1%  100.00kB/s    0:03:00  
      557056   3%   98.68kB/s    0:03:00  
      819200   4%   95.42kB/s    0:03:03  
     1081344   5%  117.34kB/s    0:02:27  
     1343488   7%  117.15kB/s    0:02:25  
     1605632   8%  133.44kB/s    0:02:05  
     1867776  10%  158.81kB/s    0:01:43  
     2129920  11%  161.67kB/s    0:01:40  
     2392064  13%  158.76kB/s    0:01:40  
     2654208  14%  157.93kB/s    0:01:39  
     2916352  15%  157.83kB/s    0:01:37  
     3178496  17%  157.51kB/s    0:01:36  
     3440640  18%  161.82kB/s    0:01:32  
     3702784  20%  163.81kB/s    0:01:29  
     3964928  21%  167.57kB/s    0:01:25  
     4227072  23%  166.86kB/s    0:01:24  
     4489216  24%  168.37kB/s    0:01:22  
     4751360  25%  167.68kB/s    0:01:21  
     5013504  27%  167.73kB/s    0:01:19  
     5275648  28%  167.32kB/s    0:01:18  
     5537792  30%  165.96kB/s    0:01:17  
     5799936  31%  167.35kB/s    0:01:14  
     6062080  33%  166.83kB/s    0:01:13  
     6324224  34%  166.91kB/s    0:01:11  
     6586368  35%  166.75kB/s    0:01:10  
     6848512  37%  167.13kB/s    0:01:08  
     7110656  38%  171.44kB/s    0:01:05  
     7372800  40%  175.10kB/s    0:01:02  
     7634944  41%  178.90kB/s    0:00:59  
     7897088  43%  182.96kB/s    0:00:57  
     8159232  44%  180.92kB/s    0:00:56  
     8421376  45%  180.92kB/s    0:00:54  
     8683520  47%  182.56kB/s    0:00:52  
     8945664  48%  181.79kB/s    0:00:51  
     9207808  50%  181.98kB/s    0:00:50  
     9469952  51%  182.89kB/s    0:00:48  
     9732096  53%  182.69kB/s    0:00:47  
     9994240  54%  180.92kB/s    0:00:46  
    10256384  55%  182.50kB/s    0:00:44  
    10518528  57%  182.30kB/s    0:00:42  
    10780672  58%  173.32kB/s    0:00:43  
    11042816  60%  173.56kB/s    0:00:42  
    11304960  61%  169.71kB/s    0:00:41  
    11567104  63%  166.21kB/s    0:00:40  
    11829248  64%  171.09kB/s    0:00:38  
    12091392  65%  167.65kB/s    0:00:37  
    12353536  67%  166.99kB/s    0:00:35  
    12615680  68%  167.81kB/s    0:00:34  
    12877824  70%  167.02kB/s    0:00:32  
    13139968  71%  167.18kB/s    0:00:31  
    13402112  73%  168.45kB/s    0:00:29  
    13664256  74%  167.27kB/s    0:00:27  
    13926400  75%  166.61kB/s    0:00:26  
    14188544  77%  167.51kB/s    0:00:24  
    14450688  78%  165.72kB/s    0:00:23  
    14712832  80%  167.95kB/s    0:00:21  
    14974976  81%  167.90kB/s    0:00:20  
    15237120  83%  166.99kB/s    0:00:18  
    15499264  84%  168.48kB/s    0:00:16  
    15761408  85%  166.42kB/s    0:00:15  
    16023552  87%  167.90kB/s    0:00:13  
    16285696  88%  167.59kB/s    0:00:12  
    16547840  90%  167.18kB/s    0:00:10  
    16809984  91%  167.05kB/s    0:00:09  
    17072128  93%  167.73kB/s    0:00:07  
    17334272  94%  167.43kB/s    0:00:06  
    17596416  95%  167.76kB/s    0:00:04  
    17858560  97%  167.68kB/s    0:00:02  
    18120704  98%  170.33kB/s    0:00:01  
    18339047 100%  165.49kB/s    0:01:48 (xfer#16, to-check=13/157)
```

which works, but the log file isnt very tidy at all. 

I wondered if there was a way to get it to show something like

```
20110501@03:04 - Filename
```

is this possible?

many thanks as always

---

### Post by wgarcia on 2011-05-01
If you run it verbose ("rsync -v") it will give more information.

(Sorry: just saw that you are already including the "v" flag).

---

### Post by kg87 on 2011-05-01
haha yes. sometimes i wonder if its too verbose :p

i got a little further

on the same file that outputs the log, if i run

> less /path/to/log | grep *.tar

I get a little bit closer. 

i could output that to yet another file, but im still missing the date and time information. 

any ideas?

---

### Post by kg87 on 2011-05-02
anyone?!

---

### Post by pqwoerituytrueiwoq on 2011-05-02
you can dump it to a text file
```
rsync -rtuvO --progress /media/Backup/ /media/GPCF/TEMP/  >> /home/$USER/rsync_backup_log.txt
```edit try dropping the progress flag

---

