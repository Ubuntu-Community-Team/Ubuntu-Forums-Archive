---
title: "Auto boot into Ubuntu"
date: 2010-11-12
forum: General Help
---

### Post by laurenbanjo on 2010-11-12
I dual boot Ubuntu with Windows, so every time I turn on my computer, I have to choose a system. 

I rarely use Windows, but I still need it on here for some applications. Being that I'm going to be using Ubuntu 90% of the time, I was wondering if there was a way to boot directly to Ubuntu without erasing Windows.

Is this possible? I'd want to be able to press a key at start up or something so I can still use Windows if I want to. 

If that's not possible, how do I edit the boot screen so instead of 14 seconds (or whatever it is), it boots Ubuntu in one or two seconds?

---

### Post by Hippytaff on 2010-11-12
This should answer most...if not all of your questions :-D
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Cavsfan on 2010-11-12
> **laurenbanjo said:**
> I dual boot Ubuntu with Windows, so every time I turn on my computer, I have to choose a system. 

I rarely use Windows, but I still need it on here for some applications. Being that I'm going to be using Ubuntu 90% of the time, I was wondering if there was a way to boot directly to Ubuntu without erasing Windows.

Is this possible? I'd want to be able to press a key at start up or something so I can still use Windows if I want to. 

If that's not possible, how do I edit the boot screen so instead of 14 seconds (or whatever it is), it boots Ubuntu in one or two seconds?

You could enter **gksu gedit /etc/default/grub** to edit your GRUB2 config and make sure GRUB_DEFAULT=0 (meaning defaulting to the very top line.) 
And make sure this is zero GRUB_TIMEOUT=0 (this is the number of seconds to display the menu).
But then you would make it difficult to get to the windows install or anything but the top entry.

Take a look at the link in my signature. It shows you how to make a custom GRUB2 background and menu 
that is maintenance free and is very useful for dual booting as I am doing.

---

### Post by laurenbanjo on 2010-11-12
but, let's say, i make the time out 2. would that be good? 'cause once i press the down arrow key, the countdown stops. and I think 2 seconds is fast but enough time to press the key if I need to.

---

### Post by drs305 on 2010-11-12
> **laurenbanjo said:**
> but, let's say, i make the time out 2. would that be good? 'cause once i press the down arrow key, the countdown stops. and I think 2 seconds is fast but enough time to press the key if I need to.

That's generally what I do. 

The other option is to leave things at zero and then check to see if holding down the SHIFT key during boot brings up the menu. If it does, you can leave the timeout at 0 and use the SHIFT key should you need to select a non-default entry. If the SHIFT key check doesn't display the menu, the time to find out is *before* you need it so you can set the menu to display for a short time or hack the Grub2 scripts to force the SHIFT key to work.

---

### Post by Cavsfan on 2010-11-12
> **laurenbanjo said:**
> but, let's say, i make the time out 2. would that be good? 'cause once i press the down arrow key, the countdown stops. and I think 2 seconds is fast but enough time to press the key if I need to.

I have mine set to 60 seconds and still do not catch it in time sometimes. If you are not standing right there with 
your finger over the arrow key, you will not catch it in time. I would set it to 10 at least IMO.

There are some example pictures at the bottom of that tutorial in my sig.

---

### Post by thomas144 on 2010-11-12
I was able to do this successfully, and this is the configuration I use on my computer for the same reason you have.

Before your do anything, your should create a backup of the two file's we'll be editing:

cp /etc/default/grub ~/grub_backup && cp /etc/grub.d/30_os-prober ~/30_os-prober_backup


First, if you have a system with multiple operating systems (which you do), you have to tweak the script at /etc/grub.d/30_os-prober
To do this, run this command:
gksu gedit /etc/grub.d/30_os-prober

You will have to comment out the conditionals at APPROXIMATELY lines 28 and 62 of the file, like this:
First change this:
```
adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
```to this:
```

adjust_timeout () {
#  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
```And further down the file, change this:

```
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
```To this:
```
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
#  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
```Then you will have to edit /etc/default/grub. Run the command:
gksu gedit /etc/default/grub
And edit the file. Change
GRUB_DEFAULT=0
to
GRUB_DEFAULT=Whatever
Where Whatever is the position of the desired default entry (the one automatically booted into). Note that this starts at zero and not one. You probably want it to be 0, too.

