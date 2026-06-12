---
title: "Trouble updating from PPA for FocusWriter 1.3.5.2 (OS 12.04 )"
date: 2012-05-23
forum: General Help
---

### Post by writebunny on 2012-05-23
Hi all, 

I wanted to upgrade FocusWriter 1.3.5.1 (from the repository) to 1.3.5.2 (from a PPA) on Xubuntu. 

I followed the instructions from Focuswriter to use their PPA and typed the following in terminal:

```
sudo add-apt-repository  ppa:gottcode/gcppa
```and after that ran I typed in the following:

```
sudo apt-get update
```It looked okay to me - I didn't see errors anywhere. (I'm a newbie though)

So then the update manager prompted me - and I looked at the update list. It looked okay, but it wouldn't check the box for the specific update from Focuswriter. :-(  Try as I might, it wouldn't take it. Here is the screen I was seeing. Why is this failing to work? (Remember I'm a newbie and I know almost nothing yet about running Linux or Xubuntu. Only enough to get by so far.)

[IMG]http://i45.tinypic.com/fedo2x.png[/IMG]

---

### Post by Enigmapond on 2012-05-23
> **writebunny said:**
> Hi all, 

I wanted to upgrade FocusWriter 1.3.5.1 (from the repository) to 1.3.5.2 (from a PPA) on Xubuntu. 

I followed the instructions from Focuswriter to use their PPA and typed the following in terminal:

```
sudo add-apt-repository  ppa:gottcode/gcppa
```and after that ran I typed in the following:

```
sudo apt-get update
```It looked okay to me - I didn't see errors anywhere. (I'm a newbie though)

So then the update manager prompted me - and I looked at the update list. It looked okay, but it wouldn't check the box for the specific update from Focuswriter. :-(  Try as I might, it wouldn't take it. Here is the screen I was seeing. Why is this failing to work? (Remember I'm a newbie and I know almost nothing yet about running Linux or Xubuntu. Only enough to get by so far.)

[IMG]http://i45.tinypic.com/fedo2x.png[/IMG]

Try it from the terminal:

```
sudo apt-get install focuswriter
```

---

### Post by writebunny on 2012-05-23
Thank you for the tip of how to install from the terminal. 

I received the following info back from terminal just now:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 focuswriter : Depends: libzip1 (>= 0.8) but it is not installable
E: Unable to correct problems, you have held broken packages.


I see that it says it is missing dependencies. Is there anything I can do to resolve this? Is it a problem to have "held broken packages?"

---

### Post by Enigmapond on 2012-05-23
If you already have it install, ( a previous version) purge it and then try to install again...so:

```
sudo apt-get purge focuswriter && sudo apt-get autoremove

```

Then

```
sudo apt-get install focuswriter
```

---

### Post by writebunny on 2012-05-23
I've now purged it as instructed. Then I tried to install from terminal again. I get the same error about missing dependencies etc. 

Anything else I can do?

Thanks for helping me try to figure this out.

---

### Post by Enigmapond on 2012-05-23
> **writebunny said:**
> 
Anything else I can do? 

Well...see if you can do without it..LOL I've come to the end of what I can do. Can't you use Libre writer? Sorry I couldn't help more...cheers!:(:confused:

---

### Post by writebunny on 2012-05-23
Thanks Enigmapond. You've been a good help. 

I'll write to the author and see if he can shed some light. Fingers crossed.

---

### Post by Toz on 2012-05-23
It would appear that focuswriter requires libzip1 but that package is missing (or has been removed) from the repositories. Here is a related bug report: [https://bugs.launchpad.net/ubuntu/+source/libzip/+bug/990314]("https://bugs.launchpad.net/ubuntu/+source/libzip/+bug/990314").

Yup, its been removed: [http://www.ubuntuupdates.org/package/core/precise/main/base/libzip1]("http://www.ubuntuupdates.org/package/core/precise/main/base/libzip1")

---

### Post by writebunny on 2012-05-24
Hurray - I have good news!!

I was able to email with the author of FocusWriter, Graeme Gott. He found out what the issue was and it is resolved currently for the 32-bit version and will be resolved 2 hours from now for the 64-bit version. 

In specific he said this:

> It appears that when I built the FocusWriter package libzip1 was still 
in Xubuntu 12.04, but after that they switched it to libzip2. I have 
forced a rebuild of the FocusWriter package and it says it will build 
the 32-bit package an hour from now **[UPDATE: NOW READY]**, and the 64-bit package in 9 hours. **[UPDATE: READY TWO HOURS AFTER THE DATE OF THIS POST**]

Please let me know if you have any more issues! 


Thanks to Graeme for being so quick to respond and find a solution. This is simply fantastic. 

Thanks to Toz who alerted me to the status of that dependency. And of course thanks to Enigmapond for walking me through how to do some of this. 

):P

---

### Post by Enigmapond on 2012-05-24
Glad it worked out for you.  Cheers!\\:D/

---

