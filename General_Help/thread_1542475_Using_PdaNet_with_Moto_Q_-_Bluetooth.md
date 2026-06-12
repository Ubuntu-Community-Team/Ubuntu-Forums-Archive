---
title: "Using PdaNet with Moto Q - Bluetooth"
date: 2010-07-30
forum: General Help
---

### Post by pwilliams55 on 2010-07-30
I am new to Ubuntu but wanted to post my solution to getting my laptop (10.4) to use my Moto Q (9c) phone for tethering.

I followed a previous thread which had a great script to use with Wvdial but I kept getting the error "Cannot open /dev/rfcomm"

I fixed it by adjusting the script (see below) to manually bind to rfcomm and it worked !  I had to share.

The original thread is here:

[http://ubuntuforums.org/showthread.php?t=629528&highlight=pdanet+moto](http://ubuntuforums.org/showthread.php?t=629528&highlight=pdanet+moto)


*******************
#!/bin/bash
echo "Finding PDAnet Channel on MotoQ:"
CHAN=`sudo -H -u \#1000 sdptool browse 00:1E:8D:0B:E4:A9 | grep 'PdaNet Dial-up Networking' --after-context=8 | grep 'Channel' | cut -d ' ' -f 6`

echo "Manually binding to channel $CHAN"
sudo rfcomm bind rfcomm$CHAN
echo "Dialing channel $CHAN:"
sudo -H -u \#1000 wvdial motoq$CHAN

---

