---
title: "Command line question"
date: 2010-04-05
forum: General Help
---

### Post by terry2001 on 2010-04-05
Hi Guys,
            I'm currently doing a HD recovery which is placing recovered files in Directories 'Recovered 1', 'Recovered 2'...3....4. I want to run a command to search through the various directories for, say *.mp3 and place identified files in Dir /home/terry/mp3 and then to use the same command structure find and copy *.divx *.mp4 *.jpg... and so on.

Thanks in advance for replies,
                                            Terry

---

### Post by KeyserSoze93 on 2010-04-05
```


mkdir ~/mp3

find /media/backup -iname "*.mp3" -exec mv '{}' ~/mp3 \;


```

etc...

---

### Post by terry2001 on 2010-04-05
Thanks fo quick reply keyser... will give that a go when recovery finishes.
                                                                                                          Terry

---

### Post by terry2001 on 2010-04-05
Works a treat many thanks for your help. Sorted

---

