---
title: "crontabs?"
date: 2006-03-21
forum: General Help
---

### Post by jjbird on 2006-03-21
I am trying to use the crontabs and Im not entirely sure how, I cant get it to work.  I looked at a few tutorials but that was only so helpful.  I think the problem is with the command. How is the command part of the crontab supposed to be done, and what kind of commands can it be done with?

Thanks

---

### Post by colo on 2006-03-21
The documentation to cron and crontab, provided via their man-pages, should clarify tose things for you.

```
whatis cron
man crontab
```

---

### Post by jjbird on 2006-03-21
I looked at them both and it didn't really help much, it explained the -* but it didn't explain how to write a crontab correctly.

---

### Post by taurus on 2006-03-21
What do you want to run?  If you can provide an example, I am sure somebody would tell you how to do it!!!

---

### Post by harisund on 2006-03-21
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

Nice intro which is what I used to learn about cron jobs.. 

Also, if you have something in mind, post that down and somebody could write you a crontab file for it ..

---

### Post by jjbird on 2006-03-21
I'm trying to turn my computer into an alarm clock, so i want to play a music file at some ridiculously early hour of the morning.

---

### Post by colo on 2006-03-22
Ok, assuming you want to have the file "/home/yourself/alarm.mp3" played with the program "/usr/bin/mpg321", precisely at 6:41am in the morning, the corresponding line in your crontab would look like the following:
```
41 6 * * * /usr/bin/mpg321 /home/yourself/alarm.mp3
```

The same as the above, but for, say, 9:38pm:
```
38 21 * * * /usr/bin/mpg321 /home/yourself/alarm.mp3
```

If you want to have "/bin/someprogram" run every 5 minutes (starting at 0:00, then 0:05, 0:10 and so on), you'll put the following in your crontab:
```
*/5 * * * /bin/someprogram
```

I'm too lazy right now to make up other examples, but I'm pretty sure you're able to make it on your own from now on, right? :)

---

### Post by jjbird on 2006-03-22
The sample was helpful and im sure im getting closer but it still doesnt work.  This is what i have

```
30 17 * * * /usr/bin/rhythmbox /home/bird/go.ogg

```

i have also tried doing this with totem, a .flac file, and using a different time. none of these have worked

---

### Post by colo on 2006-03-23
rhythmbox is, afaik, a X11-client-application, and therefore not able to start without an environemt-variable called DISPLAY pointing to a X11-display its starting user has access to. Try again with a command-line-interface-based player, it should work just fine.

---

### Post by jjbird on 2006-03-23
Uh, pretend for a second that I don't know of any command line interfaced players, what is one that I could use :)

---

### Post by jrib on 2006-03-23
[QUOTE=colo]The documentation to cron and crontab, provided via their man-pages, should clarify tose things for you.

```
whatis cron
man crontab
```[/QUOTE]

```
man 5 crontab
``` too

---

### Post by Azrael on 2006-03-23
[quote=jjbird]Uh, pretend for a second that I don't know of any command line interfaced players, what is one that I could use :)[/quote]
The one colo used in his example, for example. ;)

sudo apt-cache show mpg321
sudo apt-get install mpg321

(or to look for others: sudo apt-cache search command player)

---

### Post by colo on 2006-03-24
mpg321 or mpg123 for mp3, ogg123 for OGG VOrbis, mplayer for pretty much everything.

---