Then change GRUB_HIDDEN_TIMEOUT to 0, like so:
GRUB_HIDDEN_TIMEOUT=0

Then, to finish up, run this command:
sudo update-grub

The effect of this (given I told you to do it correctly, and you did it correctly) is that your machine will immediately boot into Ubuntu UNLESS you hold the Shift key down from when you turn on your computer until you get a menu. How does this work for you?

<added>
P.S., here are two links that may help you:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Cavsfan on 2010-11-12
Thank drs305. I was trying to remember what key brought up the menu. The SHIFT key - I'll have to remember that. :)

---

### Post by Hippytaff on 2010-11-12
> **Cavsfan said:**
> Thank drs305. I was trying to remember what key brought up the menu. The SHIFT key - I'll have to remember that. :)

I need to remember that too...drs305 has helped me out a number of times.
my stupid 'what happens if I delete .bashrc' kind of moments
(s)he is and excellent ubuntuan :-D

---

### Post by laurenbanjo on 2010-11-12
> **thomas144 said:**
> 
You will have to comment out the conditionals at APPROXIMATELY lines 28 and 62 of the file, like this:
First change this:
```
adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
```to this:
```

adjust_timeout () {
#  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
```And further down the file, change this:

```
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
```To this:
```
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
#  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
```


Are the only differences between these the # sign? What does this do?

---

### Post by Cavsfan on 2010-11-12
> **laurenbanjo said:**
> Are the only differences between these the # sign? What does this do?
The **#** sign comments that line out so it is not executable.

---

### Post by laurenbanjo on 2010-11-12
Thanks!

I tried searching for the first part mentioned, but this is as similar as I can find:

```
make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
```

Should I do it to this instead...?

---

### Post by drs305 on 2010-11-12
The 30_os-prober file changed a while back, but the section you quoted is the new format. You would comment out (place a # symbol at the start of that line and in the last **fi** in that section. 

If your **x${found_other_os}** is line 29, the **fi** line to change would be line 63.

This change will allow the menu to be hidden even on a multiple OS system.

Don't forget to run "sudo update-grub" to incorporate the changes into the configuration file (grub.cfg).

---

### Post by laurenbanjo on 2010-11-12
thank you!

Sorry I'm stupid and keep asking questions.

but I just wanna be clear, for the default/grub one, am I changing

this
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
```

to this?
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
```

---

### Post by drs305 on 2010-11-12
Yes. If you have made the changes to 30_os-prober, to get the keystatus check (SHIFT) and no menu in a multi-OS system:

The GRUB_TIMEOUT (not shown in your post) and GRUB_HIDDEN_TIMEOUT must both be set to 0. So remove the # icon in your last post, save the file, then run "sudo update-grub".

---

### Post by laurenbanjo on 2010-11-12
It worked! :)

The only thing is for some reason it seems like it's taking a LOT longer to load... I did this mainly to save time since I won't really be using Windows, but I dunno, it seemed faster the other way. 

Maybe I'm just imagining it, though.

---

### Post by Cavsfan on 2010-11-14
My system has been taking longer to load for the past few weeks. I have a Conky that has a startup delay of 15 seconds
and it used to show my desktop within about 6-8 seconds and I would wait for the Conky to appear. Without a delay, Conky 
stays on top of anything on the screen - Firefox, etc. 

But, now the screen stays purple (as the login screen) and then appears after about 12-13 seconds and almost immediately 
after that the Conky appears. But, other than that all is fine.

So, that is my situation. Is yours any different drs305?

---

### Post by drs305 on 2010-11-14
> **Cavsfan said:**
> But, now the screen stays purple (as the login screen) and then appears after about 12-13 seconds and almost immediately 
after that the Conky appears. But, other than that all is fine.

So, that is my situation. Is yours any different drs305?

I have the 14 second pause with a black screen after the grub selection, then about another 10 seconds to the Desktop. The 10-15 second pause is common with a lot of users. Some users experience it, others don't; I don't know if anyone has found a way to prevent it for those experiencing it.

---

### Post by laurenbanjo on 2010-11-14
> **drs305 said:**
> I have the 14 second pause with a black screen after the grub selection, then about another 10 seconds to the Desktop. The 10-15 second pause is common with a lot of users. Some users experience it, others don't; I don't know if anyone has found a way to prevent it for those experiencing it.
I feel as if my wait has gotten a lot longer after I did this thing.

I'll have to time it.

---

