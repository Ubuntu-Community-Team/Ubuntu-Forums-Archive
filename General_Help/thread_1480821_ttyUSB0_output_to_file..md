---
title: "ttyUSB0 output to file."
date: 2010-05-12
forum: General Help
---

### Post by projkt4 on 2010-05-12
Hi, I'm working with a [ft232r]("http://www.sparkfun.com/commerce/product_info.php?products_id=718") breakout board and a [ID-12 RFiD]("http://www.sparkfun.com/commerce/product_info.php?products_id=8419") card reader. I've got it all working fine, i can even use minicom to see the output. my problem is that when writing a script to capture the output fro ttyUSB0 (the port the usb to serial works on) i get this for output:

```
$ sh cardreader
2500ABCF3776
: not found 6: 2500ABCF3776

```

my script is this:
```

stty -F /dev/ttyUSB0 9600 cs8 -cstopb -parenb -cooked min 1 time 1
while true; do
        read LINE < /dev/ttyUSB0
        echo $LINE
        $LINE >> out
done

```

ultimately I'd like to get the output from each card show up as a new line in my output text file. the closest I've gotten is with this code :


```

stty -F /dev/ttyUSB0 9600 cs8 -cstopb -parenb -cooked min 1 time 1
while true; do
        cat /dev/ttyUSB0 > ./out

```



but the output into my out file is :
```
^B2500ABCF3776
^C^B2500AC1F52C4
^C^B2500AC0D199D
^C

```

the output adds the "^C^B" or more appropriately it adds "^B" to the beginning of each rfid code, and "^C" after the end on a new line. how do i fix either of my codes?

---

