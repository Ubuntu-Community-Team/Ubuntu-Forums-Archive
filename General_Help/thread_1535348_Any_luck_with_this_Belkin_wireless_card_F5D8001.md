---
title: "Any luck with this Belkin wireless card F5D8001?"
date: 2010-07-20
forum: General Help
---

### Post by Abu Azzubair on 2010-07-20
Someone gave me this link to solve this wireless card's problem:

[http://ubuntuforums.org/showpost.php?p=6503726&postcount=4](http://ubuntuforums.org/showpost.php?p=6503726&postcount=4)

Thanks a million to the person [ubu_dynamite]("http://ubuntuforums.org/member.php?u=49544"). But the problem is that this person thinks that everyone is as smart as himself/herself. I'm a newbie Lol

Basically I got stuck in this part:

> STEP 3: COMPILE PROGRAM

Now we'll complile the Ndiswrapper program. In a terminal, go to the  directory where you extracted ndiswrapper and execute the following:

     Code:
     cd YOUR-NDISWRAPPER-DIRECTORY
sudo make uninstall 
IMPORTANT: Do the above command multiple times. You can stop when  you get the message that says something about no files or directories  found. This usually means running the command 2 or 3 times, but not more  than about a dozen.

     Code:
     make
sudo make install 
Can anyone please tell me what this person means by
> cd YOUR-NDISWRAPPER-DIRECTORY
sudo make uninstallAaaaany help is very appreciated, I done all I can and I'm just stuck at this last point

Also

Could someone please tell what I should do in this quotation for another one of the codes he/she mentioned - it's similar to the one I'm currently stuck at:

> STEP 4: INSTALL DRIVERS

If that worked, then you now have Ndiswrapper installed. Now we need to  install the drivers.

Now change directories to the DRIVER directory and install the driver.

     Code:
     cd YOUR-DRIVER-DIRECTORY 


Thanks in advance O:)

---

