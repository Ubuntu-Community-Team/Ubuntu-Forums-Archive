---
title: "Trouble using Exaile as alarm clock"
date: 2010-04-20
forum: General Help
---

### Post by Teacher Lion on 2010-04-20
Hi,

For a while I used the following command to use Banshee as an alarm clock to get me up for work in the mornings:

echo "banshee --play" | at 09:00

I have since switched to Exaile because it's lighter. Here's the dilemma...

If I type 'exaile --play' in a terminal then it works and Exaile plays. However, if I type 'echo "exaile --play" | at 09:00' as I did with Banshee then it doesn't work.

I'm not good enough at this yet so I'm fairly confused. Any ideas on how to sort this one out? I might sleep in tomorrow and lose my job.

Thank you in advance,

Lion

---

### Post by Veteropinguis on 2010-04-20
I don't know about using Exaile, but this may work as a backup alarm:

```
sudo apt-get install alarm-clock
```

Go to Edit> Add > Create new alarm from scratch > Notification > Play Sound on event > Preferences > Use custom sound file > browse > the song you want to wake up to. It's not exactly what you're after, but you can get something going.

EDIT: You should also try putting this in Multimedia, you'd get more audio geeks there.

---

### Post by Teacher Lion on 2010-04-20
Thank you for the suggestion.

There are alternatives to using Exaile and the 'at' command and at the moment I am using them. However, I would like to figure out how to use Exaile and the task list that 'at' provides.

Looks like this is a tougher nut to crack than I thought it would be.

Again, thanks for the support.

---

