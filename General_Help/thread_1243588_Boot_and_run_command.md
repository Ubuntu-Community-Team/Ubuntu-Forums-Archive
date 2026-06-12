---
title: "Boot and run command"
date: 2009-08-18
forum: General Help
---

### Post by Psycho.mario on 2009-08-18
In windows, it is possible to schedule a task, and if you tick a certain checkbox it will boot your computer to run this task if it is turned off. 
Is this possible in ubuntu? For example, i would like my computer to turn on in the morning, play an mp3, open up my email and RSS feeds. How can i do this? 

Thanks

---

### Post by DeMus on 2009-08-18
> **Psycho.mario said:**
> In windows, it is possible to schedule a task, and if you tick a certain checkbox it will boot your computer to run this task if it is turned off. 
Is this possible in ubuntu? For example, i would like my computer to turn on in the morning, play an mp3, open up my email and RSS feeds. How can i do this? 

Thanks

I have never done it myself but i know the answer to your question is called cron. Try to read about it, for example "man cron" will give you help. Or google some.

---

### Post by Psycho.mario on 2009-08-18
I don't feel up to reading man cron at the moment. So i've installed gnome-schedule. If i set a command then turn off my computer, will it boot for me?


Thanks

---

### Post by DeMus on 2009-08-18
> **Psycho.mario said:**
> I don't feel up to reading man cron at the moment. So i've installed gnome-schedule. If i set a command then turn off my computer, will it boot for me?


Thanks

Yes, it will since it is just a GUI (interface) for Cron. So you are using Cron as I suggected but control it through a GUI called Gnome-schedule.

---

### Post by Psycho.mario on 2009-08-19
I tried crontab, i added this:
```
0 12 19 8 3 echo "crontab" > ~/Desktop/crontest
```
at 5 to 12, then shut off my computer. But it didn't turn on to do the job. 
How can i get it to do this?

thanks

---

### Post by DaithiF on 2009-08-19
No, cron can't do this.  It is only running when the computer is running.

The Windows 'Wake the computer to run this task' feature only works if your PC is hibernated, NOT if it is fully powered off, as far as I know.  It relies on the capabilities of your BIOS to make this happen, so on some computers it just won't work.

If your BIOS supports this under windows then the BIOS may also allow you to schedule a wake up at a certain time -- when booting the PC watch for the instruction to 'hit some key to enter setup' before Ubuntu starts loading, hit that key and you'll get to your BIOS screens -- have a look around there for some options to schedule a wake-up.

If there isn't anything like that in your BIOS, then I think you may be out of luck.

---

### Post by Psycho.mario on 2009-08-19
I know i can schedule turning on from my BIOS but that would mean i'd have to add whatever i wanted to run (email/RSS) to startup and i wouldnt want this to happen on every boot. Its a shame, but i won't go back to windows just for that. im sure it could be implemented at some point.

thanks

---

### Post by DaithiF on 2009-08-19
No, you'd just need the BIOS to schedule the wake up, the running of your programs you can schedule in Cron.  Once the computer is running then cron can kick in and do its stuff.

---

### Post by Psycho.mario on 2009-08-19
I can't do one-off boots in my BIOS, i can do a certain day at a certian time every week, so i'd have to set it in BIOS, then after it has booted, turn it off in BIOS. Not really worth it,  i might as well just fall out of bed and press the on button myself.

---

