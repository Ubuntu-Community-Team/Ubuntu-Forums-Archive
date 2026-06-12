---
title: "Can't edit ligthdm.conf from recovery mode"
date: 2012-04-25
forum: General Help
---

### Post by ignisuti on 2012-04-25
I need to edit my lightdm.conf file from recovery mode, but I'm told I the file is locked. I've tried sudo command without success. What else can I do?

**Background story of why I think I need to do this:**
I'm running Ubuntu 11.10 and needed to installed the older GUI for modifying users & groups in order to attempt to fix another problem I was having. After I installed this, I launched it and it sat there trying to load for hours. I couldn't even kill the app. I eventually gave up and forced a reboot. Since that time, my computer boots directly into XBMC and won't give me access to the Desktop. I can shutdown XBMC, but that takes me back to the login screen. If I login using any account, I get taken back to XBMC. 

So, I read somewhere that my lightdm.conf file might be culprit and setting XBMC as the default desktop. I booted into recovery mode and got to a terminal where I could open the file and saw "user-session=". I updated it to "user-session=ubuntu", but I can't save the file.

Please let me know if I'm hunting down the right rabbit hole.

---

### Post by strask on 2012-04-25
What command do you type when it tells you the file is locked? What is the specific error message?

(I have no idea if you are doing the right thing, hopefully someone else will chime in on that part.)

---

### Post by ignisuti on 2012-04-25
> **strask said:**
> What command do you type when it tells you the file is locked? What is the specific error message?

(I have no idea if you are doing the right thing, hopefully someone else will chime in on that part.)

It'll be at least half a day before I'm in front of that PC again. So, I'll have to tell you based on my memory.
I was using "sudo nano" to edit the lightdm.conf file. The nano app told me the file was locked when I attempted to "WriteOut" (save) it.

---

### Post by jerome1232 on 2012-04-25
I'll bet your root was mounted read only, remount it rw.

```
mount -o remount,rw /
```

---

### Post by ignisuti on 2012-04-25
> **jerome1232 said:**
> I'll bet your root was mounted read only, remount it rw.

```
mount -o remount,rw /
```

Do I type this in the same terminal I'm already using? Or, does this need to be input somewhere earlier on?

---

### Post by jerome1232 on 2012-04-25
once you get into single user mode (recovery  mode) run that, it'll remount the root file system (assuming I am correct and it is being mounted read only) and allow you to edit your file.

---

### Post by strask on 2012-04-25
> **ignisuti said:**
> Do I type this in the same terminal I'm already using? Or, does this need to be input somewhere earlier on?
I assume you are coming up in recovery mode and choosing the root shell option, right? If so, just type that at the prompt and then re-try editing your file.

If you are at a non-root prompt, you'll need to add 'sudo' to the front of the command.

---

