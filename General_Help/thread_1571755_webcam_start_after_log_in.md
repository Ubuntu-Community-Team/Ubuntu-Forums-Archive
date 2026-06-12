---
title: "webcam start after log in"
date: 2010-09-10
forum: General Help
---

### Post by M93 on 2010-09-10
i'm trying to let the built in webcam shoot a pic as soon as a login is made...is there a way to that?
thank u :)

---

### Post by Neezer on 2010-09-10
> **M93 said:**
> i'm trying to let the built in webcam shoot a pic as soon as a login is made...is there a way to that?
thank u :)

I'm not good with scripting, but you could add a script for a program like cheese to the startup cron...That is my idea on "is there a way to do that." I'm pretty sure it would work, but I haven't the foggiest idea on how to implement it.

---

### Post by M93 on 2010-09-10
thats how i was thinking about it too 'a script', but am not good at all not even close :D
thanks :)

---

### Post by Joe of loath on 2010-09-10
I seem to remember mplayer or xine is able to take pictures using a webcam. Maybe someone more experienced in scripting can help.

---

### Post by M93 on 2010-09-10
there are alot of programs to do the job...the problem is how to make it do the job ;)
thank u :)

---

### Post by M93 on 2010-09-10
WOW 1000+ views and no one has an answer!!
is it impossible or what?! :D

---

### Post by M93 on 2010-09-16
i've been searching for a solution for 5 days now, posted in several forums
and same answer 'none'
i asked my professor for a hint, and he said he'll have to minus my grade a 30%
i really need help here i'm desperate :(

---

### Post by Gunman1982 on 2010-09-16
First try to take a picture over the console/terminal. For that look here: [http://ubuntu.online02.com/node/25]("http://ubuntu.online02.com/node/25")
I didn't try it since I don't have a webcam at hand.
Another way: [http://ubuntuforums.org/showthread.php?t=1337440&highlight=webcam+command+line]("http://ubuntuforums.org/showthread.php?t=1337440&highlight=webcam+command+line")

Next you want to execute that line as autostart, so look here:
[http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/]("http://www.howtogeek.com/howto/ubuntu/how-to-add-a-program-to-the-ubuntu-startup-list-after-login/")

I don't know if it suits your needs, if not then you have to give more information.

---

### Post by piratebill on 2010-09-16
There is a sweet terminal program called motion.  Basically if it detects any movement through the web cam, it records that image to a predetermined location.  What I would do is write a perl script that launches motion and monitor the directory its writing to.  Once the image is written, terminate.

---

### Post by M93 on 2010-09-16
first of all thanks alot, i really appreciate this :)

i've reached this line through ur links, gunman 1982

```
$ streamer -t 0:0:5 -c /dev/video0 -f rgb24 -r 3  -o   outfile.avi
```

made it work, even better caz its a video and can control the duration :)
the problem is that when i make several log in's the file 'outfile.avi' is replaced by the latest log in clip...is it possible to have a file for each log in?

---

### Post by Silvernail on 2010-12-05
> **M93 said:**
> first of all thanks alot, i really appreciate this :)

i've reached this line through ur links, gunman 1982

```
$ streamer -t 0:0:5 -c /dev/video0 -f rgb24 -r 3  -o   outfile.avi
```

made it work, even better caz its a video and can control the duration :)
the problem is that when i make several log in's the file 'outfile.avi' is replaced by the latest log in clip...is it possible to have a file for each log in?
Your professor is telling you to get familure with your command line apts.
Now I want 30% of your grade.

[SIZE="5"]$date[/SIZE]

---

