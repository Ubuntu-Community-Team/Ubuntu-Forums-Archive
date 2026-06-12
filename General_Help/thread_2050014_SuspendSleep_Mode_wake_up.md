---
title: "Suspend/Sleep Mode wake up"
date: 2012-08-29
forum: General Help
---

### Post by Moeller on 2012-08-29
Hello, I was hoping someone here can help me out. I am using LTS 12.04, and at times I cannot get my computer to wake up from sleep mode. The screen just stays black and I cannot get it to come up without doing a a hard restart of my computer. Thank You for any help.

---

### Post by Toz on 2012-08-29
> **Moeller said:**
> and at times I cannot get my computer to wake up from sleep mode.

What do you mean by "at times"? Does it successfully resume sometimes? If so, have you noticed any patterns?

Also, what is the make and model of your computer?

---

### Post by Petro Dawg on 2012-08-29
I have that issue too on my Desktop computer.  Its a "common" problem usually due to an issue with the BIOS.  I've read suggestions that say to update the BIOS, but since I don't experience with that and I don't want to turn my computer into a paper weight, I just have the screen set to automatically turn off after a while and leave the computer on.  Since Ubuntu boots pretty fast anyway, its not that big a deal to just turn the computer OFF when not in use.

---

### Post by Moeller on 2012-08-30
Yes sometimes it wakes up and goes right into working, other times the screen just stays black, i can see the curser but that's it. I have to actually do a hard restart to get it working again.

---

### Post by Toz on 2012-08-30
What is the make and model of your computer?

---

### Post by Moeller on 2012-08-30
I apologize, i forgot to mention that. It is an Acer 7741z.

---

### Post by Toz on 2012-08-30
Can you post back her contents of /var/log/pm-suspend.log and /var/log/dmesg? You can use pastebinit to do this. From a terminal window:

```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
```
...and post back the links that are generated.

---

### Post by vegdaze on 2013-01-06
I have the same issue--my laptop never wakes up from the suspend mode. I always have to reboot my machine. Toshiba L755 also running Win7.

---

### Post by Toz on 2013-01-06
Hello and welcome to the forums, vegdaz.

Can you please provide more information as per post #7? From a terminal window, run:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
```
...and post back the link that is generated so that we can view your log files.

---

