---
title: "Running command after resume"
date: 2012-08-18
forum: General Help
---

### Post by quickk on 2012-08-18
Hi everyone, 

   I'm running kubuntu 12.04 on my first generation macbook air.   It runs great except that the synaptiks touchpad settings are always reset when the laptop resumes from suspend.  Running the command "synaptikscfg init" solves the problem and loads the values that I specified.

I would like to run this everything my latop resumes.  Reading up on how to do this, it seems that all I need to do is:

1. Include a bash script in the /etc/pm/sleep.d folder that has the following general form:

```
#!/bin/sh
case $1 in
suspend)
## COMMANDS THAT YOU WISH TO RUN BEFORE SUSPEND
#COMMAND1
echo "Suspeding ..."
;;
resume)
## COMMANDS THAT YOU WISH TO RUN AFTER RESUME
echo "Resuming ..."
;;
hibernate)
## COMMANDS THAT YOU WISH TO RUN BEFORE HIBERNATE
#COMMAND3
echo "Hibernating ..."
;;
thaw)
## COMMANDS THAT YOU WISH TO RUN AFTER RESUME FROM SUSPEND TO DISK
#COMMAND4
;;
esac
```

I got this info from [here]("http://ubuntu.5.n6.nabble.com/How-to-run-command-on-resume-from-quot-suspend-quot-td4978956.html") and [here]("https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks").

2. make the script executable

```
sudo chmod +x /etc/pm/sleep.d/00_myscript
``` 

(note: the naming convention is such that the "pm" utility will run all the scripts in alphabetical order when it suspends, and then in reverse order when the laptop wakes up.)

To run my command, I thought that this script would work:

```
#!/bin/sh
case $1 in
suspend)
;;
resume)
COMMAND="synaptikscfg init"
echo "Resuming ..."
echo "This is the command that will be run:"
echo $COMMAND
$COMMAND
;;
hibernate)
;;
thaw)
;;
esac

```

This does not work.   When I look at the log in /var/log/pm-suspend.log, I see this message:
```
Running hook /etc/pm/sleep.d/0000_touchpad resume suspend:
Resuming ...
This is the command that will be run:
synaptikscfg init
usage: synaptikscfg [-h] [--version] {init,load,save} ...
synaptikscfg: error: could not connect to X11 display

/etc/pm/sleep.d/0000_touchpad resume suspend: Returned exit code 2.

```

Why doesn't this work?

---

### Post by Marric on 2012-08-18
check this out [http://askubuntu.com/questions/73626/script-not-running-on-resume](http://askubuntu.com/questions/73626/script-not-running-on-resume)

---

### Post by quickk on 2012-08-19
Thanks!  Using this script, my problem was solved.

```
#!/bin/sh
case $1 in
suspend)
;;
resume)
export DISPLAY=:0.0
su -c -l mysusername "synaptikscfg init"
;;
hibernate)
;;
thaw)
;;
esac
```

(I named this file 0000_touchpad in order to ensure that it was the very last thing to run during the resume process).

---

