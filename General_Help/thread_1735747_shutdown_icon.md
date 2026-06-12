---
title: "shutdown icon"
date: 2011-04-21
forum: General Help
---

### Post by flipper T on 2011-04-21
i have created a shortcut in my panel that when selected, schedules the laptop to shut down after 60 mins (simply sudo shutdown -h 60)

what i would like is that if i press the _**same**_ shortcut again, the scheduled shutdown would be cancelled (presumably just sudo shutdown -c)

anyone know how ?


i have tried the various available shutdown apps and have found them all to be very flaky.

---

### Post by Krytarik on 2011-04-21
This script checks if the process "shutdown" is already running, and if so, it cancels the shutdown, otherwise it initiates it. It even gives a message at the screen, you need the package "libnotify-bin" therefore.
```
#!/bin/sh

if ps ax | grep -v grep | grep shutdown > /dev/null
then
    gksu "shutdown -c"
    notify-send -i system-shutdown-panel Shutdown 'cancelled.'
else
    gksu "shutdown -h 60" &
    notify-send -i system-shutdown-panel Shutdown 'in 60 minutes!'
fi
```Greetings.

---

### Post by flipper T on 2011-04-21
hi & thx for your time & effort, however i'm a complete novice when it comes to bash scripts so a few questions

1. do i save this script in my home folder, if so, as what ?

2. how do i get my current shortcut to call upon this script ?

i have installed libnotify-bin in anticipation of your response.


sorry for the idiot questions :(

---

### Post by flipper T on 2011-04-21
ah!

worked it out, if anyone else interested : [http://ubuntuforums.org/archive/index.php/t-326808.html](http://ubuntuforums.org/archive/index.php/t-326808.html)


thx again

shortcut works perfectly

may rename it in your honour :)

---

### Post by Krytarik on 2011-04-21
Personally, I would place it into "/usr/local/bin".
- create a file called "shutdown-timer", for example, to distinguish it from the actual "shutdown" command, and avoid confusion:
```
gksu gedit /usr/local/bin/shutdown-timer
```
- copy&paste the content into it
- save/quit
- make the script executable:
```
sudo chmod +x /usr/local/bin/shutdown-timer
```

To update your launcher:
- right-click at it
- choose "Properties"
- just enter "shutdown-timer" into "Command" (since its location is included by the PATH variable)

---

### Post by Krytarik on 2011-04-22
Hey, I just learned how to use Zenity! This is even cooler now. =) Now you can even specify a timer, with a slider, the default is 60 mins, and if you just press "Cancel", it does just that.
```
#!/bin/sh

if ps ax | grep -v grep | grep shutdown > /dev/null
then
    gksu "shutdown -c"
    notify-send -i system-shutdown-panel Shutdown 'cancelled.'
else
    timer=$(zenity --title="Shutdown Timer" --scale --text="Set shutdown timer (in minutes):" --value=60 --max-value=120)
    if [ -n "$timer" ]; then
       gksu "shutdown -h $timer" &
       notify-send -i system-shutdown-panel Shutdown 'in '$timer' minutes!'
    fi
fi
```Update: I just yet noticed that with either setup, the confirmation message gets displayed even while you are still being asked for your password, and it doesn't matter at all if you enter the correct password or just cancel. But I don't know how to fix that right now, without implementing a complex repeated process query, since 'shutdown' must be definitely put into background, otherwise those message wouldn't get displayed at all.

---

### Post by flipper T on 2011-04-22
when i run this all i get is a pop up box saying shutdown cancelled ?

---

### Post by Krytarik on 2011-04-22
> **flipper T said:**
> when i run this all i get is a pop up box saying shutdown cancelled ?
No, it doesn't, at least it shouldn't. Is that the case at your system then?

It just doesn't matter if you enter your password at all, or an incorrect one, the messages will get displayed anyway.

Generally, I prefer calling only the actual commands in the script with "gksu", not the script itself. But in this case it is actually better to put it the other way around, to work around the above mentioned issue. This also puts its behaviour in line with the majority of the usual admin tools, to query the password before you even get the chance to change something.

So, put the "Command" for the launcher like this:
```
gksu shutdown-timer
```And the script like this:
```
#!/bin/sh

if ps ax |grep -v grep |grep shutdown >/dev/null
then
    shutdown -c
    notify-send -i system-shutdown-panel Shutdown 'cancelled.'
else
    timer=$(zenity --title="Shutdown Timer" --scale --text="Set shutdown timer (in minutes):" --value=60 --max-value=120)
    if [ -n "$timer" ]; then
       shutdown -h $timer &
       notify-send -i system-shutdown-panel Shutdown 'in '$timer' minutes!'
       pkill gksu
    fi
fi
```However, when I tested this setup some hours ago, I noticed that, if run the script from the command line, you doesn't return to the prompt.

After some hours of fiddling/researching/testing, I figured that the process "gksu" is actually the one that only ends if and when the process *it* called ends, and that this is also the case with the previous setup, but in this case you just don't notice it, because "gksu" is run in the background, and thus you return to the prompt.

While writing the previous sentence, I noticed that you can achieve the same behaviour at the command line with the new setup if you run it just like this:
```
gsku shutdown-timer &
```But that, of course, doesn't fix the actual issue, that "gksu" and "shutdown-timer" are still running in the background. So, a bit of an 'ugly' workaround for that is to kill "gksu" after initiating the actual "shutdown" process. That leaves those process running while the ones that initiated it get terminated. Thus I added the respective command just yet to the above stated script.

---

### Post by flipper T on 2011-04-22
once again, thx for all your efforts.

i am busy right now but will test & feedback as soon as possible.

---

### Post by Krytarik on 2011-04-22
> **flipper T said:**
> once again, thx for all your efforts.

i am busy right now but will test & feedback as soon as possible.
Take your time! I guess it eventually just turned into a welcome and funny opportunity for me to improve my skills and play a bit with scripts and processes, and even learn new features. :)

---

### Post by Krytarik on 2011-09-21
> **flipper T said:**
> when i run this all i get is a pop up box saying shutdown cancelled ?
If you are still interested in such a tool, I've pretty much overhauled the script, and just posted it at the link below. Everything works just fine now! :D

[http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html](http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html)

I know now why it behaved like this on your side, but not on mine: Because I only named the script "test", whereas you named it, as advised, "shutdown-timer". By this, the check for running "shutdown" processes returned the script itself, since I only filtered out the "grep" on 'shutdown', the actual search.

And I also managed to fix the issue with "gksu" keeping running endlessly: No use of "gksu" anymore, but "sudo" from inside the script, fed with the password through a Zenity query.

Also, I turned the confirmation messages previously delivered via NotifyOSD into Zenity info windows, makes it obviously more consistent, because you set the timer and enter your password in the middle of the screen also, already before the overhaul.

I would be happy if you have a look at it, and give feedback!

Greetings.

---

