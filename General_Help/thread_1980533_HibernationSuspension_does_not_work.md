---
title: "Hibernation/Suspension does not work"
date: 2012-05-15
forum: General Help
---

### Post by Cfa77 on 2012-05-15
Hello!!!

I have an Acer Aspire 5535 and I have Kubuntu 12.04 installed. My problem is everytime I suspend my computer or when it hibernates, when I wake it up the screen remains black. Meanwhile, I've been searching the web and I found these code:

step 1: create this file as superuser:

gksudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd 

step 2: Insert the following code in the file and save it.


#!/bin/sh
#inspired by [http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19](http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19)
#...and [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)    
# tidied by tqzzaa :)

VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac

step 3: add executable permission

sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd



 My question is: is this code safe? If not, what alternatives do I have? I could really appreciate some help. Tks

---

### Post by urlwolf on 2012-05-15
I have this problem too.
Linux in general has a lot of problems with suspend.
You may get lucky and get hardware where it works 80% of the time. Consider yourself blessed. Stop tweaking it.

If it doesn't work, my advice is ignore the problem, or try different hardware. If you start trying things, you are entering a  time-wasting black-hole. Sorry to be so negative. I´ve been using linux for 10 years.

---

### Post by Cfa77 on 2012-05-16
Yes, but I actually tried the code and everything remains the same - I can't suspend my laptop yet. Is there any other way to go around this bug? I really need the suspension working. Another thing I heard is that one can disable the aditional proprietary drivers from ATI and the suspension returns to normal, but I haven't tested that yet.

Does anyone know if even if I disable the proprietary drivers will the graphics card still be working on Kubuntu?

---

