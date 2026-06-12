---
title: "Running a bash script in the background"
date: 2010-08-29
forum: General Help
---

### Post by Monotoko on 2010-08-29
Okay, so I have a basic script that watches my server, and informs me if it has gone down. I need to know how to run it without a console being open all of the time, I tried executing it with a trailing &, but to no avail. 

```
for (( ; ; ))
do
if ping -b -c 1 chatify.net
then
sleep 5m
else
echo "Problems"
cd /home/monotoko/scripts
chmod +x ./siren.wav
aplay ./siren.wav
sleep 5m
fi
done
```

This is what it gave me when I tried to run it with & (and the internet was off)

```

monotoko@Katie-III:~$ ./scripts/moniter.sh &
[1] 3112
monotoko@Katie-III:~$ ping: unknown host chatify.net
Playing WAVE './siren.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

Then i needed to leave it open...I need it in the background, any ideas?

---

### Post by ngrieb on 2010-08-29
If I'm not mistaken you can just run the command "bg" after the bash run command in the terminal to put applications in the background, and "fg" to bring them back to the foreground. Someone should check me on this though.

---

### Post by Vaphell on 2010-08-29
ping by ip?

---

### Post by Monotoko on 2010-08-29
> **ngrieb said:**
> If I'm not mistaken you can just run the command "bg" after the bash run command in the terminal to put applications in the background, and "fg" to bring them back to the foreground. Someone should check me on this though.

Elaborate? Once I have given it the command to run, the terminal has gone

---

