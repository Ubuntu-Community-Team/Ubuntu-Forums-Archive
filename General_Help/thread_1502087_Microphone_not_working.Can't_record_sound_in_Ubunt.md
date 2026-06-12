---
title: "Microphone not working.Can't record sound in Ubuntu."
date: 2010-06-05
forum: General Help
---

### Post by neoargon on 2010-06-05
In ubuntu,my  Microphone is not working , so I can't record sound or voice chat . It works well in windows. So it's not a hardware problem . Can anybody please help me? Is there anything I can do to make it working ? 
Please help me .

---

### Post by anand_30 on 2010-06-05
I think you input volume is low.

Left click on sound icon at top right.Select sound preferences.Select hardware tab and check if you are on Analog stereo duplex.Now go to Input tab and increase input volume to maximum and select connector as Analog Microphone/Microphone 1.Close.Check if it works using Applications>>Sound & video>>Sound Recorder.

Hope this helps.

---

### Post by neoargon on 2010-06-05
> **anand_30 said:**
> I think you input volume is low.

Left click on sound icon at top right.Select sound preferences.Select hardware tab and check if you are on Analog stereo duplex.Now go to Input tab and increase input volume to maximum and select connector as Analog Microphone/Microphone 1.Close.Check if it works using Applications>>Sound & video>>Sound Recorder.

Hope this helps.

Thanks for the help . . Now a lot of noise and my sound in very very  low voice can be heard . But that doesn't solve the problem .

---

### Post by anand_30 on 2010-06-05
> **neoargon said:**
> Thanks for the help . . Now a lot of noise and my sound in very very  low voice can be heard . But that doesn't solve the problem .

Ok then try this one.This does nothing much for my system but may work for you.

Go to terminal(press Ctrl+Alt+T)and type

```
alsamixer
```

You will get a screen now hit F5.
Search for Mic option and if it has MM at the bottom then going to that option press M and increase it to the fullest.You can also turn on option Mic boost the same way.

Now confirm that there is Mic 1 written above "Mic select" option if not then change it to Mic 1.

I have attached my alsamixer settings screenshot below but my Mic boost is Off.

---

