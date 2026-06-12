---
title: "i8kmon fan"
date: 2011-02-08
forum: General Help
---

### Post by qwertyjjj on 2011-02-08
Started a new thread as I am now using i8kmon instead of thinkfan.
Computer is an Inspiron 9300 laptop.

I am trying to control the fan speed as the BIOS has something wrong with it as it starts the fan at full speed right from when the OS is loaded.
Since I implemented i8kmon, the fan comes on correctly but when the temp drops below 43 it won't switch off setting 1.

part of the conf below:

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0) {{1 0} -1 50 -1 50}
set config(1) {{1 1} 43 60 43 60}
set config(2) {{1 2} 50 70 50 70}
set config(3) {{1 2} 50 128 50 128}

Any ideas, why it won;t switch off level 1?

Also, how can I control the GPU fan with i8kmon, there doesn't seem to be an option that will do anything...it only controls the cpu fan.

---

### Post by qwertyjjj on 2011-02-09
> **qwertyjjj said:**
> Started a new thread as I am now using i8kmon instead of thinkfan.
Computer is an Inspiron 9300 laptop.

I am trying to control the fan speed as the BIOS has something wrong with it as it starts the fan at full speed right from when the OS is loaded.
Since I implemented i8kmon, the fan comes on correctly but when the temp drops below 43 it won't switch off setting 1.

part of the conf below:

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0) {{1 0} -1 50 -1 50}
set config(1) {{1 1} 43 60 43 60}
set config(2) {{1 2} 50 70 50 70}
set config(3) {{1 2} 50 128 50 128}

Any ideas, why it won;t switch off level 1?

Also, how can I control the GPU fan with i8kmon, there doesn't seem to be an option that will do anything...it only controls the cpu fan.

any ideas on what to try?

---

### Post by dino99 on 2011-02-09
have you seen this thread ?

[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

---

### Post by qwertyjjj on 2011-02-09
> **dino99 said:**
> have you seen this thread ?

[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

that's what I followed but something switches the fan to full (speed 2) and i8kmon cannot switch it back

---

### Post by migs73 on 2011-02-09
> **qwertyjjj said:**
> 
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0) {{**1** 0} -1 50 -1 50}


From what I can see on the other thread the first number after the brackets is a -1 not a 1 (as per bold above).

Don't know if it's the problem but should be a fairly quick check.

Mike :)

---

### Post by qwertyjjj on 2011-02-09
> **migs73 said:**
> From what I can see on the other thread the first number after the brackets is a -1 not a 1 (as per bold above).

Don't know if it's the problem but should be a fairly quick check.

Mike :)

I'll try that.
Do you know if my GPU is supposed to have a fan?
Even when I try the i8kmon button applet, it only seems to control the CPU fan.

Edit:
No, that didn't work. It reaches 60, level 2 is turned on and then it just stays on.

```

# Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)	1

# Status check timeout (seconds), override with --timeout option
set config(timeout)	1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0)   {{-1 0}  -1  50  -1  50}
#set config(1)   {{-1 1}  45  70  45  70}
#set config(3)   {{-1 2}  70  128  70  128}

set config(0)   {{-1 0}  -1  50  -1  50}
set config(1)   {{-1 1}  43  60  43  60}
set config(2)   {{-1 2}  50  70  50  70}
set config(3)   {{-1 2}  50 128  50 128}


# For computer with 2 fans, use a variant of this instead:
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# set config(0)	{{-1 0}  -1  52  -1  65}
# set config(1)	{{-1 1}  41  66  55  75}
# set config(2)	{{-1 1}  55  80  65  85}
# set config(3)	{{-1 2}  70 128  75 128}

# end of file

```

i8kmon definitely starts with the computer as when I make it restart is has to stop it first.
sudo /etc/init.d/i8kmon restart
 * Stopping Dell Inspiron fan/cpu-temperature monitor i8kmon             [ OK ] 
 * Starting Dell Inspiron fan/cpu-temperature monitor i8kmon             [ OK ]

---

### Post by migs73 on 2011-02-09
Try i8kutils from synaptic, it works for me (Dell inspiron 1501).

You can't set the temp/fan but it seems to work fine for me (never gets above 60 deg C evne when doing CPU heavy stuff).

---

### Post by qwertyjjj on 2011-02-09
> **migs73 said:**
> Try i8kutils from synaptic, it works for me (Dell inspiron 1501).

You can't set the temp/fan but it seems to work fine for me (never gets above 60 deg C evne when doing CPU heavy stuff).

that's what i have isn't it? i8kutils managed with i8kmon

---

### Post by migs73 on 2011-02-09
I checked a couple of place and i8kutils made no mention of i8kmon, but you could well be right. I'll look around more.

Mike

---

### Post by migs73 on 2011-02-09
Just found this, haven't tried it (not sure I want to!!);

[http://ubuntuforums.org/showthread.php?t=1684657](http://ubuntuforums.org/showthread.php?t=1684657)

---

