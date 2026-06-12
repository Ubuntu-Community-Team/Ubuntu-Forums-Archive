---
title: "how to schdule program"
date: 2011-05-23
forum: General Help
---

### Post by Rakeshvijayan on 2011-05-23
Hi friends now a day its difficult to wake up at 2 o'clock and on the pc starting downloading
is there any way to schedule deluge program start at 2 o'clock

---

### Post by 3Miro on 2011-05-23
You need to learn a bit about Cron and how to edit crontab:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

This is exactly what you need.

---

### Post by Rakeshvijayan on 2011-05-23
how to set cron on deluge program on the specific time

---

### Post by 3rdalbum on 2011-05-23
Does it have to be Deluge?

In Transmission, you can set the normal download and upload speeds to zero, and set the Temporary Speed Limits to what you want the download and upload speed to be when it's downloading. You can also set times to toggle the Temporary Speed Limits.

So, in effect, Transmission is downloading nothing during the day, and then at 2 o'clock it enables Temporary Speed Limits which does your downloading. Then at 6 o'clock (or some other time of your choosing) it turns off Temporary Speed Limits, bringing your download rate back to zero.

---

### Post by Rakeshvijayan on 2011-05-24
Any one help me to set cron job .this is my requirement start deluge at 2 o'clock no need to  push download because it will automatically start downloads this is my ................i need to set it daily job

I give the command crontab -e on my terminal when it  open i wondered what should i do 

please give me the instruction for my above requirement 


thanks

---

### Post by blind2314 on 2011-05-24
> **Rakeshvijayan said:**
> Any one help me to set cron job .this is my requirement start deluge at 2 o'clock no need to push download because it will automatically start downloads this is my ................i need to set it daily job
 
I give the command crontab -e on my terminal when it open i wondered what should i do 
 
please give me the instruction for my above requirement 
 
 
thanks
 
 
Did you read the link provided to you above? It should answer most of your questions on how to write a cronjob, and how crontab is structured.

---

### Post by Rakeshvijayan on 2011-05-24
> **blind2314 said:**
> Did you read the link provided to you above? It should answer most of your questions on how to write a cronjob, and how crontab is structured.


00 02 * * * /deluge is it work

---

### Post by Rakeshvijayan on 2011-05-24
Is it enough /deluge after the time 

please give me the replay

---

### Post by Rakeshvijayan on 2011-05-24
I feel pity all my friend

---

### Post by Rakeshvijayan on 2011-05-25
00 02 * * * /deluge is it enough to start deluge at 2 0'clock at morning 


please any give me an answer

---

### Post by Rakeshvijayan on 2011-05-25
In windows I know all the program will installed on to the  program file so it is familear to all us the pgm with .exe file 

how how how in ubuntu find the path of the installed application .....

---

### Post by ApOgEEs on 2011-05-25
Here's 2 steps to run deluge or any program from cron

[LIST=1]
[*]find your program binary:
Type this command to find your deluge path:
```
$ which deluge
```
typically, it will be in /usr/bin/deluge


[*]run it from cron:
Add this line to your cron (assume your deluge is /usr/bin/deluge)
```
00 02 * * *  /usr/bin/deluge
```
[/LIST]

Hope it helps

---

### Post by Rakeshvijayan on 2011-05-28
Thanks friend it give me knew knowledge in linux But it not work for me, It may my mistake Thanks again I will try ....to get result

---

### Post by nitstorm on 2011-05-28
It does work, you just don't see it because you are not exporting it to the display 

In the cron this should be your code

```
00 02 * * *  export DISPLAY=:0 && /usr/bin/deluge
```

---

### Post by Rakeshvijayan on 2011-05-28
[LIST=1]
[*]run it from cron:
Add this line to your cron (assume your deluge is /usr/bin/deluge)
```
00 02 * * *  /usr/bin/deluge
```
[/LIST]

Hope it helps[/QUOTE]

by the command you give is correct i can able call the deluge package from the terminal 
but it is not able open by cron 


# m h  dom mon dow   command
40   9 * * *  /usr/bin/deluge


this is my command in cronfile

---

### Post by Rakeshvijayan on 2011-05-28
> **nitstorm said:**
> It does work, you just don't see it because you are not exporting it to the display 

In the cron this should be your code

```
00 02 * * *  export DISPLAY=:0 && /usr/bin/deluge
```


It working Thanks friend

---

### Post by ApOgEEs on 2011-05-28
> **Rakeshvijayan said:**
> Thanks friend it give me knew knowledge in linux But it not work for me, It may my mistake Thanks again I will try ....to get result

I just tested today and I can confirm that you are correct. It is not working like that. This is because you cannot simply run deluge from the cron since you didn't export the DISPLAY

Here is another easy steps (GUI) to make it work.

1. Install gnome-schedule
```
$ sudo apt-get install gnome-schedule
```

2. Open gnome-schedule. It should be in **Applications > System Tools > Scheduled tasks**

3. Click **New**, then click **A task that launches recurrently** button
[IMG]https://lh5.googleusercontent.com/-qTjMorX3M4Y/TeCssgA-KlI/AAAAAAAACVs/jSjUdJQ53mo/s640/gsched-apogee-01.png[/IMG]

4. Enter your details like this:
[IMG]https://lh6.googleusercontent.com/-ag69B7YB4XU/TeCswfWE8bI/AAAAAAAACVw/hWwM-IsDxlU/s640/gshed-apogee-02.png[/IMG]

5. Click **Add** and then **OK** in the next dialog.

Your deluge task will be running.

---

### Post by nitstorm on 2011-05-28
> **Rakeshvijayan said:**
> It working Thanks friend

Cheers! :D

---

### Post by Rakeshvijayan on 2011-05-28
Again and Again Thanks to my friends those who give support with kind .....am a bigner in  ubutnu . I need more support from You all
 Thanks again

---

### Post by nitstorm on 2011-05-29
Please mark the thread solved :)
Look at the Thread Tools drop down button on the top right...Click that and mark thread as solved.

---

