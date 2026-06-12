---
title: "Can't burn CDs"
date: 2010-04-10
forum: General Help
---

### Post by pcdave98 on 2010-04-10
Hello.

I can play CDs and DVDs but when I try to burn a music CD I get:

[I]error while burning

an unknown error occurred [/I] 

             when the CD is finalising. As data has been written to the CD, but not finalised, each time I try I use another CD.

I've used Brasero and whatever the default burner in 9.10 is with the same result. If I boot in Win7 I can burn CDs.

Where do I start?

:confused:

---

### Post by ubunterooster on 2010-04-10
Try K3B

---

### Post by pcdave98 on 2010-04-10
I tried installing K3B:

***This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.***

:(

Now I want to poke Ubuntu in the eye.

---

### Post by ubunterooster on 2010-04-10
But before you start poking, run update manager (assuming you are net connected)

---

### Post by pcdave98 on 2010-04-10
> **ubunterooster said:**
> But before you start poking, run update manager (assuming you are net connected)


I'm bang up to date, ubunterooster.

:P

I'm starting to poke..

---

### Post by ubunterooster on 2010-04-10
Okay, I'll dig around some more :/ 
(meantime make sure you are not burning at full speed)

---

### Post by steveneddy on 2010-04-10
How did you try to install K3B?

Did you:

```
sudo apt-get install k3b
```

??

If not - try that method.

Maybe you don't have all the repos activated?

Go into software sources and check Universe, multivers and restricted

System --> Administration --> Software Sources

EDIt:

And, yes, try burning at 4X speed.

---

### Post by ubunterooster on 2010-04-10
k3b has a lot of dependencies. You could try the minimalistic xfburn.
I'm less than 10 min from zombieland; not enough sleep. 
[I'll not be avalible till monday, so I'll check your progress status then. Hopefully it will be fixed by someone else by then]

---

### Post by pcdave98 on 2010-04-11
I've tried burning at 4X - same result. I tried installing K3B through software centre.

Command line gives:
[I]
dave@dave-desktop:~$ sudo apt-get install k3b
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  k3b: Depends: kdebase-workspace-bin but it is not going to be installed
E: Broken packages
dave@dave-desktop:~$ [/I]


I'm requesting an impossible situation.

:P

---

### Post by steveneddy on 2010-04-11
Are you running Ubuntu in Wubi?

If you are running Ubuntu in Wubi, get rid of the Wubi install and run Ubuntu in a VM like virtualbox.

If this a full install on the hard drive or a separate partition then:

Have you performed this action in terminal?

```
sudo apt-get update
```

then 

```
sudo apt-get upgrade
```

---

### Post by pcdave98 on 2010-04-11
> **steveneddy said:**
> 
Have you performed this action in terminal?

```
sudo apt-get update
```then 

```
sudo apt-get upgrade
```



I have now. Bang goes CD number 6.

:P

> **steveneddy said:**
> 

Are you running Ubuntu in Wubi?




I'm sort of new to Linux so I'm not really sure about this. I have Ubuntu 9.10 installed, in its own partition, next to W7. So, I don't think I'm using Wubi - whatever Wubi is.

---

### Post by pcdave98 on 2010-04-11
It appears that I can burn DVDs but not CDs.

When burning a DVD I first get this:

[http://ubuntuforums.org/attachment.php?attachmentid=152946&stc=1&d=1271003372](http://ubuntuforums.org/attachment.php?attachmentid=152946&stc=1&d=1271003372)

and then this:

[http://ubuntuforums.org/attachment.php?attachmentid=152947&stc=1&d=1271003372](http://ubuntuforums.org/attachment.php?attachmentid=152947&stc=1&d=1271003372)

The DVD is fine - I can see the data on there.

---

### Post by steveneddy on 2010-04-11
So there is not any data on the CD after burning it?

But there is data on the DVD?

Is this correct?

EDIT:

And were you able to install k3b?

---

### Post by pcdave98 on 2010-04-16
> **steveneddy said:**
> 
So there is not any data on the CD after burning it?


I can see the music files but get an error when I try to play them.

> **steveneddy said:**
> 
But there is data on the DVD?


Yep - DVDs are fine, even with those error messages.

> **steveneddy said:**
> 
And were you able to install k3b?


Tried and failed.

Sorry it took me 4 days to reply - I didn't check for replies as I work away from home, during the week, so can't fiddle with the desktop CD burner.

I'm thinking of giving up on this one. I can burn the occasional music CD, for the car, when I boot into Windows to update my Sat Nav and iPhone.

Thanks anyways, steveneddy.

:P

---

### Post by pcdave98 on 2010-05-01
Hurrah for 10.04!


All working now.

:P

---

