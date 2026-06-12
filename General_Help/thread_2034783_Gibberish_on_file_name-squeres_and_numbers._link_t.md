---
title: "Gibberish on file name-squeres and numbers. link to example file and a picture"
date: 2012-07-29
forum: General Help
---

### Post by xp15 on 2012-07-29
I'm having a problem of gibberish in filename. picture:

[IMG]http://i.stack.imgur.com/B6kOX.png[/IMG]


That how the Gibberish is look. here also a download for an one empty folder with gibberish on its filename: [http://theag.co/ht/LALOT/data/AAA.zip](http://theag.co/ht/LALOT/data/AAA.zip)

I tried convmv, but it says it's already UTF-8. so encoding may not be the problem.
 output of convmv-It seems not copyable (it's on th Desktop, "con" folder and in Jazz2 threre's also another file with gibberish):

        ```
ubuntu@PrecisePangolin:~$ convmv -r -f windows-1255 -t UTF-8 /home/ubuntu/*
        Your Perl version has fleas #37757 #49830 
        Starting a dry run without changes...
        Skipping, already UTF-8: /home/ubuntu/&#1490;&#1497;&#1489;&#1493;&#1497; gta sa/&#1514;&#1497;&#1511;&#1493;&#1503; &#1500;&#1492;&#1508;&#1506;&#1500;&#1492;
        Skipping, already UTF-8: /home/ubuntu/&#1490;&#1497;&#1489;&#1493;&#1497; gta sa/dsound.dll &#1490;&#1497;&#1489;&#1493;&#1497;/&#1502;&#1511;&#1493;&#1512;&#1497; &#1502;XP &#1513;&#1500;&#1497;
        .
        .
        .
        Skipping, already UTF-8: /home/ubuntu/&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492;/&#1495;&#1489;&#1500;-&#1497;&#1513; &#1506;&#1493;&#1491; &#1502;&#1511;&#1493;&#1501; &#1508;&#1504;&#1493;&#1497; &#1489;&#1514;&#1511;&#1500;&#1497;&#1496;&#1493;&#1512;
        Skipping, already UTF-8: /home/ubuntu/&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492;/  
        Skipping, already UTF-8: /home/ubuntu/&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492;/con/  
        Skipping, already UTF-8: /home/ubuntu/&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492;/Jazz2/ !.txt
        Skipping, already UTF-8: /home/ubuntu/&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492;
        .
        .
        .
        Skipping, already UTF-8: /home/ubuntu/&#1514;&#1502;&#1493;&#1504;&#1493;&#1514;/TESTDISK/&#1502;&#1497;&#1511;&#1493;&#1501; &#1511;&#1493;&#1489;&#1509;.png
        Skipping, already UTF-8: /home/ubuntu/&#1514;&#1502;&#1493;&#1504;&#1493;&#1514;
        No changes to your files done. Use --notest to finally rename the files.
        ubuntu@PrecisePangolin:~$ 
```I also tried running:

    ```
sudo apt-get install unifont 

```but I didn't see any changes, should I logout and login or restart?


any solution and suggest is appreciated (:

---

### Post by Kelvari on 2012-07-29
Just as a shot in the dark, have you made sure that all packages have been installed for the language you're trying to use?

---

### Post by xp15 on 2012-07-29
> **Kelvari said:**
> Just as a shot in the dark, have you made sure that all packages have been installed for the language you're trying to use?

everything is installed and hebrew is the first in the list. also there is no asking to install more support.

there also a link to download if you want to check it a bit (:
or, any more solution?


Thanks!

---

### Post by xp15 on 2012-07-30
any ideas?

---

### Post by xp15 on 2012-07-30
> **xp15 said:**
> any ideas?

Please, Anyone?

---

### Post by xp15 on 2012-07-31
Bump. no one knows?
please, it's kind of imporatnt.

---

### Post by xp15 on 2012-08-02
bump

---

### Post by Vaphell on 2012-08-02
care to write what is supposed to be in place of that gibberish directory name? It's hard to debug the issue when you don't know the desired outcome.


if you can, try compressing to some other format (rar, ...), reportedly the zip format can be problematic with non-ascii characters.

---

