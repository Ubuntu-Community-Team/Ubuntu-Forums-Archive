---
title: "Ubuntu 10.10 stuck at &quot;Ready when you are...&quot;"
date: 2010-10-11
forum: General Help
---

### Post by jcd29 on 2010-10-11
I'm doing a clean install in a new computer of Ubuntu 10.10, and it's stuck at abou 80-90% with a "ready when you are..." message. It's right after the keyboard layout.

I found somewhere that it might be the username, which has to be lowercase, but I didn't even get to the username screen.

It's a 500GB with its two ntfs partitions, and I'm installing the ext4 primary partition, and the swap primary partition.

---

### Post by darkstaar on 2010-10-11
Did you reboot and start the installation over or does it do the same thing with every attempt?

---

### Post by jcd29 on 2010-10-11
Trying again right now. Chose swap as logical partition since I found out a drive can't have four primaries.

---

### Post by jcd29 on 2010-10-12
Solved!

---

### Post by go-rebels on 2010-10-12
I'm having the same problem now.  Please explain fix to newbie in more detail.  I have configured the disk to one 160gb partition.

Thx

---

### Post by rio2000 on 2010-10-12
> I'm having the same problem now. Please explain fix to newbie in more detail. I have configured the disk to one 160gb partition.

me too, i am using virtual box and instalation stuck at about 80% progress

---

### Post by yangexp on 2010-10-12
> **rio2000 said:**
> me too, i am using virtual box and instalation stuck at about 80% progress
me tooooooooo! please find out detail problem ???? how to fix ?

---

### Post by go-rebels on 2010-10-12
> **darkstaar said:**
> Did you reboot and start the installation over or does it do the same thing with every attempt?

My condition is now repetitive.

Still need help...

Thx

---

### Post by JohnnyMalakian on 2010-10-12
I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html]("http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html")

---

### Post by jcd29 on 2010-10-12
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html]("http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html")

I used lowercase letters, yeah. But I think my problem was just the four primary partitions. I also moved the mouse every two minutes just in case it thought I was gone or something.

---

### Post by go-rebels on 2010-10-13
Fixed!  No caps in username.

---

### Post by phill3006 on 2010-10-26
+1.
Had the same problem.  No caps in username fixed it as well.

---

### Post by txspaderz on 2010-10-28
Same here, no caps in username worked!

---

### Post by 71GA on 2010-11-03
Did not solve the problem here. I never get to the "specify username" part.... I am stuck before this happens. 1 step earlier i choose "erase and clean install".

Stupid 10.10 ... should be perfect as they told us... BULSHIT

---

### Post by Pabx on 2010-11-07
In  my case i had to put my keyboard layout to "USA" to make it work . in other keyboard layouts it wouldn't work. 


With the ubuntu alternate disk I did a clean install without problems and with latam layout.

---

### Post by JPWhite on 2011-01-02
I can confirm that a lower-case user-name resolved this issue for me.

For one minute I thought I had messed up a perfectly good computer :-)

JP

---

### Post by XnP on 2011-01-09
I needed both solutions: Default keyboard and lower case username.
Working with MS OS's as well, this is the first time I get this kind of issue installing an OS.
MS 1, LX 1. (LX 1 'cause it is free!).

Xn

---

### Post by Hranj on 2011-02-03
If it wasn't for this stupid bug I'd still have a laptop with an intact screen. After messing around and messing around trying to get this to work I had it on the coffee table and dropped a remote on it.

I know its really not Ubuntu's fault, I was careless. But if it had worked the first time the computer would have stayed up in my room instead of being brought down to the coffee table where it met its demise.

---

### Post by pressko on 2011-02-04
Hi guys,

I'm doing a clean installation of ubuntu 10.10 on my acer 6920g.
I have the problem with inactive "forward" button on the username's page. I'm using ONLY small latters for username , but its still inactive.
Down there the orange bar is frozen to about 80% and the ... "Ready when you are ... " .Can u explain me  how to configure partiotion and etc. 

10x :))

---

### Post by Zheldon on 2011-02-13
Lower case user name worked for me as well!

---

### Post by Stefka29 on 2011-02-14
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html](http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html)


yes that was the problem for me.
Thanks

---

### Post by Egilbe on 2011-02-28
Beating my head against this for 36 hours now. That is just silly! No caps in a user name

---

### Post by microdoc on 2011-03-02
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.
 
See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)
 
Hope I helped. (it would be my first contribution :P)
Cheers!
 
Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html](http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html)
 
Johnny:
 
Thanks from one Hye to another. That did it for me! I hope I can repay your help some time.
 
Jim

---

### Post by seanksg on 2011-03-07
Also noted with 10.10:

Spaces are not permitted in the UserName field, even though the installer puts a check mark next to a name with both caps and spaces.

-Sean

---

### Post by Bigfootedadam on 2011-03-15
Thanks for the Tip on Caps had no idea probably should have come here sooner say prior to the 3 hours i spent stewing on this

---

### Post by i20234 on 2011-03-24
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html](http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html)

THANK YOUUUU Yeah I capitalized my first name.... it fixed it. Thanks!

---

### Post by i20234 on 2011-03-24
> **microdoc said:**
> Johnny:
 
Thanks from one Hye to another. That did it for me! I hope I can repay your help some time.
 
Jim

lold didn't know so many armenians used linux. I live in glendale

---

### Post by brianp48093 on 2011-03-29
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html]("http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html")

Worked like a charm!! THANK YOU!!!!

---

### Post by JBetts on 2011-04-15
This is the dumbest bug ever. This is why people are driven to use Windows.

---

### Post by radarFailure on 2011-04-18
> **JohnnyMalakian said:**
> I'm gonna go out on a limb here: I just had the same issue and, after some searching around Google about this, I found the fix to it. Like the site I found described, it's simple and stupid.

See if NOT using capital letters in the 'username' field solves the problem.
It did for me. (pretty lame bug, right? -.-)

Hope I helped. (it would be my first contribution :P)
Cheers!

Thanks to this site: [http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html](http://www.crazyengineers.com/forum/computer-science-engineering/37240-ubuntu-10-10-installer-stuck-solution.html)


Exactly. Had the same problem here
username should not have any capital letters. 

Solved Thanks :)

---

### Post by Tweedle Dee on 2011-05-11
> **seanksg said:**
> Also noted with 10.10:

Spaces are not permitted in the UserName field, even though the installer puts a check mark next to a name with both caps and spaces.

-Sean

thanks Sean - that was my problem - username with caps and space. 

this is what makes ubuntu great - the people.


thx again

tweedle

---

### Post by Calinda on 2011-12-13
For anyone else who can't get past the user detail window... 

Make sure that you have set a password, even though you chose not to use a password for login... (It's the root pw.)

---

