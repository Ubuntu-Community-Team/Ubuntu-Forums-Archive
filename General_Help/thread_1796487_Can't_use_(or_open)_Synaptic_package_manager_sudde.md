---
title: "Can't use (or open) Synaptic package manager suddenly. Help please?"
date: 2011-07-03
forum: General Help
---

### Post by Rasa1111 on 2011-07-03
Hey humans,

 For the past few days (week maybe) I've been getting the
 ***" cannot upgrade- Would you like to do a partial upgrade?"*** message
Whenever I run update manager. 
So I say no, and just do whatever updates it will allow, 
But it always leaves one or two things unchecked/un-updated/and un-able to even check them.

Today, 
I attempt to run synaptic package manager ,
and I get this~ [ATTACH]196646[/ATTACH]

I don't even know what that means, 
and I dont know how to fix whatever it is so that I can get into synaptic. 

Also, when I run something like. "sudo apt-get update && sudo apt-get upgrade"
It goes through the packages, Does its thing.. But ends with "Some packages have failed.."

You'll also notice in the screenshot, Up to the left of my weather indicator in top panel, 
The little (X) icon. 
 This just appeared today.

Something is/has obviously gone awry, and I've no idea what. 
But I'm clearly still too ignorant to fix it myself. :(

Can anyone enlighten me, please? 

thanks in advance. 
and a gold:KS for whoever helps. lol
<3

---

### Post by wildmanne39 on 2011-07-03
> **Rasa1111 said:**
> Hey humans,

 For the past few days (week maybe) I've been getting the
 ***" cannot upgrade- Would you like to do a partial upgrade?"*** message
Whenever I run update manager. 
So I say no, and just do whatever updates it will allow, 
But it always leaves one or two things unchecked/un-updated/and un-able to even check them.

Today, 
I attempt to run synaptic package manager ,
and I get this~ [ATTACH]196646[/ATTACH]

I don't even know what that means, 
and I dont know how to fix whatever it is so that I can get into synaptic. 

Also, when I run something like. "sudo apt-get update && sudo apt-get upgrade"
It goes through the packages, Does its thing.. But ends with "Some packages have failed.."

You'll also notice in the screenshot, Up to the left of my weather indicator in top panel, 
The little (X) icon. 
 This just appeared today.

Something is/has obviously gone awry, and I've no idea what. 
But I'm clearly still too ignorant to fix it myself. :(

Can anyone enlighten me, please? 

thanks in advance. 
and a gold:KS for whoever helps. lol
<3Hi, run these two commands and it should fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Rasa1111 on 2011-07-03
> **wildmanne39 said:**
> Hi, run these two commands and it should fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```


Wowzers!
You're a lifesaver dude! 
Worked great! haha
many thanks! 

You rock, 
5 gold :KS:KS:KS:KS:KS's for you buddy! lol  
Thanks! <3

Wonder if that will fix everything else?....


hmm.........

---

### Post by wildmanne39 on 2011-07-03
Hi, thank you, and your welcome, I am glad it worked please mark thread solved. I do not know about the X on the panel. I would start a separate thread for that issue, that might have been there because the update manager would not have been working either.

---

### Post by Rasa1111 on 2011-07-03
> **wildmanne39 said:**
> Hi, thank you, and your welcome, I am glad it worked please mark thread solved. I do not know about the X on the panel. I would start a separate thread for that issue, that might have been there because the update manager would not have been working either.

 :)
marked as Solved. 

Yeah the X in the panel just means there's a prob. somewhere with a repo. or something.

 It has vanished for now. :P lol
But update manager is still funky..

What's left now, Is this.. [ATTACH]196651[/ATTACH]
Any ideas? 

Can i just remove those repos. and be done with it? lol
Also, 
I don't know what the "Read /write NTFS driver for FUSE" is for..
So not sure if i should get rid of it or not, I dont remember installing it. 

Thanks again. <3

---

### Post by Rasa1111 on 2011-07-04
Think Im good now..
Ive actually just unchecked the repo that was giving me the problems. 
Didnt remove it, Just unchecked it from the software sources list.

Not an actual "fix" i know, But dont know what else to do. lol

Very annoying when people can't keep their own PPA's going properly.
Why even bother?  :rolleyes:

---

### Post by wildmanne39 on 2011-07-04
> **Rasa1111 said:**
> Think Im good now..
Ive actually just unchecked the repo that was giving me the problems. 
Didnt remove it, Just unchecked it from the software sources list.

Not an actual "fix" i know, But dont know what else to do. lol

Very annoying when people can't keep their own PPA's going properly.
Why even bother?  :rolleyes:
Hi, that ntfs fuse that is the package that lets you see your window files in ubnutu, and there is nothing wrong with unchecking it, also I have learn that a partial upgrade is almost always a bad idea, it usually breaks synaptic.

---

### Post by Rasa1111 on 2011-07-04
Alright cool. . :)
Yeah i learned the badness of the "partial upgrade" the hard way, a while back.
Ill never do that again! :lol:

Thanks man(ne)!!

---

