---
title: "Program a shell script to auto-terminate?"
date: 2012-01-10
forum: General Help
---

### Post by jmknash on 2012-01-10
Hello all.

I have a simple script which requests a voltage check using hardware and returns the value in decimal.

My problem is I want it to finish after cat so I do not have to manually CTRL+C, any ideas?

Thanks Jon.

````````````````````````````````````````````````````````````````
sudo stty -F /dev/ttyUSB0 19200      #Sets Serial Port Speed

sudo cat /home/jon/readvolt.txt > /dev/ttyUSB0 #Sends Binary Code to device

cat /dev/ttyUSB0 #Returns battery data instantly
```````````````````````````````````````````````````````````````

---

### Post by Paqman on 2012-01-10
Just put:
```

sleep 10
exit
```
at the end to have it wait for 10 seconds then end.

---

### Post by jmknash on 2012-01-10
Hi Paqman,

Thank you but unfortunately that does not work, this is the output:


jon@iClean:~$ ./readvolt
t

It's still flashing command cursor...if I terminate cat in another terminal window (killall cat) it does what I want, maybe run two scripts will work?

jon@iClean:~$ ./readvolt
t./readvolt: line 4:  1534 Terminated              cat /dev/ttyUSB0
jon@iClean:~$

---

### Post by CharlesA on 2012-01-10
The script should exit automatically when it finishes the last command.

What is the output of the cat command in question?

```
sudo cat /home/jon/readvolt.txt > /dev/ttyUSB0
```

This will probably give you a permission denied error since you are redirecting with sudo, but make sure each command runs successfully from a terminal before trying to figure out which one isn't working.

---

### Post by jmknash on 2012-01-10
Hi Charles,

The cat command doesn't finish unless manually terminated.

Okays! I have managed to get it working okay by forcing the system to run two commands at once, this is what I have done..


jon@iClean:~$ 
jon@iClean:~$ catterm | readvolts
Voltage:
t/home/jon/readvolt: line 5:  1792 Terminated              cat /dev/ttyUSB0
jon@iClean:~$ 


`````inside catterm```````
sleep 3
sudo killall cat
``````````````````````````

p.s The output of the Cat command is a Binary number

Jon

---

