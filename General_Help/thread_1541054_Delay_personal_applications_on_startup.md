---
title: "Delay personal applications on startup"
date: 2010-07-28
forum: General Help
---

### Post by nodnolse1 on 2010-07-28
I use to auto start Firefox and Thunderbird. I would like to add others but using a delay. For instance, Firefox starts with 10 seconds of delay, Thunderbird with 30 second an so on. I tried to make a script using "sleep" command, but I am not expert and nothing worked. So, do you know if already exist an application that does this if not, are you able to show me how to create the script?

Thank you, Paolo


If can help, I link the script that i made [http://paste.ubuntu.com/469892/](http://paste.ubuntu.com/469892/)

---

### Post by prodigy_ on 2010-07-28
It's not ```
#/bin/bash
``` it's ```
#!/bin/bash
```
The rest of your script is ok.

Also make sure that the file where you saved your script has "execute" permission.

---

### Post by nodnolse1 on 2010-07-28
> **prodigy_ said:**
> It's not ```
#/bin/bash
``` it's ```
#!/bin/bash
```The rest of your script is ok.

Also make sure that the file where you saved your script has "execute" permission.

I tried also wit "#!/bin/bash", I set it executable but nothing to do. I kept the script on the desktop just to testing it, should be the location the problem?

---

### Post by prodigy_ on 2010-07-28
This is strange.

You say the script is on your desktop. Open terminal and run the following command: ```
bash ~/Desktop/<your_script>
``` Does it work?
(Of course you need to use the actual file name instead of <your_script>.)

---

### Post by nodnolse1 on 2010-07-29
> **prodigy_ said:**
> This is strange.

You say the script is on your desktop. Open terminal and run the following command: ```
bash ~/Desktop/<your_script>
``` Does it work?
(Of course you need to use the actual file name instead of <your_script>.)

I tried to run ~/Desktop/stupapps.sh but it it dead, nothing happens. I used "bash" and as well i tried w/o, no response ...

---

### Post by aeiah on 2010-07-29
```
#!/bin/sh

sleep 1 && gnome-terminal -x top &
sleep 20 && firefox &
sleep 20 && thunderbird &
sleep 10 && skype-wrapper &
sleep 15 && pidgin &

```


that should work fine. does for me. i changed your top command so it's run in gnome-terminal

&& is 'and then'
& is 'and also'

im guessing your script either stopped running when it started top, or it started top and waited for top to finish. because top is cli, it was hidden from you

---

### Post by tbird222 on 2011-05-31
Thanks so much -- this worked like a charm !!

---

