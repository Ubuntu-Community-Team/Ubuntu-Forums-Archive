---
title: "Update Package Manager - have 2 running"
date: 2011-05-26
forum: General Help
---

### Post by dee119 on 2011-05-26
:):):)

Hi There - as a newbie I wonder if anyone could help, or point me in the
right direction with this please.

Trying to update my system with the Update Manager, I keep getting
this message....

#Failed to lock the package manager 

It then says that I have 2 package managers running at the same time.

I have no idea how to revert back to the default, so any suggestions would
be most appreciated.

Thanks for looking  :)

---

### Post by iclestu on 2011-05-26
did you try:

```
sudo dpkg --configure -a
```

Thats kinda my catch all for when package manager crashes or anything.... Im sure someone with more experience will be able to give you help if it doesnt work

---

### Post by dcstar on 2011-05-26
> **dee119 said:**
> :):):)

Hi There - as a newbie I wonder if anyone could help, or point me in the
right direction with this please.

Trying to update my system with the Update Manager, I keep getting
this message....

#Failed to lock the package manager 

It then says that I have 2 package managers running at the same time.
..........

The Ubuntu system automatically updates packages in the background shortly after boot-up and also on set schedules.

You may be trying to do a manual update while one of these is running, wait 10 minutes and try again.

---

### Post by dee119 on 2011-05-26
:):):)


Thanks Guys for your input -

Have tried #sudo --configure - a   =  still have the same problem.

Here's what I get when trying to update....

#Check if you are currently running another software management
tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

Can see from other posts that there is some sort of problem with update manager,
just would like to get mine back as before.

Perhaps the above might shed more light on the subject. 

Thanks again for your thoughts  :)

---

### Post by iclestu on 2011-05-26
> **dee119 said:**
> :):):)


Thanks Guys for your input -

Have tried #**sudo --configure - a **  =  still have the same problem.

Here's what I get when trying to update....

#Check if you are currently running another software management
tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

Can see from other posts that there is some sort of problem with update manager,
just would like to get mine back as before.

Perhaps the above might shed more light on the subject. 

Thanks again for your thoughts  :)

Just checking that you did "sudo [SIZE=3]**dpkg**[/SIZE] --configure -a", yeah?

If so, then I am out of ideas :) someone waaaaay better will be along shortly no doubt.... Maybe it will help them if you post the output from that command?

---

### Post by dee119 on 2011-05-26
:):):)

Thanks Iclestu for your input -

Still no joy with this package manager problem,  seems as
if there is a lot having the same issue in Ubuntu 11.4.

I am running 10.10 and tried your code, all I got from that
was just the cursor, nothing else.  So don't know if it did 
anything,  so will try logging in/out to see if that does anything.

But my thanks again for taking the time to help.  Hopefully someone
will stop by that may have the solution.

Cheers+Beers  :)

---

### Post by dee119 on 2011-05-26
Have managed to get into Update Manager but get
stopped with the following message ......

#E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
#E: Unable to lock the list directory

Anyone have an idea how to unlock/lock .....

Looking at the message it seems as if the Repository/Resource is closed.  Think that
cannot be right, so again would appreciate your input please.

Thanks again for looking  :)

---

### Post by plucky on 2011-05-26
You have some process that is keeping the lock file to itself.

Try re-booting (to stop any dpkg processes) and then after the system has booted, delete the lock file with the command from a terminal ```
sudo rm /var/lib/apt/lists/lock
```

It will be re-created the next time you run any package managers.

Good Luck

---

### Post by dee119 on 2011-05-26
:):):)

Thanks Plucky for your help -  have managed to get the update package manager
to sort of work - but it keeps throwing me out with....

#Insert the CD Nutty/W 11.04 -  then it says check Internet connection, after which
I get the message that it cannot download the Repository Directories.

Hope that makes sense.  

At least we are moving along the right lines, so thanks for your help.  :)

---

### Post by northwestern on 2011-05-26
I had the same problems, type **[COLOR=Black]northwestern[/COLOR]** in the search box and you may find the answer to your problem.

---

### Post by dee119 on 2011-05-26
:):):)

Thanks for your help Northwestern - tried your code, which opened the
package manage.  But returned with the following.....

#Please insert the disc labelled:
Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)
in drive /cdrom/

I think for some reason (probably me trying command line code that was
posted earlier)  the system thinks I am running 11.04,  when I am in fact
running 10.10.

Not sure how to rectify this, so any help would be much appreciated on
how to go about it.  

Thanks again for looking.   :)

---

### Post by dee119 on 2011-05-26
:):)

Problem solved - :)

After opening the Synpatic manager,  I found that I had
checked the box for the 11.04 repository for download.

Unchecked that box, and all seems to be working OK now.

My thanks to all those that took the time to help me over
this hic-cup.

As a newbie to Ubuntu for only a few weeks,  I still have not 
changed my mind on it being the best distro I have used.

So thanks again,  it really has been appreciated.

Good Luck.  :):)

---

