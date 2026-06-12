---
title: "Startup Application order (app after Compiz)"
date: 2010-05-08
forum: General Help
---

### Post by stringkarma on 2010-05-08
Hi everyone, rockin Lucid now and everything seems good except one small annoyance. 

I like to use Tilda in transparent mode. In Karmic I just added tilda to the startup applications and everything worked well. Now in Lucid, it starts up before Compiz and I don't get Compiz transparency. I have to quit Tilda and load it again before I get the transparency right. Is there some way to force tilda to start after Compiz? (I have tested this on several comps. it seems to hold true)

Thanks

---

### Post by stringkarma on 2010-05-10
Politely bump.

---

### Post by stringkarma on 2010-05-12
Ok so I have a script (called start_tilda.sh) I have to use it as the startup application. Its contents are simply "sleep 3 && tilda"

Is this really the way to do this?? There must be a more consistent way!

---

### Post by stringkarma on 2010-05-24
Again, politely as possible, bump

---

### Post by xurei on 2011-03-02
I found a way to do this, by using bash : 
> 
#!/bin/sh

#run_after_compiz.sh : allows to run an application after that compiz has been launched.

OPEN=0;

while [ $OPEN -eq 0 ]
do
OPEN=$(ps -e | grep compiz);
OPEN=${#OPEN};
echo "waiting for compiz...";
done

$*


Just type ./run_after_compiz.sh <app_command> to run the application. You cann of course use this in the startup configuration tool to make your application run after compiz.

Hope it will help.

---

### Post by buminatrain on 2011-03-03
this should answer your questions, and allow you to determine the best way to go about it 

[http://ubuntuforums.org/showthread.php?t=1119945](http://ubuntuforums.org/showthread.php?t=1119945)

I prefer to edit the autostart files hidden in the home directory.

---

