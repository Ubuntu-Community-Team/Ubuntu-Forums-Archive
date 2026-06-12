---
title: "importing from outlook express to mozilla thunderbird"
date: 2012-05-29
forum: General Help
---

### Post by hunterkasy on 2012-05-29
I have a old xp machine that I am using outlook express for email, I just got another machine up and running with Ubuntu 12.04, I was able to import my contacts to thunderbird, but I also would like all of my old emails imported also, does any one know how?

---

### Post by mike555 on 2012-05-30
You need to find the folder on Windows that holds your old emails, then convert them to eml using a free program like "unDBX", then import them into Thunderbird or just open them using Thunderbird.

---

### Post by Habitual on 2012-05-30
You *may* be able to install Thunderbird on the xp box and let Tbird import the Outlook Express mailbox(s)/messages there, then you should be able to export that to the Linux host.

---

### Post by hunterkasy on 2012-05-30
> **mike555 said:**
> You need to find the folder on Windows that holds your old emails, then convert them to eml using a free program like "unDBX", then import them into Thunderbird or just open them using Thunderbird.

I used undbx and that found the emails and exported them into a folder, now how do I import the emails into Thunderbird?

---

### Post by hunterkasy on 2012-05-30
> **Habitual said:**
> You *may* be able to install Thunderbird on the xp box and let Tbird import the Outlook Express mailbox(s)/messages there, then you should be able to export that to the Linux host.

I first tried doing this, but was unable to find a way to export the emails

---

### Post by Habitual on 2012-05-30
> **hunterkasy said:**
> I first tried doing this, but was unable to find a way to export the emails

Well, now you could copy the thunderbird profile directory to the linux host as ~/.thunderbird.  It may be under File > Run > %appdata% <enter> on the XP system

---

### Post by gordintoronto on 2012-05-30
> **Habitual said:**
> You *may* be able to install Thunderbird on the xp box and let Tbird import the Outlook Express mailbox(s)/messages there, then you should be able to export that to the Linux host.

I did exactly this when I moved to Ubuntu. Worked perfectly.

---

### Post by hunterkasy on 2012-05-31
> **gordintoronto said:**
> I did exactly this when I moved to Ubuntu. Worked perfectly.

how do you do that, I could not find any place to do it

---

### Post by Habitual on 2012-05-31
you need to "find" the thunderbird profile directory on the xp box and copy that directory carefully to the ~/.thunderbird directory on the linux host.

Try this on XP:
command prompt 
```

cd \ <enter>
dir profiles.ini /ah /s/p 
```

Paste the results here please.

---

