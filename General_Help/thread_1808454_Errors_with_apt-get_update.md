---
title: "Errors with apt-get update"
date: 2011-07-20
forum: General Help
---

### Post by Juliolp on 2011-07-20
Hi Ubuntu geeks! :P

I'm new to Ubuntu, changed from Windows7 and i wonder why i never changed before. I love it. :)

When I installed Ubuntu 11.04 i went to some blogs to do the classics "10 things to do after installing Ubuntu 11.04". It seems all is fine. But when i do this command in the terminal, 

> sudo apt-get updateI get this errors ("imposible obtener"="can't get", i think this is the translation) in the terminal:

> W: Imposible obtener [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/tucan/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/tucan/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/tucan/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/tucan/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
What's wrong and how can i fix this? Thank you very much! :D

---

### Post by kroq-gar78 on 2011-07-20
First, glad you're enjoying ubuntu! That's the exact same thing I was thinking when I moved :D

Now, to your error: Are you trying to install software from a PPA? You probably typed the addresses in wrong and that's why you are getting 404 Not Found errors. 404 errors on the internet mean that the file/address you were looking for either don't exist or were moved. In this case, the updates for Java are old and the PPA isn't being used AFAIK (the packages are WAAAY old) and it doesn't even support 11.04 (natty narwhal). The repositories (the official ubuntu ones) support Java6 update26 right now. Just remove the Sun Java PPA and that error is gone.

Now, the toucan error. You typed in the address wrong. it's supposed to be "ppa:toucan/stable", not "ppa:toucan/ppa".

To fix:
run "sudo add-apt-repository ppa:toucan/stable" from a Terminal (that's the name of the application)
then, open Software Center and, from the "Edit" Menu (top right), select "Software sources". Then, go to "Other Software" and uncheck the four sources from there to fix the errors. Then, exit Software Sources, and just run "sudo apt-get upgrade" from a terminal, and voila, you're done.

Just ask if you need any help!

Sincerely,
kroq-gar78

---

### Post by Wayne_V on 2011-07-20
did you add those launchpad entries to /etc/apt/sources.list or /etc/apt/sources.list.d?

All it is saying is that those repos don't exist.  The other repos should be fine and you should be able to 'apt-get upgrade' without problems.

---

### Post by Juliolp on 2011-07-20
> **kroq-gar78 said:**
> 
Now, the toucan error. You typed in the address wrong. it's supposed to be "ppa:toucan/stable", not "ppa:toucan/ppa".

To fix:
run "sudo add-apt-repository ppa:toucan/stable" from a Terminal (that's the name of the application)
then, open Software Center and, from the "Edit" Menu (top right), select "Software sources". Then, go to "Other Software" and uncheck the four sources from there to fix the errors. Then, exit Software Sources, and just run "sudo apt-get upgrade" from a terminal, and voila, you're done.

Just ask if you need any help!

Sincerely,
kroq-gar78

Hi! Thanks both for the answer. Kroq-gar78, i did your steps but first command:

> sudo add-apt-repository ppa:toucan/stable
[sudo] password for julio: 
Error reading [https://launchpad.net/api/1.0/~toucan/+archive/stable:](https://launchpad.net/api/1.0/~toucan/+archive/stable:) HTTP Error 404: Not Found


But then i went to step 2: i unchecked those 4 PPA's. I wrote:

> sudo apt-get update 			 		

but then again:

> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/toucan/stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/toucan/stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/toucan/stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/toucan/stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found


Maybe i touched something that i shouldn't? :D Maybe i must uninstall something? Sometimes i installed from Terminal and sometimes from Ubuntu Software Center and maybe i add some wrong PPA's, now i'm going to restart my PC to look if something changes, but i didn't type by myself those urls -and i'm still learning what is a PPA, LOL-: all I do is copy&paste in the Terminal the tips from some Ubuntu blogs. :D 

But my system still works so... Ubuntu is still cool. Maybe you can suggest another way? I'm sure it's a newbie mistake. :D

Sincerely (thank you very very much to both), Julio :D

---

### Post by oldos2er on 2011-07-20
It's 'tucan', not 'toucan'.

---

### Post by kroq-gar78 on 2011-07-20
> **oldos2er said:**
> It's 'tucan', not 'toucan'.
Yes, that must be the problem. Oops :(

Juliolp, you fixed the 1st problem you had, but now you have to change "toucan" to "tucan". 

Remove the source for "toucan" (yes, the incorrectly spelled one) and then go to terminal and type "sudo add-apt-repository ppa:tucan/stable"

Post back if you have any questions! ;)

---

### Post by Juliolp on 2011-07-20
Guys! I got to say you are all the fu*ing masters of Ubuntu LOL. Sure it was easy for all of you but for me is like that guy in the moon, "a big step for me, a small step for Ubuntu", LOL, but i'm very happy.

kroq-gar78, thanks for all, I unchecked all toucan/tucan in sources and... well, 0 errors. 

I will learn here a lot (and of course searching and testing). :D

Oh, guys, i go to say this: Ubuntu is coooooooooooooooooooool :D

Thanks very much to everybody and** very specials for kroq-gar78**, sincerely!! :D

---

### Post by kroq-gar78 on 2011-07-20
Lol np.
 
 Wait! you still need to install tucan!
 ```
sudo apt-get install tucan
``` Then you're good B)
 
 Sincerely,
 kroq-gar78

Sorry, I couldn't get this to post for like an hour :|

---

